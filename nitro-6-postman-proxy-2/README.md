# NITRO 6: Postman Proxy

## Overview

In this exercise, work with Postman Proxy to capture NITRO
configurations and replay them back to the NetScaler.

## Exercise 7.1: Postman History Sidebar

1.  Open Postman, open the Sidebar, and click on the History tab.

![](./img/media/image120.png)

Here you can see that Postman interceptor captured the NITRO requests that we sent the NetScaler via the previous exercise and posted them into our history. We could edit these requests and send them back to the NetScaler via Postman to perform the same or similar configurations.

In the example, above we successfully captured the configuration of the load balancing virtual server creation, service binding, and deletion.

## Exercise 2: Capture NetScaler Web GUI with Postman Proxy

1.  Now we will use the standard NetScaler GUI and capture a configuration into Postman using the Proxy.

Open the **NS2 bookmark in Mozilla Firefox** and login using the credentials username **nsroot** and password **nsroot**.

Head to the **configuration tab.**

Open **Traffic Configuration -&gt; Load Balancing -&gt; Virtual Servers.**

![](./img/media/image121.png)

2.  Click **Add.**

![](./img/media/image122.png)

3.  Enter the name **WWW** and IP address of **192.168.10.32**. Click **OK**.

![](./img/media/image123.png)

4.  Click on **No Load Balancing Virtual Server Service Binding.**

![](./img/media/image124.png)

5.  Click **Click to select.**

![](./img/media/image125.png)

6.  Select **All Services by checking every box** and click **Select**.

![](./img/media/image126.png)

7.  Click **Bind.**

![](./img/media/image127.png)


8.  Click **Continue.**

![](./img/media/image128.png)

9.  Open **Postman** and **scroll through your history in the History tab on the sidebar**. You will see **two to three POST methods**. *Three if you completed the Bonus Adding an Additional Service, two otherwise.*

Here we see the GUI sending a NITRO request to NetScaler creating the load balancing virtual server as well as two service binding operations. These are the same requests we have been doing through this lab!

![](./img/media/image129.png)

![](./img/media/image130.png)

> Note: If you do not see these methods double check that Postman Proxy is enabled by performing exercise 5. Delete the WWW virtual server and try this exercise again.

## Exercise Summary

In this exercise, you saw how you can use postman and postman interceptor to capture your NITRO requests to the NetScaler appliance via both the NITRO web client and the NetScaler GUI.