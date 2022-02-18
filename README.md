# HTML-Upload-File
File Upload with Progress Bar HTML CSS &amp; JavaScript (optional Apache2 Authentication)

![image](https://user-images.githubusercontent.com/23278182/154736693-3c8cf381-fa5d-4979-8697-04482c7c0cf2.png)

<h1>Virtual Host Configuration for Apache Authentication (optional)</h1>
To add basic authentication to an apache2 virtual host you need to add the following lines to the virtual host configuration.<br>

AuthType Basic                                               (1)<br>
AuthName "Private Documentation Repository"                  (2)<br>
AuthUserFile /var/www/upload/.htpasswd-private      (3)<br>
Require valid-user                                           (4)<br>

1 - Set the Basic authentication method<br>
2 - Provide a name for the location (optional)<br>
3 - Specify the pathname to the file that contains usernames and passwords. The usual filename to use is .htpasswd<br>
4 - Specify that only users that exist in the file are allowed access<br>

The AuthUserFile should not be located in a directory served by apache2 since you do not want people to be able to download the contents of this file. This file contains the valid usernames and passwords. Example: Virtual Host Entry

<strong>Apache Virtual Host Example with Autentication File</strong>

<h1>htpasswd file</h1>
The htpasswd file (var/www/upload.htpasswd-private' in the example above) is created and maintained by the `htpasswd program. Use use this program to add or change password entries in the file.

<h3>Creating New Users</h3>
Example: Creating a new entry

$ htpasswd /var/www/upload/.htpasswd-private newuser<br>
New password:<br>
Re-type new password:<br>
This prompts for the password for newuser and stores the encrypted password in the password file.<br>

Example: Created password entry (part of the .htpasswd file)<br>

newuser:Po9FhxMKQJcRY<br>

<h3>Deleting Users</h3>
You delete users from the .htpasswd access file as follows<br>
Example: Deleting user account newuser<br>
$ htpasswd -D .htpasswd newuser
