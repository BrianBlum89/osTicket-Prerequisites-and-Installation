# osTicket Prerequisites and Installation

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
Here I will outline the prerequisites and installation of the help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Remote Desktop 
- Internet Information Services 

<h2>Operating Systems Used </h2>

- Windows 10</b> 

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>

## Step 1  
To start we will create a Virtual machine using the Microsoft Azure portal. Once in you will search Virtual machines search bar and then select the create Virtual machine option. From here start by creating a resource group and title it "osTicket". Afterwards create a VM with 2-4 CPUs. 
  
![os ticketing creating vm step 1](https://github.com/user-attachments/assets/fb6de8f2-ae21-4e6e-a570-09fa8574d358)

## step 2 
</p>
<br />
<p>
</p>
<p> We will connect to our newly created VM using RDP 
</p>

![step two log into the VM](https://github.com/user-attachments/assets/39f51c65-e902-481d-b13d-c3e6c515025a)


## Step 3

</p>
<br />

<p>
</p>
<p>
You will have to enable IIS. To do this access the control panel then select uninstall a program. Off to the left select "Turn windows features on or off". A list will appear then you will enable Internet Information Services, then expand it, now expand world wide web services, and finally expand application development features from there we will enable CGI 
</p>  

![install ISS](https://github.com/user-attachments/assets/e4834740-3ea6-4704-b75b-8266b051d64a)

</p>
<br />
</p>
<p>

## Step 4

Now that we have enabled IIS we need to install PHP Manager, ISS Rewrite module i have included a google doc you can go to and download to get this as well as other files needed to get osTicket up and running that you will see me listing below 
https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD

![step 3 php manager](https://github.com/user-attachments/assets/dff62467-9571-44f8-8e08-803bfa6974bd)
![step 5 iss rewrite](https://github.com/user-attachments/assets/fd97d9d4-9891-45a3-80c0-c940ffbfeb59)

</p>
</p>
<p>

  ## Step 5
We are going to creat a file on the C drive and call it PHP. We are then going to extract the PHP zip file into the PHP file we created on the C Drive after doing this your going to instal Microsoft Visual C++

</p>

![step 6](https://github.com/user-attachments/assets/a8d98216-8738-4890-8dd3-26e7cdf96c91)
![step 6 part 2](https://github.com/user-attachments/assets/b6ff53ad-2627-40c9-8a21-23b411c1d2f8)

<p>
</p>
<p>

## Step 6 

Next download MySQL, this is a database that osTicket is going to use to store all our data in. This will hold all our user accounts and all our ticketing information when the download is done and you start setting up MySQL you will select standard configuration from there you will need to create a password aftewords hit next and execute

![step 7](https://github.com/user-attachments/assets/be96b4f9-a219-4d13-9c65-e988c3ae43d0)
![stpe 7 part 2](https://github.com/user-attachments/assets/f831446a-f385-415d-8334-be33742ed63a)


</P>


</p>
<br />
<p>
</p>

## Step 7
Now we are going to register PHP from within IIS so what you will do is go to your search bar search ISS 
and open as an admin, from there you will click PHP manager, Register new PHP version. Then we will upload register the PHP file highlighted in the picture below this will be located in the PHP file we saved to our C drive earlier after this is done we will go back to the main screen and restart the program by clicking stop and then start in the right hand corner 
</p>

![step 8](https://github.com/user-attachments/assets/260e99a4-0982-42a2-954e-78916af3a86a)
![step 8 part 2](https://github.com/user-attachments/assets/ef1507ca-44a4-49ee-acfd-ba3c1afaafdc)

<br />
<p>
</p>
<p>

## Step 8
Now we are finally going to go and unzip our our osTicket installation folder once we do that we will copy the folder titled "upload" from the unzipped file and copy it onto the folder on our C Drive titled "inetroot"
then we are going to rename upload to "osTicket" 
</p>

![os ticket](https://github.com/user-attachments/assets/d038b376-7c0a-4c10-b26d-03202dfcdaa4)

<br />
<p>
</p>
<p>

## Step 9 

We are no going to go back into ISS manager as an admin and restart it and attempt to browse to osTicket 
once restarted you are going to want to expand "sites","default web site" and click osTicket and attempt to browse to the site you can do this by clicking browse on the upper left hand side youll notice some of the extensions are not enabled you will want to enable those so that osTicket will work. In order to do this we will just go back to IIS PHP Manager and make some configurations. In the php manager you will 
"click enable or disable extentions" 
you are going to want to enable 

- php_imap.dll
- php_intl.dll
- php_opcache.dll

once you have done this refresh your broweser and you should see osTicket has now enabled these features

![browse to osTicket](https://github.com/user-attachments/assets/edc54fe6-6063-44fb-8f7e-918faa381e1f)
![image](https://github.com/user-attachments/assets/a473d90b-dfdd-49fa-b62d-1b7fdf1bead1)


## Step 10

now we will rename a file that osTicket uses to make configurations you are going want to change the name of the file 

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To :  C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign permissions to ost-config.php Disable inheritance->Removeall New Permissions->Everyone->all

![Capture](https://github.com/user-attachments/assets/d6a9f3b0-f742-484b-94ce-d766dc75068a)

<br />
<p>

## Step 11 

Afterwards continue setting up osTicket in the browser (click continue) then you will name the Helpdesk and  default email that will receive emails from customers who submit tickets. Before you click "install now"
we will need to download HeidiSQL from the folder you downloaded onto the PC from the google docs be sure the username and password match your username and password from MySQL once youve done this click open 
and then you will create a database called "osTicket" Now go back into the browser to set up the final database settings make sure your MySQL Database information matches everthing you just put in HeidiSQL

</p>

![Capture](https://github.com/user-attachments/assets/39c72d4d-accb-4f96-8d47-255f6a64eba8)
![Capture](https://github.com/user-attachments/assets/069d1734-cce8-4baf-a289-4769632e3640)
![Capture](https://github.com/user-attachments/assets/4c2c8b40-ebd7-4448-a944-8543f2e7c1fa)

## Step 12 

click install now if done correctly your screen should look just like mine below 

![Capture](https://github.com/user-attachments/assets/57ad569a-ce60-4453-b8e8-8f3c0d17ce2b)

