# Configuration and Environment in Nest.js

Configuration management is crucial for separating application settings from your codebase. Nest.js provides a way to manage configurations and environment variables easily.

## Configuration Management

To manage configurations, Nest.js recommends using the @nestjs/config package. Start by installing it:

```bash
npm install @nestjs/config

```

## Configuration Module

Create a configuration module to load and parse configuration values from various sources like .env files, environment variables, and more.

```javascript
// config.module.ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [ConfigModule.forRoot()],
})
export class ConfigAppModule {}

```

## Accessing Configuration Values

To access configuration values, inject the ConfigService into your services, controllers, or other providers.

```javascript
// cats.service.ts
import { Injectable } from '@nestjs/common';
import { ConfigService } from '@nestjs/config';

@Injectable()
export class CatsService {
  constructor(private configService: ConfigService) {
    const databaseHost = this.configService.get<string>('DATABASE_HOST');
  }
}

```

## Environment Variables and .env Files

Store your application's environment-specific variables in .env files and load them using the ConfigModule.

```dotenv
# .env
DATABASE_HOST=localhost
DATABASE_PORT=5432

```

## Validation and Type Casting

You can use validation and type casting for configuration values to ensure they have the expected format and types.

```javascript
// config.module.ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [ConfigModule.forRoot({
    validationSchema: Joi.object({
      DATABASE_HOST: Joi.string().required(),
      DATABASE_PORT: Joi.number().default(5432),
    }),
  })],
})
export class ConfigAppModule {}

```

# Conclusion

Configuration and environment management are crucial for keeping your application's settings organized and separate from your codebase. By following this crash course, you've learned how to use the @nestjs/config package to load and access configuration values, validate them, and manage environment variables effectively in Nest.js applications.