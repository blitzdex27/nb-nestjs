# Nest JS

npm install -g nest

nest g module auth

docker compose

`docker-compose.yml`

```yml
version: "3.8"
services:
  dev-db:
    image: postgres:13
    ports:
      - 5434:5432
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: 123
      POSTGRES_DB: nest
    networks:
      - freecodecamp
networks:
  freecodecamp:
```

docker compose up dev-db -d

Install prisma

npm install -D prisma
npm install @prisma/client
npx prisma init

settings.json -> vscode

```json
"[prisma]": {
  "editor.defaultFormatter": "Prisma.prisma"
},
```

setup .env

npx prisma --help
npx prisma migrate dev
npx prisma studio

nest g module prisma

Test express

```js
import { Controller, Post, Req } from '@nestjs/common';
import { Request } from 'express';
import { AuthService } from './auth.service';

@Controller('auth')
export class AuthController {
  constructor(private authService: AuthService) {}

  @Post('signup')
  signup(@Req() req: Request) {
    return this.authService.signup();
  }

  @Post('signin')
  signin() {
    return this.authService.signin();
  }
}

```

npm install class-validator class-trasformer
npm install argon2

```
    "db:dev:rm": "docker compose rm dev-db -s -f -v",
    "db:dev:up": "docker compose up dev-db -d",
    "db:dev:restart": "npm run db:dev:rm && npm run db:dev:up",

```
