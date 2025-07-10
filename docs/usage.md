# Ollama Inference Framework  
## Product Link  
[Ollama Inference Framework](https://marketplace.huaweicloud.com/intl/hidden/contents/e81fb144-b2c8-4f64-802a-8183548f0752)  

## Product Description  
[Ollama](https://ollama.com/) is a cross-platform inference framework client (MacOS, Windows, Linux) designed for seamless deployment of large language models (LLMs) such as Llama 2, Mistral, Llava, and more. With one-click setup, Ollama enables local execution of LLMs, keeping all interaction data on your own machine to enhance data privacy and security.  

This product is provided as a pre-installed image on Kunpeng Cloud with Ubuntu 24.04 and HCE 2.0 systems for user convenience.  

## Product Purchase  
You can search for "Ollama Inference Framework" in the cloud marketplace.  
For **Region** and **Specifications**, use the recommended configurations. The **Purchase Method** can be selected based on your needs—**Pay-as-you-go** for short-term use or **Monthly/Yearly** for long-term use. After confirming the configuration, click **"Buy Now"**.  

![alt text](./images/image.png)  

### Direct Deployment Using RFS Template  
![img.png](images/img1.png)  
Fill in the required fields and click **Next**.  
![img.png](images/img2.png)  
![img.png](images/img3.png)  
After creating the deployment plan, click **Confirm**.  
![img.png](images/img4.png)  
![img.png](images/img5.png)  
Click **Deploy** to execute the plan.  
![img.png](images/img6.png)  
The message **"Apply required resource success."** indicates that the resources have been successfully created.  
![img.png](images/img7.png)  

### ECS Console Configuration  
#### Preparations  

Before configuring the ECS console, you need to set up **Security Group Rules** in advance.  

> **Security Group Rules Configuration:**  
> - Allow inbound traffic on port **11434**, ensuring the source IP range includes your client IP; otherwise, access will be denied.  
> - Allow inbound traffic on port **22** for CloudShell connections to enable console debugging.  
> - Enable full outbound traffic.  

#### Creating an ECS  

After completing the preparations, navigate to the [ECS Purchase Page](https://support.huaweicloud.com/qs-ecs/ecs_01_0103.html) via the ECS console. Configure the ECS resources as shown below:  

**Select CPU Architecture**  
![img.png](images/img8.png)  
**Select Server Specifications**  
![img_1.png](images/img_1.png)  
**Select Image**  
![img_2.png](images/img_2.png)  
Fill in other parameters according to your actual needs, then click **Buy Now**.  
![img_3.png](images/img_3.png)  

> **Important Notes:**  
> - You can create a **VPC** yourself.  
> - Select the **Security Group** configured in the [**Preparations**](#preparations) section.  
> - For **Elastic Public IP**, select **"Purchase Now"** and choose **"Pay-by-Traffic"** (recommended). Set the bandwidth to **5Mbit/s**.  
> - **Advanced Configuration** requires custom data injection, so **Login Credentials** cannot be set as **"Password"**—select **"Set After Creation"** instead.  
> - Other settings can be left as default or configured as needed.  

## Product Usage  
### Logging into the Server to Check Ollama Service Status  
- Use the command `systemctl status ollama` to check the service status.  
![alt text](./images/image-4.png)  

### Downloading Models & Starting Models (Ollama Manual)  
[Ollama Manual](https://ollama.cadn.net.cn/#quickstart)
