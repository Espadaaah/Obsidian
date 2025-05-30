#### What is Access Control?

Access control is a security mechanism used to control which users or systems are allowed to access a particular resource or system. Access control is implemented in computer systems to ensure that only authorized users have access to resources, such as files, directories, databases, and web pages. The primary goal of access control is to protect sensitive data and ensure that it is only accessible to those who are authorized to access it.

![Example of Access Control](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/c0163e47202f8fb14d0d9bf407fb65df.png)

Access control can be implemented in different ways, depending on the type of resource being protected and the security requirements of the system. Some common access control mechanisms include:

1. **Discretionary Access Control (DAC)**: In this type of access control, the resource owner or administrator determines who is allowed to access a resource and what actions they are allowed to perform. DAC is commonly used in operating systems and file systems. In layman’s terms, imagine a castle where the king can give keys to his advisors, allowing them to open any doors they like, whenever they want. That’s DAC for you. It’s the liberty to control access to your own resources. The one in charge, like the king of the castle, can hand out permissions to whomever they please, dictating who can come in and out.
    
    ![Example of Discretionary Access Control](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/fda89930eb8e0fe0be0bc2b0050df2bb.png)
    
2. **Mandatory Access Control (MAC)**: In this type of access control, access to resources is determined by a set of predefined rules or policies that are enforced by the system. MAC is commonly used in highly secure environments, such as government and military systems. In layman’s terms, picture a fort with an iron-clad security protocol. Only specific individuals with particular security clearances can access certain areas, and this is non-negotiable. The high commander sets the rules, and they are rigorously followed. That’s how MAC works. It’s like the stern security officer who allows no exceptions to the rule.
    
    ![Example of Mandatory Access Control](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/680f5f2a359b86e88a01f75509b48976.png)
    
3. **Role-Based Access Control (RBAC)**: In this type of access control, users are assigned roles that define their level of access to resources. RBAC is commonly used in enterprise systems, where users have different levels of authority based on their job responsibilities. In layman’s terms, imagine a modern corporation. You have your managers, your executives, your sales staff, etc. They each have different access to the building. Some can enter the boardroom, others can access the sales floor, and so on. That’s the essence of RBAC - assigning access based on a person’s role within an organization.
    
    ![Example of Role-based Access Control](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/951b891b22025b3a67b2675361b23415.png)
    
4. **Attribute-Based Access Control (ABAC)**: In this type of access control, access to resources is determined by a set of attributes, such as user role, time of day, location, and device. ABAC is commonly used in cloud environments and web applications. In layman’s terms, think of a highly advanced sci-fi security system that scans individuals for certain attributes. Maybe it checks whether they’re from a particular planet, whether they’re carrying a specific device, or if they’re trying to access a resource at a specific time. That’s ABAC. It’s like the smart, flexible security of the future.
    
    ![Example of Attribute-Based Access Control](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/0057e9b8b5ea7f0e1bed9c33f586163b.png)
    

Implementing access control can help prevent security breaches and unauthorized access to sensitive data. However, access control is not foolproof and can be vulnerable to various types of attacks, such as privilege escalation and broken access control vulnerabilities. Therefore, it is important to regularly review and test access control mechanisms to ensure that they are working as intended.

#### Broken Access Control:

Broken access control vulnerabilities refer to situations where access control mechanisms fail to enforce proper restrictions on user access to resources or data. Here are some common exploits for broken access control and examples:

1. **Horizontal privilege escalation** occurs when an attacker can access resources or data belonging to other users with the same level of access. For example, a user might be able to access another user’s account by changing the user ID in the URL.
    
2. **Vertical privilege escalation** occurs when an attacker can access resources or data belonging to users with higher access levels. For example, a regular user can access administrative functions by manipulating a hidden form field or URL parameter.
    
    ![](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/fa3bb36f2fde2bd29aa290ff2610428d.png)  
    
3. **Insufficient access control checks** occur when access control checks are not performed correctly or consistently, allowing an attacker to bypass them. For example, an application might allow users to view sensitive data without verifying their proper permissions.
    
4. **Insecure direct object references** occur when an attacker can access a resource or data by exploiting a weakness in the application’s access control mechanisms. For example, an application might use predictable or easily guessable identifiers for sensitive data, making it easier for an attacker to access. You may refer to this [room](https://tryhackme.com/room/owasptop102021) in **Task #4** to learn more about this.
    
    ![Example of Insecure direct object references](https://tryhackme-images.s3.amazonaws.com/user-uploads/645b19f5d5848d004ab9c9e2/room-content/55df42c444edbd2a24f7973b5792b769.png)
    

These exploits can be prevented by implementing strong access control mechanisms and regularly reviewing and testing them to ensure they are functioning as intended.

Answer the questions below

What is IDOR?
	Insecure direct object reference

What occurs when an attacker can access resources or data belonging to other users with the same level of access?  
	Horizontal privilege escalation

What occurs when an attacker can access resources or data from users with higher access levels?  
	Vertical privilege escalation

What is ABAC?
	Attribute-Based Access Control

What is RBAC?
	Role-Based Access Control


[[Task 4 - Assessing the Web Application]]
