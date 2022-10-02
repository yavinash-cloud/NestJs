# NestJs
The JavaScript Node.js Framework

NESTJS

First, let's explain what is NestJS?
Nest (NestJS) is a framework for building efficient, scalable Node.js server-side applications, built with and fully supports TypeScript.Nest JS was developed with a mission to build effective, scalable backend apps with the support of JavaScript/TypeScript.
Under the hood, Nest makes use of robust HTTP Server frameworks like Express (the default) and optionally can be configured to use Fastify as well!
With the help of the Nest CLI developers can quickly create modules, controllers, pipes, and middleware without pain and therefore it boosts productivity, and automates many of the routine tasks.
Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify) but also exposes their APIs directly to the developer. This allows developers the freedom to use the myriad of third-party modules which are available for the underlying platform.

Installation
$ npm install -g @nestjs/cli
$ nest new project-name

but why use instead use pure express?
the main reason no has a standard of projects in node.js, every time you enter in a new project which uses node.js each has a properly architecture, some use an only single file for API( ugh...), other use MVC, others use a component architecture or other architecture, but sometimes the developer is new and don`t have the real concept of what is controller, what is Model, and project continue growth and people will improve their skills, but no have time to refactor the previous code and that make your project really messy.

that is the main reason to use Nestjs, he has an architecture clearly enough and run only in this format( you still can code another module and import as well, but always try to continue in the same style).

use the component architecture and separate in:
⦁	Controllers
⦁	Modules
⦁	Providers ( services, repositories, factories, helpers, and so on)
⦁	DTOs
⦁	Entities
an example your src file must be in this architecture:
src
  components
     cats
       dto
⦁	         index.ts
⦁	         catsCreate.dto.ts
⦁	         catsUpdate.dto.ts
       cats.controller.ts
       cats.module.ts
       cats.repository.ts
       cats.service.ts
     dogs
       dto
⦁	         index.ts
⦁	         dogsCreate.dto.ts
⦁	         dogsUpdate.dto.ts
       dogs.controller.ts
       dogs.module.ts
       dogs.repository.ts
       dogs.service.ts
  entities
⦁	    index.ts
⦁	    cats.entity.ts
⦁	    dogs.entity.ts
  config
    index.ts
    postgres.config.ts
  app.module.ts
  main.ts

the main reason to use this architecture is that is easy to "break" the application into microservices
if you already know Angular will be really easy to code with nestjs, and for those coming from spring boot(java) it's easy to come a nodejs developer too.

Back-end fundamental areas:
⦁	Server architecture
⦁	Database administration
⦁	Data transportation
⦁	Security
⦁	Integrations and third-party libraries (tools) support.

All these areas are well covered and handled using Nest JS (directly from the official documentation following the industries best practices and technologies) .
Next, I will depend on the following criteria to measure the pros and cons:
Architecture / Performance / Documentation / Community / Learning Curve / Testing / Integrations

Architecture:
- Nest JS is a highly opinionated framework, the architecture paths are already built, and the developers follow the provided structure guidelines (The architecture is heavily inspired by Angular's solid structure).

- In my opinion this makes it easier for the team to understand each others code and find things quickly.

Performance:
- There are two important aspects of software performance: responsiveness and scalability,
 - Nest JS is perfect to handle these aspects.
- Nest JS offers compatibility with other libraries, such as Fastify or Express.js out of the box.

Documentation:
Their official documentation covers all the backend aspects I've mentioned earlier, using the latest trend technologies and best practices.

Community and Learning Curve:
In a nutshell: Nest JS is the Angular for the backend.

Testing:
You can use any testing framework that you like, as Nest JS doesn't force any specific tooling, but it provides integration with Jest and Supertest out-of-the-box.

Integrations, Libraries, Security and More:
⦁	All Node JS packages and integrations are available.
⦁	Many aspects are ready out-of-the-box, such as: Database (TypeORM), Data Validation, Caching, Task Scheduling, Logging, Cookies, File Upload, Server-Sent Events, Authentication, Authorization, Encryption, Hashing, Helmet, CORS, CSRF, Limiters, GraphQL, WebSockets, Microservices, Redis, MQTT, Kafka ...

Framework Structure and Core Concepts:
⦁	Controller: Route the request to a particular function.
⦁	Providers: Inject dependencies; this means objects can build various relationships with each other.
⦁	Services: Responsible for operating the database and running the business logic.
⦁	Repository: Handle DB data.
⦁	Guard: User authentication.
⦁	Pipe: Validate and transform data.
⦁	Filters: Handle errors
⦁	Interceptors: Extra logic for requests/responses
⦁	Module: The module class is the place to connect Services, Controllers

controllers
The Propose of the controller is to handle of requisitions ( of any protocol, HTTP, MQTT or some Message queue[ Kafka, rabbitMQ, Nats]) and pass to the service to handle the business logic.

creating with nest CLI
$ nest g controller cats

Providers
he is more generic, can be a repository, service, help or factory. The main idea of a provider is that it can inject dependencies; like a service or a database connection with specific tables.

creating a service using cli
$ npm g service cats

cats.service.ts
In the service you'll put the business logic of the application, here it's only a CRUD, so only have a call to the repository, but if you need to get another data and handle will be nice you put here, and use repository only for connections with the database.

cats.repository.ts
In the repository you will put all database logic, complex queries etc, because the query its self isn't the real business logic itself, it's kinda weird but with the time you will get more clarity.

DTO
Data Transfer Object (DTO) is the format of data you will accept in the route, sometimes you want to define a basic schema like age need be a number positive, o name be a string.

using the lib class-validator and use the pipe of nestjs (in the begin of the route or global), for more information about pipe see the documentation.

Entities
The entity is the place you will get the information of the database to your application, using typeorm in this case, is an easy way to make SQL queries, its kinda MongoDB commands for more please go to typeorm.

 Final Notes:
 
⦁	NestJS adopted both TypeScript and Angular features.
⦁	NestJS uses TypeORM which gives leverage to connect with SQL and NoSQL databases.
⦁	Since NestJs is an Abstraction over the NodeJS. So we can use NodeJS libraries
⦁	NestJS surrounds your route handler body with try catch blocks, and it binds error-handling middleware.


