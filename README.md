> 本包纯属是测试自己发布`Nestjs`包的方式,没任何功能点,如果你还不会发布`Nestjs`包的可以学习下

# 使用方式
* 1、安装包

  ```shell
  npm install nest-log
  ```

* 2、在需要使用的模块中引入

  ```ts
  import { NestLogModule } from 'nest-log';

  @Module({
    imports: [
      // 使用自己刚刚发布的npm包
      NestLogModule.register('test---')
    ],
    providers: [UsersService],
    controllers: [UsersController]
  })
  export class UsersModule { }
  ```

* 3、在控制器中使用服务

  ```ts
  import { Controller, Get } from '@nestjs/common';
  import { NestLogService } from 'nest-log';

  @Controller('users')
  export class UsersController {
    constructor (
      private readonly nestLogService: NestLogService,
    ) { }

    @Get()
    hello(): string {
      this.nestLogService.log('获取用户信息')
      return 'hello';
    }
  }
  ```