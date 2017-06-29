# vagrant-devbox
Sample configuration for a vagrant devbox on VirtualBox 

Use: Collaborative dev and simulation

# Manifesto 
This configuration is meant to be used by PHP applications and easy to customize.
Required software: Vagrant, VirtualBox and a Git software (I recommend Source Tree)
They can be easily downloaded via Chocolatey.

In this conf, the name of the app is "myapp". 
Its source code is located in C:/Users/Administrator/Documents/myapp/coreapp and the master repository is on gitlab at gitlab.com/myapp/coreapp.git

The IP of the vagrant virtual box is "192.168.50.4".
OS: bento/ubuntu-16.04,  Web server: Nginx
 
# Installation
1. Move "devbox" and "coreapp" to C:/Users/Administrator/Documents/myapp/
2. Open "devbox" and make the following changes:
  - In Vagrantfile and playbooks/vagrant.yaml, replace "myapp" with the actual name of your application on github
  - In devbox/playbooks/roles/{myapp}/tasks/main.yaml, provide the appropriate username and password to clone your app's source code from gitlab (Note that if your password contains special characters you will have to percent-encode them)
  - In playbooks/roles/myapp/templates/.env.j2 update the value of the database global vars DB_DATABASE, DB_USERNAME and DB_PASSWORD
  - Rename playbooks/roles/{myapp}/templates/ to playbooks/roles/{your_app_name_goes_here}/templates/
3. Launch the command line as admin in C:/Users/Administrator/Documents/myapp/devbox/ and run "vagrant up" 
4. Open a browser and go to 192.168.50.4:8082

# Maintenance
If later on, after runnning "vagrant up", you have to bring changes to your local code (C:/Users/Administrator/Documents/myapp/coreapp) and commit them to gitlab, you apply these modifications to the vagrant devbox by launching the command line as admin in C:/Users/Administrator/Documents/myapp/devbox/ and run "vagrant provision" 

# Miscellaneous
You can also work directly on the vagrant virtual box through ssh by launching the command line as admin in C:/Users/Administrator/Documents/myapp/devbox/ and run "vagrant ssh".

Thank me later
