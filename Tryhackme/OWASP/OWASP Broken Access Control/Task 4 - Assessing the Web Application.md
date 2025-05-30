#### Assessing the Application:

When you browse a web application as a penetration tester, imagine what the underlying code looks like and what vulnerabilities come to mind for each functionality, request, and response.

The web application for this room features a Dashboard, Login, and Registration form that enables users to access the dashboard of the website. From a web app pentester standpoint, the pentester will usually register an account. After the registration, the pentester will then try to check the login function for any access control vulnerabilities.

Below are the screenshots of each webpage:

**Registration:**

![Registration Page](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/1b103a3eb8b3bda9f399da0702de7655.png)

**Login:**

![Login Page](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/34f8072b8919303582352d6a1d914579.png)

**Dashboard:**

![Dashboard Page](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/95f2bd55c06a13d47ab06ee6a8a0b6cd.png)

In order for us to capture the HTTP requests being sent to the server, we can use [OWASP ZAP](https://www.zaproxy.org/) or Burp Suite Community Edition.

To learn more about the detailed usage of Burp Suite and its functionalities, you may refer to the [Burp Suite Module](https://tryhackme.com/module/learn-burp-suite).

#### Capturing the HTTP traffic

In order for us to further analyze the requests and responses being sent and received from the server, we will use the **“Proxy”** module of Burp Suite to capture the HTTP traffic that is being sent to the server. The captured HTTP traffic can be used with the other modules of Burp Suite.

These can then be manipulated or sent to other tools, such as **“Repeater”**, for further processing before being allowed to continue to their destination. 

Below is the captured HTTP traffic that is being sent to `functions.php` after login.

![Captured HTTP traffic](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/85d5720c06d8e1d993730cbf1a790849.png)

Based on the screenshot displayed above, we can observe that upon completing the login process, the web application will give us a JSON response that contains the status, message, first_name, last_name, is_admin, and redirect_link which the server uses to redirect the user to the `dashboard.php` with the parameter “isadmin” in the URL.

#### Understanding the content of the HTTP request and response:

- The target web application does not have any implemented security headers, which indicates that there are no preventative measures (like a first line of defense) in place to protect the web application against certain types of attacks.
- The target web application is running on a Linux operating system (`Debian`) and is using Apache web server (`Apache/2.4.38`). This information can be useful in identifying potential security vulnerabilities that may exist in the target web application.
- The target web application utilizes `PHP/8.0.19` as its backend programming language. This information is important for understanding the technology stack of the application and identifying potential security vulnerabilities or compatibility issues that may arise with other software components.
- The target web application redirects the user to the dashboard with a parameter that we can possibly test for privilege escalation vulnerabilities.

Answer the questions below

What is the type of server that is hosting the web application? This can be found in the response of the request in Burp Suite.
	Apache

What is the name of the parameter in the JSON response from the login request that contains a redirect link?
	redirect_link

What Burp Suite module allows us to capture requests and responses between ourselves and our target?
	Proxy

What is the admin's email that can be found in the online users' table?
	admin@admin.com

[[OWASP TOP 10 - 2021]]
[[Taskk 5 - Exploiting the Web Application]]

