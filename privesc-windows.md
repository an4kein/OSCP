### First let's find out what OS we are connected to:
systeminfo | findstr /B /C:"OS Name" /C:"OS Version"

### Next we will see what the hostname is of the box and what user we are connected as.
hostname

%username%


### Now we have this basic information we list the other user accounts on the box and view our own user's information in a bit more detail. We can already see that user1 is not part of the localgroup Administrators.
net users

net users user1

### First let's have a look at the available network interfaces and routing table.
ipconfig /all

route print

### arp -A displays the ARP (Address Resolution Protocol) cache table for all available interfaces.
arp -A


### The following two netsh commands are examples of commands that are not universal across OS/SP. The netsh
firewall commands are only available from XP SP2 and upwards

netsh firewall show state

netsh firewall show config

### This will display verbose output for all scheduled tasks, below you can see sample output for a
single task.

schtasks /query /fo LIST /v

### The following command links running processes to started services.

tasklist /SVC

net start

### This can be useful sometimes as some 3rd party drivers, even by reputable companies, contain more holes than Swiss cheese. This is only possible because ring0 exploitation lies outside most peoples expertise.
DRIVERQUERY


wmic qfe get Caption,Description,HotFixID,InstalledOn
