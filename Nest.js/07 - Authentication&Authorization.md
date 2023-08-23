# Authentication and Authorization in Nest.js

Authentication involves verifying the identity of a user, while authorization determines what actions a user is allowed to perform. Nest.js provides tools and techniques to implement both authentication and authorization in your applications.

## Authentication Strategies

Nest.js supports various authentication strategies, such as JWT (JSON Web Tokens), OAuth2, and more. Here, we'll focus on JWT authentication.

- Passport: Nest.js integrates well with the popular authentication library Passport.

## Creating an Auth Module

Start by creating an authentication module to handle user authentication.

```bash
nest generate module auth

```

## Authentication Service

Create an authentication service to handle user authentication logic.

```bash
nest generate service auth
```

## User Entity

Define a user entity that represents your user data.

```javascript
// user.entity.ts
import { Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  username: string;

  @Column()
  password: string;
}

```

## Authentication Controller

Create an authentication controller to handle login and token generation.

```javascript
// auth.controller.ts
import { Controller, Post, Body } from '@nestjs/common';
import { AuthService } from './auth.service';
import { User } from './user.entity';

@Controller('auth')
export class AuthController {
  constructor(private authService: AuthService) {}

  @Post('login')
  async login(@Body() user: User) {
    return this.authService.login(user);
  }
}

```

## Authentication Service Logic

In the authentication service, implement the logic to validate user credentials and generate JWT tokens.

```javascript
// auth.service.ts
import { Injectable } from '@nestjs/common';
import { JwtService } from '@nestjs/jwt';
import { User } from './user.entity';

@Injectable()
export class AuthService {
  constructor(private jwtService: JwtService) {}

  async validateUser(username: string, password: string): Promise<User | null> {
    // Implement user validation logic here
  }

  async login(user: User): Promise<{ access_token: string }> {
    const payload = { username: user.username, sub: user.id };
    return {
      access_token: this.jwtService.sign(payload),
    };
  }
}

```

## Guarding Routes

Guards are used for authorization. They determine whether a user is allowed to access a certain route or resource. Create a guard to protect routes that require authentication.

```javascript
// auth.guard.ts
import { Injectable, CanActivate, ExecutionContext } from '@nestjs/common';
import { Observable } from 'rxjs';

@Injectable()
export class AuthGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean | Promise<boolean> | Observable<boolean> {
    // Implement guard logic here
  }
}

```

Apply the guard to a route using the @UseGuards() decorator.

```javascript
// cats.controller.ts
import { Controller, Get, UseGuards } from '@nestjs/common';
import { CatsService } from './cats.service';
import { AuthGuard } from './auth.guard';

@Controller('cats')
export class CatsController {
  constructor(private catsService: CatsService) {}

  @Get()
  @UseGuards(AuthGuard)
  findAll() {
    return this.catsService.findAll();
  }
}

```

# Conclusion

Authentication and authorization are crucial for securing your applications and controlling access to resources. By following this crash course, you've learned how to implement user authentication using JWT, create guards for route protection, and apply these concepts to your Nest.js application.