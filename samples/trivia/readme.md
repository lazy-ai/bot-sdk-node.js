#问答技能模板简介
问答技能模板实现了古诗问答的功能。技能从古诗列表中选取5首歌诗，依次读出来并提供4个作者选项。用户需要回答选项中正确的作者的序号，回答正确以后技能会记录用户得分。技能交互过程如下：

* **用户**：打开古诗问答
* **技能**：[技能欢迎语]。第一题:离离原上草 一岁一枯荣。 1，李白 2，白居易 3，杜甫 4，柳宗元
* **用户**：第二个
* **技能**：回答正确，得一分。目前的分 1分。第二题。。。

技能从列表中选择古诗，可以杜绝题目重复和答案排列顺序重复的问题。开发者只需要更新题目列表和相应的技能配置信息，即可生成新的技能并在DuerOS DBP平台上发布。

列表中的一个问题和答案示例。请注意，正确的答案需要放置在可选答案中的`第一个`的位置。


```javascript
    {
      '人生自古谁无死，留取丹心照汗青': [
        '文天祥',
        '杜甫',
        '白居易',
        '李白',
      ],
    },
```

##使用模板开发技能
###新建技能

新建技能详情请参阅[自定义技能创建](https://dueros.baidu.com/didp/doc/dueros-bot-platform/dbp-custom/create-custom-skill_markdown)
###配置意图

意图配置详情请参阅 [意图、常用表达和槽位](https://dueros.baidu.com/didp/doc/dueros-bot-platform/dbp-nlu/intents_markdown)

问答技能模板需要创建两个意图，分别是回答问题意图和重新开始问答意图。
回答问题意图如下图所示：

![回答问题意图](http://dbp-resource.gz.bcebos.com/b53ad936-60d9-4f32-58a5-77159e1b0e9c/answerintent.png?authorization=bce-auth-v1%2Fa4d81bbd930c41e6857b989362415714%2F2018-09-28T08%3A25%3A20Z%2F-1%2F%2F7bd575bdd501694e2f2b2e4147429d8e6e6f9d39deb66895e0f4a2c549e45050)

重新开始问答意图如下图所示：

![重新开始问答意图](http://dbp-resource.gz.bcebos.com/b53ad936-60d9-4f32-58a5-77159e1b0e9c/newgame.png?authorization=bce-auth-v1%2Fa4d81bbd930c41e6857b989362415714%2F2018-09-28T08%3A26%3A29Z%2F-1%2F%2Fe2e1b2580ba9e340994790f053c0386b4a434c447f5a69c51415dee2533d287c)

###配置技能服务部署

问答技能模板使用CFC部署技能服务。使用CFC部署技能服务详情请参阅 [百度云CFC](https://dueros.baidu.com/didp/doc/dueros-bot-platform/dbp-deploy/cfc-deploy_markdown)

###修改CFC函数代码
问答技能模板使用questions.js配置题库。开发者需要下载技能CFC函数完整zip程序包到本地进行开发，开发完成后上传函数zip包进行发布。具体流程如下：

* 在CFC控制台通过模板创建函数, 选择node.js DuerOS Bot SDK模板
* 函数生成后，在函数控制台点击`点击下载完整 ZIP 程序包`链接下载程序包
* 在本地解压程序包
* 将问答技能模板中的questions.js文件拷贝到程序包文件夹中
* 使用问答技能模板中的index.js文件替换程序包文件夹中的index.js文件
* 将程序包文件夹中的所有文件重新打包成zip文件
* 在函数控制台上传zip程序包并保存

CFC操作说明请参阅[函数计算 CFC](https://cloud.baidu.com/doc/CFC/GettingStarted.html#.E4.BB.8E.E6.A8.A1.E6.9D.BF.E5.88.9B.E5.BB.BA.E5.87.BD.E6.95.B0)

###测试技能
至此，问答技能就开发完成了。开发者可以在技能开放平台的模拟测试页面对技能进行测试。

##开发者TODO
问答技能模板只是实现了问答技能的基础功能。开发者可以在模板的基础上对技能进行更多的完善。如：

* 增加更多意图，比如放弃当前问题意图，下一题意图，帮助意图等等
* 使用数据库或其他方式存储用户信息和得分，以便增加更多功能。如用户抽奖功能，或者分享功能。