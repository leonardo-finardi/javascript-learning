## Data Persistence and ORM in Nest.js

Nest.js provides support for integrating databases and performing data operations using Object-Relational Mapping (ORM) libraries. One of the most commonly used ORM libraries with Nest.js is TypeORM.

# Setting Up TypeORM

To get started with TypeORM, you need to install it along with a database driver (e.g., mysql, postgres, sqlite, etc.). You can also install the @nestjs/typeorm package to integrate TypeORM with your Nest.js application.

```bash
npm install typeorm @nestjs/typeorm mysql

```

# Creating Entities

Entities are TypeScript classes that represent your database tables. Each property of an entity class corresponds to a column in the associated table. Decorate entity properties using the @Column() decorator and the entity class itself with the @Entity() decorator.

```javascript
// cat.entity.ts
import { Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class Cat {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column()
  age: number;
}

```

# Creating Repositories

Repositories provide methods for interacting with entities and performing CRUD (Create, Read, Update, Delete) operations. You can create a repository by extending the Repository class from TypeORM.

```javascript
// cats.repository.ts
import { EntityRepository, Repository } from 'typeorm';
import { Cat } from './cat.entity';

@EntityRepository(Cat)
export class CatsRepository extends Repository<Cat> {}

```

# Using Repositories in Services

Services are used to encapsulate business logic. Inject the repository into your service and use its methods to perform data operations.

```javascript
// cats.service.ts
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Cat } from './cat.entity';
import { Repository } from 'typeorm';

@Injectable()
export class CatsService {
  constructor(
    @InjectRepository(Cat)
    private catsRepository: Repository<Cat>,
  ) {}

  async findAll(): Promise<Cat[]> {
    return this.catsRepository.find();
  }

  async create(cat: Cat): Promise<Cat> {
    return this.catsRepository.save(cat);
  }
}

```

# Using Services in Controllers

Inject your service into your controller and use it to handle HTTP requests.

```javascript
// cats.controller.ts
import { Controller, Get, Post, Body } from '@nestjs/common';
import { CatsService } from './cats.service';
import { Cat } from './cat.entity';

@Controller('cats')
export class CatsController {
  constructor(private catsService: CatsService) {}

  @Get()
  async findAll(): Promise<Cat[]> {
    return this.catsService.findAll();
  }

  @Post()
  async create(@Body() cat: Cat): Promise<Cat> {
    return this.catsService.create(cat);
  }
}

```

## Conclusion

Using TypeORM and data persistence in Nest.js makes it easier to work with databases and perform CRUD operations. By following this crash course, you've learned how to define entities, repositories, services, and controllers to create a functional ORM-based application in Nest.js.

