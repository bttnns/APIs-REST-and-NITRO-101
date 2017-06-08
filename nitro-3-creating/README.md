# NITRO 3: Adding, Updating, and Deleting configurations

## Overview

In this exercise, you will further your NITRO skillset by utilizing the
add, update, and delete functionality of the NITRO API. For this
exercise, we will be utilizing NS2, which is a fresh, clean
configuration NetScaler.

## Exercise 1: Enable NetScaler Features

1.  Use your knowledge (or the postman history) to perform a login to NS2.training.lab. Exercise 2 Step 6 should help if you need assistance. Remember to change the URL to NS2.training.lab

2.  For this exercise, we will be utilizing **NS2**, which is a fresh, clean configuration NetScaler. Since our goal is to enable a load balanced virtual server we will need to first enable the load balancing feature.

We will head to the **NITRO API Docs on Google Chrome** and open the **Configuration -&gt; NS -&gt; NSFeature** element. We will find the **enable** method.

Make note of the **URL, HTTP Method, and Request Payload.**

![](./img/media/image82.png)

3.  [Create the request by opening **Postman**, clicking **Plus (+)** and entering **http://ns2.training.lab/nitro/v1/config/nsfeature?action=enable**](http://ns2.training.lab/nitro/v1/config/nsfeature?action=enable) for the **request URL**. Set the **HTTP Method to** **POST**. We will set the **URL Parameter Key** to **action** with a **value** of **enable** as per the documentation. We will also include the **Content-Type** **header** with **value** of **application/json** The **Data** payload will be set to **raw** with the data of:

```json
{
  "nsfeature":
  {
    "feature":
    [
      "lb"
    ]
  }
}
```

![](./img/media/image83.png)

![](./img/media/image84.png)

4.  Finally click Send. You should see a status of 200 OK meaning that the feature was enabled.

![](./img/media/image85.png)

## Exercise 2: Add a Load Balancing Virtual Server

1.     Next we need to add a load balancing virtual server.

We open the **NITRO API Docs** and head to **Configuration -&gt; Load Balancing -&gt; lbvserver**. Find the **add method**. Make note of the **URL, HTTP Method, and Request Payload.**

![](./img/media/image86.png)

> Note: The values marked in RED are mandatory fields which always must be provided.

2.     Open **Postman**, click **the Plus (+)** and enter [**http://ns2.training.lab/nitro/v1/config/lbvserver**](http://ns2.training.lab/nitro/v1/config/lbvserver) as the **request URL**. We will set the **HTTP Method to POST** and configure a **header** of **Content-Type** with **value** of **application/json** The payload will be set to **Data and Raw** with the data of

```json
{
  "lbvserver":
  {
    "name":"WWW",
    "servicetype":"http",
    "ipv46":"192.168.10.32",
    "port":80
  }
}
```

![](./img/media/image87.png)

![](./img/media/image88.png)

3.  Click on **Send**. You should see an **HTTP status of 201 Created** if the virtual server was added.

![](./img/media/image89.png)

4.  The next step of adding a load balanced virtual server is to add some services to load balance.

First we need to create the services.

To do so we head to the **NITRO API Docs** and open **Configuration -&gt; Basic -&gt; Service.** Find the **add method.** Make note of the **URL, HTTP Method, and Request Payload**.

![](./img/media/image90.png)

> Note: The items in red are the required fields.

5.  Now we will build the request.

Open **Postman**, and click on **Plus (+)**. We will enter [**http://ns2.training.lab/nitro/v1/config/service**](http://ns2.training.lab/nitro/v1/config/service) as the **request URL** with the **Content-Type** **header** and **value** of **application/json** We will set the payload data to **Data and Raw** and fill in the field with

```json
{
  "service":
  {
    "name":"WWW1",
    "servicetype":"http",
    "ip":"192.168.10.50",
    "port":80
  }
}
```

![](./img/media/image91.png){width="5.992361111111111in" height="3.029861111111111in"}

![](./img/media/image92.png){width="5.209060586176728in" height="1.2397561242344708in"}

6.  Send the request and notice that the **HTTP Status** returned should **201 Created**, meaning the service was created.

![](./img/media/image93.png)

7.  Now we will bind the newly created service to the load balancing virtual server that we also just created.

We will open the **NITRO API Docs** and head to **Configuration -&gt; Load Balancing -&gt; lbvserver_service_binding.** Find the **add method**. We will make note of the **URL, HTTP Method, and Request Payload.**

![](./img/media/image94.png)

8.  To bind the service, we will create the request above.

Open **Postman** and click on **Plus (+)**. Enter the **request URL** of [**http://ns2.training.lab/nitro/v1/config/lbvserver\_service\_binding**](http://ns2.training.lab/nitro/v1/config/) with the **Content-Type** **header** and **value** of **application/json** The data type will also be set to **raw** and we will fill in the field with

```json
{
  "lbvserver\_service\_binding":
  {
    "name": "WWW",
    "servicename": "WWW1"
  }
}
```

![](./img/media/image95.png)

![](./img/media/image96.png)

9.  ***Challenge!***

Add a service named WWW2 with IP Address 192.168.10.51, service type of http, and port 80. Bind that newly created service to WWW.

10.  Test your newly created load balancing virtual server by opening **Google Chrome** and heading to the URL [**http://192.168.10.32**](http://192.168.10.32). You should be able to click refresh and see that the service IP changed from 192.168.10.50 to 192.168.10.51 if you successfully completed the challenge above.

![](./img/media/image97.png)

## Exercise 3: Delete a Load Balancing Virtual Server

1.  Now we will delete the load balancing virtual server that we just created.

We will open the **NITRO API Docs** and head to **Configuration -&gt; Load Balancing -&gt; lbvserver**. We will find the **delete** method. Make note of the **URL and HTTP Method.**

![](./img/media/image98.png)

2.  Open **Postman** and click **Plus (+)**.

Enter the **request URL** of [**http://ns2.training.lab/nitro/v1/config/lbvserver/WWW**](http://ns2.training.lab/nitro/v1/config/lbvserver/WWW) and **HTTP Method of** **DELETE**. Set the **Accept** **header** to **application/json** Be sure that the Body tab is empty.

![](./img/media/image99.png)

![](./img/media/image100.png)

3.  Click **Send** and notice that the **Status is a 200 OK**, meaning that the virtual server has been deleted.

![](./img/media/image101.png)

## Exercise 4: MacroAPI - Send Multiple Configurations in one NITRO API Request

1.  Now let’s use the NetScaler NITRO Macroapi to create a lbvserver, service group, and bindings all in one API call. The macroapi was introduced in 11.1. This allows us to send multiple API requests at one time.

Open **Postman** and click on **Plus (+)**. Enter the **request URL** of **http://ns2.training.lab/nitro/v1/config/macroapi** with the **Content-Type** **header** and **value** of **application/json** The data type will also be set to **raw** and we will fill in the field with

```json
{
  "lbvserver": [
    {"name": "lbv1", "servicetype": "http"},
    {"name": "lbv2", "servicetype": "http"}
  ],
  "servicegroup": [
    {"servicegroupname": "sg1", "servicetype": "http"},
    {"servicegroupname": "sg2", "servicetype": "http"}
  ],
  "servicegroup\_servicegroupmember\_binding": [
    {"servicegroupname": "sg1", "ip": "1.1.1.1", "port": 80},
    {"servicegroupname": "sg1", "ip": "1.1.1.2", "port": 80},
    {"servicegroupname": "sg2", "ip": "1.1.2.1", "port": 80}
  ],
  "lbvserver\_servicegroup\_binding": [
    {"name": "lbv1", "servicegroupname": "sg1"},
    {"name": "lbv2", "servicegroupname": "sg2"}
  ]
}
```

![](./img/media/image102.png)

2.  ![](./img/media/image103.png)

3.  Click on **Send.** Your response should be a **HTTP Status of 201 Created**.

![](./img/media/image104.png)

## Exercise Summary

In this exercise, you utilized the add, update, and delete functionality of the NITRO API. We first went through and enabled a NetScaler feature. Then we added a load balancing virtual server, followed by adding a few services. We bound those services to the load balancing virtual server and tested the server. We finally deleted the virtual server that we just created.