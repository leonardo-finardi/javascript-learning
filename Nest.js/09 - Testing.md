# Testing in Nest.js

Testing is a critical aspect of software development to ensure that your application behaves as expected and remains stable. Nest.js provides tools and techniques for writing unit tests, integration tests, and end-to-end tests.

## Setting Up Testing

Nest.js comes with built-in testing tools that use the Jest testing framework. To get started, you can create a test suite for a module using the following command

```javascript
nest generate test module-name

```

This will create a test suite for the specified module in the test directory of your project.

## Writing Unit Tests

Unit tests focus on testing individual components or functions in isolation. You can use mocks and stubs to isolate the component being tested from its dependencies.

```javascript
// app.controller.spec.ts
import { Test, TestingModule } from '@nestjs/testing';
import { AppController } from './app.controller';
import { AppService } from './app.service';

describe('AppController', () => {
  let appController: AppController;

  beforeEach(async () => {
    const app: TestingModule = await Test.createTestingModule({
      controllers: [AppController],
      providers: [AppService],
    }).compile();

    appController = app.get<AppController>(AppController);
  });

  describe('root', () => {
    it('should return "Hello, Nest.js!"', () => {
      expect(appController.getHello()).toBe('Hello, Nest.js!');
    });
  });
});

```

## Writing Integration Tests

Integration tests focus on testing the interactions between different components, such as controllers and services.

```javascript
// cats.controller.spec.ts
import { Test, TestingModule } from '@nestjs/testing';
import { CatsController } from './cats.controller';
import { CatsService } from './cats.service';

describe('CatsController', () => {
  let catsController: CatsController;

  beforeEach(async () => {
    const app: TestingModule = await Test.createTestingModule({
      controllers: [CatsController],
      providers: [CatsService],
    }).compile();

    catsController = app.get<CatsController>(CatsController);
  });

  describe('findAll', () => {
    it('should return an array of cats', () => {
      expect(catsController.findAll()).toHaveLength(2);
    });
  });
});

```

## Running Tests

You can run tests using the following command:

```bash
npm run test

```

## Testing Endpoints with Supertest

To test your API endpoints, you can use the Supertest library, which provides a fluent API for making HTTP requests and assertions.

```javascript
// app.e2e-spec.ts
import { Test, TestingModule } from '@nestjs/testing';
import { AppModule } from '../src/app.module';
import { INestApplication } from '@nestjs/common';
import * as request from 'supertest';

describe('AppController (e2e)', () => {
  let app: INestApplication;

  beforeEach(async () => {
    const moduleFixture: TestingModule = await Test.createTestingModule({
      imports: [AppModule],
    }).compile();

    app = moduleFixture.createNestApplication();
    await app.init();
  });

  it('/GET should return "Hello, Nest.js!"', () => {
    return request(app.getHttpServer())
      .get('/')
      .expect(200)
      .expect('Hello, Nest.js!');
  });

  afterAll(async () => {
    await app.close();
  });
});

```

# Conclusion

Testing is crucial for ensuring the reliability and stability of your Nest.js applications. By following this crash course, you've learned how to write unit tests, integration tests, and end-to-end tests using the built-in testing tools and the Jest framework. This knowledge will help you maintain and improve the quality of your applications over time.