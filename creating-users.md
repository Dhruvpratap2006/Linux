Now for creting user we can write the commands

sudo adduser "Account Name"
<!-- then it will ask the your root account password -> type it and enter
then set new account password -->

Now to go from root account to new account type 
su - NewAccountName

to exit from current account type exit

<!-- now imp info -->
Only root user has complete excess of the machine new user can do things but do not have full excess like root user 
for ex if we write with new acount sudo apt update then this will not executes 

but if we want we can gave complete excess and it will have all powers like root user

sudo usermod -aG sudo AccountName

now re-login to new account su - AccouintName
now type it will update

to take all rights back from new Account write
sudo deluser newAccountname sudo