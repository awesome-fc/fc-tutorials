# Create a function by using Funcraft

This topic describes how to create a function in Function Compute by using Funcraft. In this topic, a Hello World function is created.

<tutorial-nav></tutorial-nav>

## Prerequisites

* [Activate the Function Compute service](https://www.alibabacloud.com/help/doc-detail/51783.htm#section-938-43e-c63)

* You have [installed the command-line tool Fun](https://github.com/alibaba/funcraft/blob/master/docs/usage/installation.md).

---
**NOTE**

Since Cloud Shell has pre-installed Funcraft, this step is not required.

---

Funcraft is an application deployment tool provided by Function Compute. It allows you to conveniently manage resources of Function Compute, API Gateway, and Log Service to quickly deploy applications.

## Step 1: Configure Funcraft 

---
**NOTE**

You do not need to configure Funcraft unless you want to use a different account other than the current logged-in accout.

---

1. Run the following command to initialize Funcraft and open the account information configuration page:
    ```bash
    fun config
    ```
   

2. Sequentially specify AccountID (the ID of the Alibaba Cloud account), AccessKey ID, AccessKey Secret, and Default Region Name for Funcraft as instructed.

   If you are using a Resource Access Management (RAM) user, set AccountID to the account ID of the corresponding Alibaba Cloud account and set AccessKey ID and AccessKey Secret to the AccessKey pair of the RAM user.
   **Note** You can obtain your Alibaba Cloud account ID from [Account Management](https://account.console.aliyun.com/) and AccessKey ID and AccessKey Secret from [User Management](https://usercenter.console.aliyun.com/).
   After the configuration is completed, Funcraft saves the configurations to the *.fcli/config.yaml* file in your directory.

   For more information about how to configure Funcraft, see [Configure Funcraft](https://www.alibabacloud.com/help/doc-detail/146702.htm?#concept-2260072).
   




## Step 2: Create an initialization template 

1. Run the following command to initialize the project template:
    ```bash
    fun init -n demo
    ```

2. Select a project template as instructed.

   The following project templates are available:

   * Templates prefixed with `event-` are common event functions.
   
   * Templates prefixed with `http-trigger` automatically create HTTP triggers. An HTTP trigger uses request and response as input parameters, helping you quickly create a web application.

   In this example, the `event-nodejs10` template is selected.

   Funcraft creates a demo folder in the directory where you run the command. The demo folder contains the `index.js` and `template.yml` files.

   * The <tutorial-editor-open-file filePath="fc-tutorials/demo/index.js"> index.js </tutorial-editor-open-file> file contains the sample code of the function. 
   
   * The <tutorial-editor-open-file filePath="fc-tutorials/demo/template.yml"> template.yml </tutorial-editor-open-file> file describes how Funcraft creates function resources.
     * In this example, the `demo` service and the `demo` function are created for you.
     
     * For more configuration items supported by the template.yml file, see [Serverless Application Model](https://github.com/alibaba/funcraft/blob/master/docs/specs/2018-04-03-zh-cn.md).


## Step 3: Deploy the function to the Function Compute service 

1. Run the following command to deploy the function to the Function Compute console:
    ```bash
    cd demo
    fun deploy
    ```
   

2. During deployment, enter `Y` to confirm the resources you want to create.

   After the creation is complete, a message "`service demo deploy success`" appears, indicating that your resources are deployed.

## Step 4: Invoke the function

1. Run the following command to invoke the function and you should see `hello world` returned by the function:

    ```bash
    fun invoke demo
    ```

## Step 5: Update the function

1. Open <tutorial-editor-open-file filePath="fc-tutorials/demo/index.js"> index.js </tutorial-editor-open-file> file and change `hello world` to `hello world from function compute`.

2. Run the following command to deploy the function:
    ```bash
    fun deploy
    ```

3. Run the following command to invoke the function and now you should see `hello world from function compute`:

    ```bash
    fun invoke demo
    ```
