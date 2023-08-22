# Middleware in Nest.js

Middleware functions in Nest.js are designed to intercept incoming requests and outgoing responses. They can perform actions such as authentication, logging, data transformation, error handling, and more. Middleware functions can be executed before a route handler is called or after it has completed its execution.

## 1 - Creating Middleware

Middleware is created by defining a class with a specific method name. The method's name corresponds to the lifecycle event you want to intercept (use for incoming requests, reply for outgoing responses). You can use the @Middleware() decorator to bind the middleware to the specific method.

```javascript
// logging.middleware.ts
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response } from 'express';

@Injectable()
export class LoggingMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: Function) {
    console.log(`Request...`);
    next();
  }
}
```

## 2 - Using Middleware

Middleware can be applied globally, at the module level, or at the route/controller level.

- Global Middleware: You can apply middleware to all routes globally in the main.ts file:

```javascript
const app = await NestFactory.create(AppModule);
app.use(new LoggingMiddleware());

```

- Module Middleware: Apply middleware to a specific module by using the @Module() decorator:

```javascript
@Module({
  imports: [],
  controllers: [],
  providers: [],
  exports: [],
  middlewares: [LoggingMiddleware], // Add middleware here
})
export class AppModule {}

```

- Controller Middleware: Apply middleware to a specific controller:

```javascript
@Controller('cats')
@UseMiddleware(LoggingMiddleware) // Apply middleware to the controller
export class CatsController {
  // ...
}

```

## 3 - Middleware Execution Order

Middleware functions are executed in the order they are registered. The next() function is used to pass control to the next middleware in the chain.

## 4 - Middleware Execution Order

You can create middleware specifically for error handling by using the @Catch() decorator. Error handling middleware can be applied globally or at the controller level. They intercept thrown exceptions and allow you to customize the error response.

```javascript
@Catch(HttpException)
export class CustomExceptionFilter implements ExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse<Response>();
    const request = ctx.getRequest<Request>();

    const status = exception.getStatus();
    response.status(status).json({
      statusCode: status,
      timestamp: new Date().toISOString(),
      path: request.url,
    });
  }
}

```

Apply the error handling middleware in the same way as regular middleware, either globally or at specific controllers.

## Using Middleware

# 1 - Importing and Using Middleware

Import and use middleware within the relevant modules or controllers where you want them to apply.

```javascript
import { Module, MiddlewareConsumer, NestModule } from '@nestjs/common';
import { LoggingMiddleware } from './logging.middleware';

@Module({
  // ...
})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggingMiddleware).forRoutes('*');
  }
}

```

In the example above, forRoutes('*') means the middleware applies to all routes. You can replace '*' with specific route paths as needed.

# Conclusion

Middleware in Nest.js allows you to intercept and modify incoming requests and outgoing responses. It's a powerful tool for tasks such as authentication, logging, error handling, and more. By following this crash course, you've gained a solid understanding of how to create, use, and apply middleware in Nest.js applications.