# Cygwin

# FAQ/Errors

## Your group is currently "mkpasswd"

	Your group is currently "mkpasswd".  This indicates
	that
	the /etc/passwd (and possibly /etc/group) files should
	be rebuilt.
	See the man pages for mkpasswd and mkgroup then, for
	example, run
	mkpasswd -l [-d] > /etc/passwd
	mkgroup  -l [-d] > /etc/group
	Note that the -d switch is necessary for domain users.

From [here](http://www.cygwin.com/ml/cygwin/2005-12/msg00865.html)
	
	mkgroup -l -d > /etc/group
	mkpasswd -l > /etc/passwd
	mkpasswd -u "$USERNAME" -d "$USERDOMAIN" >> /etc/passwd
	
The first 'mkpasswd' creates a passwd file containing local accounts.

The second 'mkpasswd' creates an entry for my domain account and appends it to the passwd file. At least in my case, the group id generated in this step matches the right group entry generated by the call of 'mkgroup'.

In my case, using 'mkpasswd -d "$USERDOMAIN"' would have generated tens of thousands of entries and taken rather a long time so the use of -u was rather important. I also had to specify the domain explicitly, the one that is used if I just use -d is not the domain that contains my account.	