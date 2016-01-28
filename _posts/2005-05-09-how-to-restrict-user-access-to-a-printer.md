---
title: How To Restrict User Access To A Printer
layout: post
---

Two Ways To Restrict User Access To A Printer

  /usr/sbin/lpadmin -p printer -u allow:all 
 /usr/sbin/lpadmin -p printer -u allow:peter,paul,mary 
 /usr/sbin/lpadmin -p printer -u deny:peter,paul,mary 

The second method is similar to the first since it changes the same configuration file. Instead of issuing the lpadmin command, edit the /etc/cups/printers.conf file to add users to the AllowUser and DenyUser directives within a printer definition. Here are two examples:

 # Deny everyone except for users peter, paul and mary
 <Printer my_printer>
 ...
 AllowUser peter
 AllowUser paul
 AllowUser mary
 </Printer>
 
 # Accept everyone except for users peter, paul and mary
 <Printer my_printer>
 ...
 DenyUser  peter
 DenyUser  paul
 DenyUser  mary
 </Printer>
