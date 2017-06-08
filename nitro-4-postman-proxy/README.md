# NITRO 4: Enable Postman Proxy

## Overview

In this exercise, you will enable and configure the Postman Proxy functionality. The proxy allows you to track and intercept all RESTful communication that occurs between your browser (Mozilla Firefox) and the server, in our case NITRO and the NetScaler.

## Exercise 1: Enable Postman Proxy

1.  We are going to enable **Postman Proxy** to capture our next exercise to review later. To do so click on the **Postman Proxy button inside of Postman**.

![](./img/media/image105.png)

2.  Next click **Connect**.

![](./img/media/image106.png)

3.  You should verify the Proxy is enabled by the notification that flashes by **stating Proxy Connected**, as well as the **Postman Proxy Icon changing to orange**.

![](./img/media/image107.png)

## Exercise 2: Configure Mozilla Firefox to use Postman Proxy

1.  Next, Open **Mozilla Firefox** by double clicking the icon on the desktop.

![](./img/media/image108.png)

2.  Within **Firefox** click on the **Settings** menu and choose **Options**.

![](./img/media/image109.png)

3.  Head to **Advanced -&gt; Network** and choose **Settings** under the Connection menu.

![](./img/media/image110.png)

4.  Choose **Manual Proxy Configuration** and specify **HTTP Proxy as 127.0.0.1 and Port as 5555**. Click **OK** and **close the Options Tab**.

![](./img/media/image111.png)

## Exercise Summary

In this exercise, you enabled Postman Interceptor to capture all RESTful browser communication from Mozilla Firefox. We will review this data in a future exercise. This quick exercise might feel a bit out of place, but you will see why we did it here in an upcoming exercise.