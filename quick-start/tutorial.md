# Create a function by using Funcraft

This topic describes how to create a function in Function Compute by using Funcraft. In this topic, a Hello World function is created.

## Prerequisites
-------------

* [Activate the Function Compute service](t1880966.html#multiTask782/section-938-43e-c63)

* You have [installed the command-line tool Fun](https://github.com/alibaba/funcraft/blob/master/docs/usage/installation-zh.md?spm=a2c4g.11186623.2.16.4cc918b1zLFgpb&file=installation-zh.md).


Funcraft is an application deployment tool provided by Function Compute. It allows you to conveniently manage resources of Function Compute, API Gateway, and Log Service to quickly deploy applications.

## Step 1: Configure Funcraft 
-----------------------------------------------

1. Run the following command to initialize Funcraft and open the account information configuration page:
    ```bash
    fun config
    ```
   

2. Sequentially specify AccountID (the ID of the Alibaba Cloud account), AccessKey ID, AccessKey Secret, and Default Region Name for Funcraft as instructed.

   If you are using a Resource Access Management (RAM) user, set AccountID to the account ID of the corresponding Alibaba Cloud account and set AccessKey ID and AccessKey Secret to the AccessKey pair of the RAM user.
   **Note** You can obtain your Alibaba Cloud account ID from [Account Management](https://account.console.aliyun.com/) and AccessKey ID and AccessKey Secret from [User Management](https://usercenter.console.aliyun.com/).
   After the configuration is completed, Funcraft saves the configurations to the *.fcli/config.yaml* file in your directory.

   For more information about how to configure Funcraft, see [Configure Funcraft](t1881165.html#concept-2260072).
   




## Step 2: Create an initialization template 
--------------------------------------------------------------

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

   * The `index.js` file contains the sample code of the function. 
   
   * The `template.yml` file describes how Funcraft creates function resources.
     * In this example, the `demo` service and the `demo` function are created for you.
     
     * For more configuration items supported by the template.yml file, see [Serverless Application Model](https://github.com/alibaba/funcraft/blob/master/docs/specs/2018-04-03-zh-cn.md).
     

     
   

   




## (Optional) Step 3: Locally debug the function 
------------------------------------------------------------------

To locally debug the function, you must install Docker locally. For more information, see [Install Docker](https://github.com/alibaba/funcraft/blob/master/docs/usage/installation-zh.md?file=installation-zh.md#%E5%AE%89%E8%A3%85-docker%E5%8F%AF%E9%80%89). If you cannot install Docker locally, skip this step and debug the function in the Function Compute console.

Run the following command locally to debug the function:

    ```bash
    cd demo
    fun local invoke demo
    ```

**Note** It takes a long time to debug the function for the first time because the image of the execution environment is pulled locally.

## Step 4: Deploy the function to the Function Compute console 
--------------------------------------------------------------------------------

1. Run the following command to deploy the function to the Function Compute console:
    ```bash
    fun deploy
    ```
   

2. During deployment, enter `Y` to confirm the resources you want to create.

   After the creation is complete, a message "`service demo deploy success`" appears, indicating that your resources are deployed.
   




## Step 5: Test the function in the Function Compute console 
------------------------------------------------------------------------------

You can log on to the Function Compute console to check whether the preceding deployment is successful.

1. Log on to the [Function Compute console](https://fc.console.aliyun.com).

   

2. In the top navigation bar, select a region.

   

3. In the left-side navigation pane, click **Service/Function** .

   

4. On the page that appears, click the demo service. On the Functions tab, click the demo function.


5. On the page that appears, click the **Code** tab. On the Code tab, click **Invoke** to execute the function in the Function Compute console.




## Step 6: View execution logs of the function 
----------------------------------------------------------------

You can view the execution logs on the current page after each execution. To view historical execution logs, click the **Log** tab. You must configure a Logstore for the function first. For more information, see [Configure and view function logs](t1881019.html#multiTask2691).





