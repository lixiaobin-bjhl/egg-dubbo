# 功能说明
egg的dubbo插件，dubbo客户端

# 使用示例

* 将代码拷贝到工程的lib/plugin目录下
* 插件配置代码

```javascript

// config/plugin.ts
import { EggPlugin } from 'egg'
import path = require('path');

const plugin: EggPlugin = {
    dubbo: {
        enable: true,
        path: path.resolve(__dirname, '../lib/plugin/dubbo/')
    }
}

export default plugin


``` 
* 调用

```javascript
    
import { Controller } from 'egg';

export default class HomeController extends Controller {
  public async index() {
     this.ctx.body = await this.app.dubboClinent.dubboAgent.AreaService.getAllCity()
  }
}
   
```

* typeScript 声明

```
import "egg";

declare module "egg" {
    interface Application {
        dubboClinent: {
          dubboAgent: {
            AreaService: {
              getAllCity(): Promise<Any>;
            }
          }
        }
    }
}
```






