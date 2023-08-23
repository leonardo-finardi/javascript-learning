# Error Handling and Logging in Nest.js

Proper error handling and effective logging are essential for building robust and maintainable applications. Nest.js provides features to handle errors gracefully and manage logs efficiently.

## Global Exception Filters

Exception filters in Nest.js intercept exceptions and provide custom responses. You can create a global exception filter to handle errors globally for your application.

```javascript
// http-exception.filter.ts
import { ExceptionFilter, Catch, HttpException, ArgumentsHost } from '@nestjs/common';
import { Response } from 'express';

@Catch(HttpException)
export class HttpExceptionFilter implements ExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse<Response>();
    const status = exception.getStatus();

    response.status(status).json({
      statusCode: status,
      timestamp: new Date().toISOString(),
      path: request.url,
    });
  }
}

```

Register the global exception filter in your main.ts:

```javascript
const app = await NestFactory.create(AppModule);
app.useGlobalFilters(new HttpExceptionFilter());

```

## Custom Exception Handling

You can create custom exceptions to handle specific error cases in a more organized manner. Create a custom exception class and throw it where needed.


```javascript
// custom.exception.ts
import { HttpException, HttpStatus } from '@nestjs/common';

export class CustomException extends HttpException {
  constructor() {
    super('This is a custom exception', HttpStatus.BAD_REQUEST);
  }
}

```

## Logging with Custom Logger

Nest.js allows you to create custom loggers to manage your application's logs effectively. Create a custom logger that implements the LoggerService interface.

```javascript
// custom.logger.ts
import { LoggerService } from '@nestjs/common';

export class CustomLogger implements LoggerService {
  log(message: string) {
    // Implement your logging logic here
  }

  error(message: string, trace: string) {
    // Implement your error logging logic here
  }

  warn(message: string) {
    // Implement your warning logging logic here
  }

  debug(message: string) {
    // Implement your debug logging logic here
  }

  verbose(message: string) {
    // Implement your verbose logging logic here
  }
}

```

Register the custom logger in your main.ts:

```javascript
const app = await NestFactory.create(AppModule, { logger: new CustomLogger() });

```

# Conclusion

Proper error handling and effective logging are essential for building reliable and maintainable applications. By following this crash course, you've learned how to create global exception filters, handle custom exceptions, and implement custom loggers in Nest.js. These practices will help you manage errors and logs in a structured and controlled manner.