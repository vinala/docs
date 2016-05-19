# Setup

[![alt return](https://raw.githubusercontent.com/fiesta-framework/Art/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.2/#index)

- [Brief](#brief)
- [General](#general)
- [Database](#database)
- [Security](#security)
- [Panel](#panel)

### Brief

After completing installation of the framework, pikia propose to you an assistant to configure it step by step, you should just fill the fields with the appropriate information, all information you give will be set in `/config` files, any info you set can be edited later in same files (in config folder), also you can skip the configuration. when you finish the configuration, the **configured** parameter in `/config/panel.php` will be true.

### General
![alt tag](https://raw.githubusercontent.com/fiesta-framework/Docs/3.2/rsrc/setup/general.png)

In the first step you will have to set general configuration related to application, transalator, debugging and maintenance. First you set your name, and choose a language to set it as default language, sure you can edit it after.
The debugging switch set true in `debug` in `/config/loggin.php` file, it makes your application in production mode, it means if its false, when you have bug in your application it will never show the error message it just show simple page with simple message defined in config paramter `msg` in same connfig file else (if true) it will show detailed page shows the error by using [Whoops](https://github.com/filp/whoops).
The maintenance switch is same as The debugging switch but it will make all http routes shows a message set in `msg` in `/config/maintenance.php`b the switch will set true in `activate` in same file.
### Database
![alt tag](https://raw.githubusercontent.com/fiesta-framework/Docs/3.2/rsrc/setup/database.png)
### Security
![alt tag](https://raw.githubusercontent.com/fiesta-framework/Docs/3.2/rsrc/setup/security.png)
### Panel
![alt tag](https://raw.githubusercontent.com/fiesta-framework/Docs/3.2/rsrc/setup/panel.png)