# NITRO 7: Advanced NITRO Automation via Python

## Overview

In this exercise, you will use a pre-scripted python environment to
utilize the NITRO Python SDK to configure NS1.

## Exercise 1: NetScaler NITRO Automation via Python

1.  To begin, open SuperPuTTY.

![](./img/media/image131.png)

2.  Connect to TOOLS1 by double clicking on TOOLS1 in the right sidebar.

![](./img/media/image132.png)

3.  Login using the password: **Password1.**

![](./img/media/image133.png)

1.          | Execute the script to automate    |
 | the configuration of NS1 by       |
 | running the command    |
 |  |
 | python ns1conf.py      |
 |  |
 | ![](./img/media/image134.png){wid |
 | th="2.96916447944007in"|
 | height="0.20836286089238845in"}   |
----------------------------------+-----------------------------------+
1.          | The script executes to configure  |
 | the NetScaler.         |
 |  |
 | ![](./img/media/image135.png){wid |
 | th="3.0941819772528434in"         |
 | height="2.437840113735783in"}     |
----------------------------------+-----------------------------------+
1.          | Verify the load balancing virtual |
 | server has been created by        |
 | heading to  |
 | **<http://192.168.10.22> in       |
 | Google Chrome.**       |
 |  |
 | ![](./img/media/image136.png){wid |
 | th="5.6674573490813644in"         |
 | height="2.6462029746281717in"}    |
----------------------------------+-----------------------------------+
1.          | You can view the contents of the  |
 | python script if you wish by      |
|  | typing the command:\   |
|  | **more ns1conf.py**    |
|  |  |
|  | ![](./img/media/image137.jpeg)    |
+-----------------------------------+-----------------------------------+
| 1.          | The next steps I challenge you to |
|  | create your own python script to  |
|  | output the total hits and hit     |
|  | rate of the lbvserver WWW.        |
|  |  |
|  | You will need to create this code |
|  | on the tools server that you are  |
|  | already connected to. This is     |
|  | pretty much already done for you; |
|  | you just need to edit the         |
|  | previous script. Let’s copy the   |
|  | script by running the command     |
|  | **cp ns1conf.py**      |
|  | **ns1monitor.py** and edit it by  |
|  | running **nano ns1monitor.py**    |
|  | Edit this by removing all         |
|  | unnecessary elements to configure |
|  | the NetScaler, leaving the        |
|  | monitoring section. Exit by       |
|  | running **CTRL+X** and run the    |
|  | script by running **python        |
|  | ns1monitor.py** If all went       |
|  | correctly you should have a       |
|  | script that only shows the hits   |
|  | and hit rate of the WWW|
|  | lbvserver. If you wish you can    |
|  | use the python API documentation  |
|  | and experiment with your own      |
|  | scripts.    |
|  |  |
|  | You will want to utilize the      |
|  | python API documentation hosted   |
|  | on the NetScaler found in the     |
|  | **Downloads Tab.** Lucky for you  |
|  | I have included this bookmark in  |
|  | **Google Chrome under Other       |
|  | Bookmarks.**|
|  |  |
|  | ![](./img/media/image138.png){wid |
|  | th="5.992361111111111in"          |
|  | height="0.9694444444444444in"}    |
|  |  |
|  | Here I went to config -&gt; lb    |
|  | -&gt; lbvserver and you can see   |
|  | the class methods of each         |
|  | element.    |
|  |  |
|  | ![](./img/media/image139.png){wid |
|  | th="5.992361111111111in"          |
|  | height="6.211111111111111in"}     |
|  |  |
|  | Good luck!  |
+-----------------------------------+-----------------------------------+

### Exercise Summary

In this exercise, you ran the automation configuration script for NS1
and possibly created your own script to monitor the lbvserver.