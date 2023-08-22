# Controllers and Routing in Nest.js

Controllers in Nest.js are responsible for handling incoming HTTP requests and generating responses. They act as intermediaries between the client and the application's business logic. Routing is the process of defining how different endpoints (routes) are mapped to specific controller methods.

## 1 - Creating a Controller

You can create a controller by generating a new file and decorating it with the @Controller() decorator. This decorator specifies the base route for all the routes defined within the controller.

```javascript
// cats.controller.ts
import { Controller, Get } from '@nestjs/common';

@Controller('cats')
export class CatsController {
  @Get()
  findAll(): string {
    return 'This action returns all cats';
  }
}
```

## 2 - Defining Routes

Inside the controller class, you can define routes using decorators like @Get(), @Post(), @Put(), @Delete(), etc. These decorators define which HTTP methods the routes correspond to.

## 3 - Route Parameters

You can define route parameters using colon syntax (:paramName) in the route path and then access them within the method using the @Param() decorator.

```javascript
@Get(':id')
findOne(@Param('id') id: string): string {
  return `This action returns a cat with id ${id}`;
}
```

## 4 - Query Parameters

Query parameters can be extracted using the @Query() decorator. This is useful for accessing parameters provided in the URL's query string.

```javascript
@Get()
findByName(@Query('name') name: string): string {
  return `This action returns a cat named ${name}`;
}
```

## 5 - Request and Response Objects

You can access the full request and response objects using the @Req() and @Res() decorators, respectively. This allows you to interact with the HTTP request and response directly.

```javascript
@Get()
find(@Req() request: Request, @Res() response: Response): void {
  response.status(200).send('This action handles the request');
}
```

## 6 - Route Prefixing

You can prefix all routes within a controller using the @Controller() decorator's path option.

```javascript
@Controller('prefix')
export class CatsController {
  // Routes here will be prefixed with '/prefix'
}
```

## 7 - Global Prefixing

You can apply a global prefix to all routes in the entire application using the app.setGlobalPrefix() method in the main application file.

```javascript
const app = await NestFactory.create(AppModule);
app.setGlobalPrefix('api');
```

# Using Controllers

## 1 - Importing Controllers

To use a controller, you need to import it into a module's controllers array.

```javascript
@Module({
  controllers: [CatsController],
})
export class CatsModule {}
```

## 2 - Module Dependencies

Ensure that the module containing the controller has all required dependencies imported, including services or other providers.

# Running the Application

After creating a controller and setting up the necessary modules, you can run your Nest.js application using

```bash
npm run start
```

Access the defined routes at http://localhost:3000/yourRoutePath.

# Conclusion

Controllers and routing play a crucial role in handling incoming requests and defining the structure of your application's API. By following this crash course, you've learned how to create controllers, define routes, work with route parameters and query parameters, and more. This knowledge will help you build well-structured APIs and web applications using Nest.js.