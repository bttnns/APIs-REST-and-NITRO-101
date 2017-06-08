# NITRO 2: Getting Configuration and Statistics

## Overview

In this exercise, you will work with the NITRO API to request and
retrieve configuration and statistics from NetScaler.

## Exercise 1: Getting Enabled NetScaler Modes and Features

1.  The first step of any interaction with NITRO is to login. Open **Postman** and head to the **History tab**. From here we can see the **login method** that we utilized earlier. Click on this method and hit **send**. Be sure you receive a **201 as the HTTP Status** in the response area.

![](./img/media/image56.png)

> Note: If you receive an HTTP Status other than 201 try to delete the cookies in Postman by following the troubleshooting step referenced in Exercise 1’s login steps and send the request again.

2.  Let’s begin by getting the configuration of the NetScaler modes that are enabled and disabled.

Like always, we will begin with the documentation. We can find the nsmode documentation by heading to the **NITRO API Docs in Google Chrome** and heading to **Configuration -&gt; NS -&gt; nsmode**. Find the **get** **method**. Here we will make note of the **URL and HTTP Method**.

![](./img/media/image57.png)

3.  As per the documentation, now we will head to **Postman** and create our request. Click on **Plus (+)** and fill in the **request URL** of [**http://ns3.training.lab/nitro/v1/config/nsmode**](http://ns3.training.lab/nitro/v1/config/nsmode) with **HTTP Method of GET**. We will open the **Headers** and add the **Accept** header key with value of **application/json**

![](./img/media/image58.png)

> Note: You may notice that the header we are including in our request is different than the header that was included in the previous requests. When performing, an HTTP GET or HTTP DELETE to NITRO we need to include the Accept header instead of the Content-Type header. The value of the header remains the same as before.

4.  We will send the response by clicking **Send**. Acknowledge the **200 OK status** meaning all is well and **make note of the response body**. The nsmodes that are enabled are shown in the **mode array**. You can also see individual nsmodes below and if they are enabled, value of true, or disabled, value of false.

![](./img/media/image59.png)

5.  Compare this to the modes that you see enabled in the NS3 NetScaler GUI.

To do so, head to **Google Chrome and open NS3**. Login using the default credentials of username **nsroot** and password **nsroot**.

![2016-11-10 07\_56\_41-studentdesktop - Citrix Receiver](./img/media/image33.png)

Head to the **Configuration tab** and expand the **System** element in the sidebar. Head to **Settings and click Configure Modes.**

![](./img/media/image60.png)

Here we see the same modes that are enabled and disabled as above.

![](./img/media/image61.png)

> Note: The NITRO API utilizes aliases for each nsmode name. You can decipher the list in the NITRO Documentation Read Only Properties to understand what each nsmode alias means. Below is an excerpt of the documentation.*

![](./img/media/image62.png)

6.  ***Challenge! Let’s get the NetScaler features that are enabled and disabled.***

Reference the **NITRO API Docs in Google Chrome** by heading to **Configuration -&gt; NS -&gt; nsfeature**.

![](./img/media/image63.png)

Reference the results you got from the NITRO API to the NS3 GUI. You should see the same items enabled and disabled.

*SSL, LB, Rewrite, CS, SP, WL, Cloudbridge*

## Exercise 2: Getting all available Load Balancing Virtual Servers

1.  Next we will get all available load balancing virtual servers and their configurations.

We will head to the documentation by opening Google Chrome, heading **to NITRO API Docs** and clicking **Configuration**. We will go to **Load Balancing followed by lbvserver**. Find the **get (all) method**. Make note of the **URL and the HTTP Method**. Like before, since we are getting content the method is an HTTP GET.

![](./img/media/image64.png)

2.  We will open Postman and click on the **Plus (+)** button.

We will fill in the **request URL** of **<http://ns3.training.lab/nitro/v1/config/lbvserver>** with **HTTP Method of GET**. Select the **Headers** and fill in the **Accept** header’s value of **application/json**

![](./img/media/image65.png)

3.  Next we will click **Send**. Acknowledge the **HTTP Status of 200** and the body that was returned. We should see two lbvservers, **WWW** and **TOOLS**. For information about each returned item you can refer to the documentation.

![](./img/media/image66.png)

## Exercise 3: Filtering Responses

1.  Having all the data in one call can be great, but sometimes we might only require a subset of data to be returned. This concept applies to most GET methods in NITRO. We can find this method of **get** in the nitro documentation. *Note: Not get (all)*

![](./img/media/image67.png)

In this request, we want to only return the name, load balancing method, and persistence type of the WWW virtual server.

To do so we edit the **request URL in Postman** to be [**http://ns3.training.lab/nitro/v1/config/lbvserver/WWW**](http://ns3.training.lab/nitro/v1/config/lbvserver/WWW) Here we add WWW at the tail end of the url. This tells NITRO to only return the lbvserver WWW.

We will add a **URL parameter (params)** to limit the data that gets returned by adding the **attrs** **URL Parameter Key** with **value** of **name,lbmethod,persistencetype** Be sure not to include spaces. (*Note: If you do not see URL Parameter Key and Values click the Params button*)

Since this is a NITRO GET method we need to be sure to include the **Accept** **header** and its **value** of **application/json**

![](./img/media/image68.png)

2.  Click send and notice **HTTP Status of 200** and the **body** that was returned. We successfully only returned the WWW virtual server with a few data points.

![](./img/media/image69.png)

3.  **Challenge! **

Apply your knowledge of getting configuration elements within NITRO to get the list of names and ports of all the services enabled within NS3. Your response body should be:

![](./img/media/image70.png)

Hint: The Service documentation can be found in the documentation at Configuration -&gt; Basic -&gt; Service and your method will be get (all).

Hint 2: attrs

4.       Let’s now get all lbvservers who’s port is equal to 80. To do so we will need to perform a **filter**.

Open the NITRO API Docs and head to **Configuration -&gt; Load Balancing -&gt; lbvserver**.

Find the **get (all) method**. Here we will focus on **filter**.

![](./img/media/image71.png)

To perform the filter, we will open Google Chrome **not postman** and enter the URL of http://ns3.training.lab/nitro/v1/config/lbvserver?filter=port:80

![](./img/media/image72.png)

We should see two lbvserver elements, WWW and TOOLS.

> Note: This request was performed in Google Chrome to showcase that you can use a standard web browser to preform HTTP GET requests to NITRO for simple one off tests.

## Exercise 4: Getting NetScaler Statistics

1.  Now we will use the HTTP GET method to get statistics from the NetScaler. The first thing that we will get would be general NetScaler stats.

Head to the **NITRO API Docs and open Statistics -&gt; NS -&gt; NS** and find the get (all) method. Make note of the **URL** and the **HTTP Method**.

![](./img/media/image73.png)

2.  Fill in the **request URL** of [**http://ns3.training.lab/nitro/v1/stat/ns**](http://ns3.training.lab/nitro/v1/stat/ns) with the **Accept header** of **application/json** Be sure your HTTP method is **GET**.

![](./img/media/image74.png)

3.  Click **Send** and make note of the objects that you received such as the **CPU Usage, and Memory usage**.

![](./img/media/image75.png)

4.  Next, let’s get details about the NetScaler’s interfaces.

Open the NITRO API Docs and head to **Statistics -&gt; Network -&gt; Interface**. Find the get (all) method and make note of the **URL and HTTP Method.**

![](./img/media/image76.png)

5.  Open Postman and enter [**http://ns3.training.lab/nitro/v1/stat/interface**](http://ns3.training.lab/nitro/v1/stat/interface) as the request URL with the **Accept** header of **application/json** Be sure to select **GET as the HTTP Method.**

![](./img/media/image77.png)

6.  Click on **Send** and notice the interfaces and their statistics such as uptime, transmit receive rate and send rate.

![](./img/media/image78.png)

7.  Lastly, get the statistics of the WWW Load Balanced Virtual Server.

Open Google Chrome and head to the NITRO API Docs. Open **Statistics -&gt; Load Balancing -&gt; lbvserver**. Find the get method and make note of the **URL and the HTTP Method.**

![](./img/media/image79.png)

8.  Enter [**http://ns3.training.lab/nitro/v1/stat/lbvserver/WWW**](http://ns3.training.lab/nitro/v1/stat/lbvserver/WWW) as the request URL with the **HTTP Method of GET**. Add the **Accept** header with value of **application/json** You may notice that we are filtering here similar to how we filtered with the configuration section by adding WWW after the lbvserver in the URL.

![](./img/media/image80.png)

9.  Click **Send** and note the statistics of the WWW lbvserver. Here we can see things such as health, state, request and hit rate, amongst others.

![](./img/media/image81.png)

If you wish, you can filter the data points in the response the same way that we did earlier by passing in the URL Param attrs with the value of the elements you wish to retrieve.

## Exercise Summary

In this exercise, you retrieved configuration and statistics via the NITRO API from the NetScaler appliance. We first retrieved the enabled and disabled NetScaler modes and features. Next we worked with the configuration of load balancing virtual servers and filtering. These methods of getting and filtering content and configuration can be applied to all various configuration methods of the NetScaler appliance such as Content Switching or Policy. We finally wrapped up with getting statistics from various aspects of the appliance.