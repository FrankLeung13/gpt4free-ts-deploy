## 部署之前配置变量

1. 配置环境变量 [去配置](env/README.md)

- 把`env`文件夹下面的示例文件`*.env.example`环境变量文件统统去除`.example`后缀
- 你基本只需要修改 gpt4free.env，其他配置不知道具体含义，请勿修改


2. 配置oneapi渠道

原封不动按照，截图填入即可

![oneapi_cfg_help](https://github.com/xiangsx/gpt4free-ts-deploy/assets/29322721/da1676cb-458b-49a7-94ab-e964b8e96514)

3. 【可选】配置监控

配置http监控, 画框的地方，原样填入即可，不用修改
![image](https://github.com/xiangsx/gpt4free-ts-deploy/assets/29322721/82052e78-9bb8-498b-9460-93b8cb2cfcf0)
复制下面的值，填入参数
```json
{
    "site": "auto",
    "model": "gpt-3.5-turbo",
    "prompt": "say 1"
}
```

4. 【可选】配置clash
有些站点需要服务器配置代理，方便切换节点，例如`sincode` `perplexity`

> 注意把你的clash配置复制到 `clash/config.yaml`, 并且确认`external-controller: '0.0.0.0:9090'`, 该字段是监听的 `0.0.0.0`


## 部署步骤

1. 克隆项目
```shell
git clone git@github.com:xiangsx/gpt4free-ts-deploy.git
```

2. 配置`env/gpt4free.env`

根据环境变量文件中的注释填一下

3. 配置代理

- 国内机器: 配置`clash/config.yaml`
- 国外机器: 去除`env/proxy.env`中的`http_proxy`字段，即关闭代理

4. 启动
```shell
docker-compose up --build -d
```

## 相关链接

1. oneapi配置：http://127.0.0.1:29000
登录用户名密码 root 123456

2. clash配置界面：http://127.0.0.1:29002

3. 监控页面：http://127.0.0.1:29004

## Q&A

1. 出现`ERR PROXY COMMECTION FALED`
出现下图相关错误，检查你的代理，
**解决办法**: 如果你的机器是国外的，去除proxy.env的http_proxy字段或者在前面加个#注释掉; 如果你的机器是国内的，配置代理 `clash/config.yaml`或者使用你自己的代理端口，在proxy.env中修改
![image](https://github.com/xiangsx/gpt4free-ts-deploy/assets/29322721/59d5b369-b856-4d41-84af-bd27c2c45654)


