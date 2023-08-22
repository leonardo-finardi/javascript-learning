# Modules in Nest.js

Modules are the building blocks of a Nest.js application. They help organize your code into cohesive units and facilitate separation of concerns. Each module groups together related components like controllers, providers, and other modules. Here's how you can create a basic module:

## Create a Module

Modules are defined using the @Module() decorator. You can create a module by specifying its metadata, including its imports, controllers, providers, and exports.

```javascript
// cats.module.ts
import { Module } from '@nestjs/common';
import { CatsController } from './cats.controller';
import { CatsService } from './cats.service';

@Module({
  controllers: [CatsController],
  providers: [CatsService],
  exports: [CatsService], // Make CatsService available for other modules
})
export class CatsModule {}

```

## Importing Modules

Modules can import other modules to utilize their functionality. For example, if you have a DogsModule, you can import it into the CatsModule:

```javascript
// cats.module.ts
import { Module } from '@nestjs/common';
import { DogsModule } from '../dogs/dogs.module'; // Import DogsModule

@Module({
  imports: [DogsModule], // Import DogsModule here
  // ...
})
export class CatsModule {}

```

# Dependency Injection

Dependency Injection (DI) is a design pattern where the dependencies of a component (e.g., services, other components) are injected from the outside rather than being created within the component. This promotes modularity, testability, and flexibility.

## 1 - Providers

In Nest.js, providers are classes that define the business logic of your application. They can be injected into controllers, other providers, or even custom decorators. Providers are defined using the @Injectable() decorator:

```javascript
// cats.service.ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class CatsService {
  private cats = ['Garfield', 'Tom', 'Sylvester'];

  getCats(): string[] {
    return this.cats;
  }
}
```

## 2 - Injecting Dependencies

You can inject dependencies (providers) into other components (like controllers or other providers) using constructor injection. Nest.js will automatically handle the injection for you:

```javascript
// cats.controller.ts
import { Controller, Get } from '@nestjs/common';
import { CatsService } from './cats.service';

@Controller('cats')
export class CatsController {
  constructor(private readonly catsService: CatsService) {}

  @Get()
  getCats(): string[] {
    return this.catsService.getCats();
  }
}
```

## 3 - Module-Level Injection

In your module, you can specify which providers should be available for injection within that module:

```javascript
// cats.module.ts
import { Module } from '@nestjs/common';
import { CatsController } from './cats.controller';
import { CatsService } from './cats.service';

@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class CatsModule {}
```

# Conclusion

Understanding modules and dependency injection is essential to harness the full power of Nest.js. Modules organize your application into manageable units, and dependency injection promotes clean and maintainable code by managing component relationships. This crash course provides a foundation for building Nest.js applications with structured and well-organized code.
