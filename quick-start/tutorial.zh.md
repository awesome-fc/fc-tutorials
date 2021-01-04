# 使用Funcraft创建函数 

本文以编写Hello World函数为例，演示了在函数计算中如何使用Funcraft创建函数。

<tutorial-nav></tutorial-nav>

## 前提条件


* [开通函数计算服务](https://www.alibabacloud.com/help/doc-detail/51783.htm?#section-938-43e-c63)

* [安装命令行工具Funcraft](https://github.com/alibaba/funcraft/blob/master/docs/usage/installation-zh.md)

---
**注意**

Cloud Shell已经预先安装了Funcraft，除非你需要使用最新版本的Cloud Shell，否则你不必再次安装Funcraft。

---


背景信息
----

Funcraft是函数计算提供的应用部署工具，可以帮助您便捷地管理函数计算、API网关、日志服务等资源，快速部署应用。Funcraft的更多信息，请参见[功能概览](https://www.alibabacloud.com/help/doc-detail/146701.htm)。


## 步骤一：配置Funcraft 

---
**注意**

使用Cloud Shell需要登录控制台，登录后Funcraft会以当前登录用户的身份操作云服务。除非你需要使用不同于当前登录用户的账号操作云服务，你不必配置Funcraft。

---

1. 执行以下命令初始化Funcraft工具，配置账号信息。
    ```bash
    fun config
    ```

2. 根据提示依次配置AccountID（主账号 ID）、AccessKey ID、AccessKey Secret、Default Region Name。

   如果您的账号是子账号，AccountID需要配置为主账号的AccountID，AccessKey ID、AccessKey Secret为子账号的密钥。
   **说明** 您可以在[账号管理](https://account.console.aliyun.com/)中获取账号的AccountID，[用户信息管理](https://usercenter.console.aliyun.com/)中获取AccessKey ID和AccessKey Secret。
   完成配置后，Funcraft会将配置保存到用户目录下的 *.fcli/config.yaml* 文件中。

   配置Funcraft的更多操作，请参见[配置Funcraft](https://www.alibabacloud.com/help/doc-detail/146702.htm?#concept-2260072)。


## 步骤二：创建初始化模板 

1. 执行以下命令初始化项目模板。
    ```bash
    fun init -n demo
    ```


2. 根据提示选择一个项目模板。

   项目模板类型如下：

   * 以`event-`为前缀的模板是普通的事件函数。
   
   * 以`http-trigger`为前缀的模板会默认为您创建的HTTP触发器。HTTP触发器以Request、Response为入参，帮助您快速搭建Web应用。
   
   本示例中，选择`event-nodejs10`的模板。

   Funcraft在执行命令的目录下，创建了一个demo的目录，并添加了两个文件，分别是 *index.js* 和 *template.yml* 。

   * <tutorial-editor-open-file filePath="fc-tutorials/demo/index.js"> index.js </tutorial-editor-open-file> 包含了函数的示例代码。
   
   * <tutorial-editor-open-file filePath="fc-tutorials/demo/template.yml"> template.yml </tutorial-editor-open-file> 指定了函数资源的相关信息。
     * 本示例为您创建了一个名为`demo`的服务与一个名为`demo`的函数。
     
     * *template.yml* 文件支持的配置项，请参见[Serverless Application Model](https://github.com/alibaba/funcraft/blob/master/docs/specs/2018-04-03-zh-cn.md)。



# 步骤三：部署到云端 

1. 执行以下命令将函数部署到云端。
    ```bash
    cd demo
    fun deploy
    ```
   

2. 部署过程中，输入`Y`确认需要创建的资源。

   创建完成后，提示`service demo deploy success`代表您的资源部署成功。
   


## 步骤四：调用函数

1. 执行下面的命令来调用函数，你会看到函数返回 `hello world`。

    ```bash
    fun invoke demo
    ```

## 步骤五：更新函数

1. 打开 <tutorial-editor-open-file filePath="fc-tutorials/demo/index.js"> index.js </tutorial-editor-open-file> 文件，将 `hello world` 改为 `hello world from function compute`.

2. 再次执行下面的命令来部署函数：
    ```bash
    fun deploy
    ```

3. 执行下面的命令来调用函数，你会看到函数返回 `hello world from function compute`:

    ```bash
    fun invoke demo
    ```




