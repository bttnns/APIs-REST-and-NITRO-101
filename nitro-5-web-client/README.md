# NITRO 5: The Web Client

## Overview

In this exercise, you will learn about and utilize the built-in NITRO
web client.

## Exercise 1: Add Load Balancing Virtual Servers using the NITRO Web Client

1.  To get to the NITRO web client first open the **NS2 bookmark within Mozilla Firefox**. Login using the **username nsroot and password nsroot**. Click on the **Documentation** tab at the top right and select **NITRO Client**.

![](./img/media/image112.png)

2.  We are going to create the same load balancing virtual server that we created in exercise four. Begin by heading to **Configuration -&gt; Load balancing -&gt; lbvserver**.

Select an **add** operation under **Select Operation**. Specify the following attributes by picking them in the **Select Attributes dropdown, filling in the value**, and clicking **Add**.

```
Name: WWW
Servicetype: HTTP
Ipv46: 192.168.10.32
Port: 80
```

Click on **GO**.

![](./img/media/image113.png)

3.  Verify that the virtual server was created by acknowledging the same HTTP status of 201 created you saw in exercise 4.

![](./img/media/image114.png)

4.  Next we will specify a load balancing virtual server service binding.

Expand **Configuration -&gt; Load Balancing -&gt; lbvserver_service_binding.**

Select the **add** operation. Specify the following attributes:

```
Name: WWW
Servicename: WWW1
```

Click **GO**.

![](./img/media/image115.png)

5.  Verify that the service was bound to the virtual server by checking for a **200 OK HTTP status.**

![](./img/media/image116.png)

6.  Test that your newly created virtual server works by heading to **<http://192.168.10.32> in Mozilla Firefox.**

![](./img/media/image117.png)

## Exercise 2: Delete Load Balancing Virtual Servers using the NITRO Web Client

1.  Delete the load balancing virtual server by heading to **Configuration -&gt; Load Balancing -&gt; lbvserver**.

Select the **delete** operation. Specify the **resource name** of **WWW.** Click **GO.**

![](./img/media/image118.png)

2.  Verify that the resource was deleted by receiving a 200 OK HTTP Status.

![](./img/media/image119.png)

## Exercise Summary

In this exercise, you created a load balancing virtual server, bound a service, and deleted that virtual server using the built-in NITRO web client.