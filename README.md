# Hibernate-Switcher
A simple automator app made to switch the hibernate mode from default to 25 or back to default.</br>
This app simply serves one purpose, to make it easier for the end user to change the hibernate settings on their Mac.</br>
# Hibernate Modes</br>
3 or Default, is pretty simple. It places your MacBook in a mode where the RAM is still powered while the system goes to sleep</br>
this uses more battery life than hibernate 25, the hidden hibernate mode. This mode uses even less power by shutting off the RAM</br>
in hibernate 25 your RAM is coppied to your hard drive or SSD. This takes longer to wake from but uses less power as the system</br>
soon shuts off power to your RAM until it's time to wake up. Upon wake up all of your files are restored to RAM. The only draw back</br>
is that your computer ports are also powered off in this mode.</br>
</br>
# Note:</br>
Since this app is made from Apple & Shell scripts using Automator there's no real source code to compile yourself.</br>
If you really want to poke at the internals and possibly make a better version the scripts are stored in document.wflow</br>
along with all the other things the automator app needed to create it.</br>
</br>
# Code:</br>
```
#Bash script included with program:
cd /Applications
mkdir HibernateSwitcher
cat &gt; /Applications/HibernateSwitcher/Hibernate25.command &lt;&lt; EOT
#!/bin/bash
sudo pmset -a hibernatemode 25

EOT

cat &gt; /Applications/HibernateSwitcher/Hibernate3.command &lt;&lt; EOT
#!/bin/bash
sudo pmset -a hibernatemode 3

EOT

cd /Applications/HibernateSwitcher
chmod a+x Hibernate25.command &amp;&amp; chmod a+x Hibernate3.command
cd /
# Generate Readme
cat &gt; /Applications/HibernateSwitcher/Readme.txt &lt;&lt; EOT
These scripts are needed to run Hibernate Switcher. They will automatically regenerate every time you run the app.

EOT

Applescript:

set question to display dialog "Which hibernate do you want to set?" buttons {"Default", "25", "Cancel"} default button 2
set answer to button returned of question

if answer is equal to "Default" then
	do shell script "/Applications/HibernateSwitcher/Hibernate3.command" with administrator privileges
end if

if answer is equal to "25" then
	do shell script "/Applications/HibernateSwitcher/Hibernate25.command" with administrator privileges
end if

if answer is equal to "Cancel" then
end if
```
</br
```set question to display dialog "Which hibernate do you want to set?" buttons {"Default", "25", "Cancel"} default button 2
set answer to button returned of question

if answer is equal to "Default" then
	do shell script "/Applications/HibernateSwitcher/Hibernate3.command" with administrator privileges
end if

if answer is equal to "25" then
	do shell script "/Applications/HibernateSwitcher/Hibernate25.command" with administrator privileges
end if

if answer is equal to "Cancel" then
end if
```
</br
# License</br>
This is free and unencumbered software released into the public domain.</br>
</br>
Anyone is free to copy, modify, publish, use, compile, sell, or</br>
distribute this software, either in source code form or as a compiled</br>
binary, for any purpose, commercial or non-commercial, and by any</br>
means.</br>
</br>
In jurisdictions that recognize copyright laws, the author or authors</br>
of this software dedicate any and all copyright interest in the</br>
software to the public domain. We make this dedication for the benefit</br>
of the public at large and to the detriment of our heirs and</br>
successors. We intend this dedication to be an overt act of</br>
relinquishment in perpetuity of all present and future rights to this</br>
software under copyright law.</br>
</br>
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,</br>
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF</br>
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.</br>
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR</br>
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,</br>
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR</br>
OTHER DEALINGS IN THE SOFTWARE.</br>
</br>
For more information, please refer to <http://unlicense.org/>
