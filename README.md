1. install vagrant ~> 1.8.4
	- download from https://www.vagrantup.com

2. install virtualbox ~> 5.0.20 r106931
	- download from https://www.virtualbox.org/wiki/Downloads

3. install the chef development kit ~> 0.15.15
	- download installer from https://downloads.chef.io/chef-dk/

4. install vagrant-berkshelf by running the command below in your terminal
	- vagrant plugin install vagrant-berkshelf

5. clone the repository (or simply go to the url below and download the zip and extract it wherever you want vagrant to run from)
	- git clone https://github.com/stretchnate/lms_vagrant.git

6. cd lms (or cd <whatever you named the folder you unzipped/cloned>)

7. Ensure you have the lms svn repository checked out/cloned
NOTE: if you choose a different location for your code repository in step 7 you will need to change the location in Vagrantfile for config.vm.synced folder for '/opt/local/apache2/htdocs' to the location you used.
Likewise, you will need to adjust the symlink in step 8 to fit your location

8. Ensure that you have a symlink from /opt/local/apache2/htdocs/library to /opt/local/apache2/htdocs/lms/library, if you don't have the symlink run the below command.
	- ln -s /opt/local/apache2/htdocs/library /opt/local/apache2/htdocs/lms/library

9. from within the lms directory (recenly cloned git repo) run
	- vagrant up

This should install CentOS 7.1 on a new virtualbox environment, install Apache and php on that vbox, sync your local codebase to the vbox environment and configure apache and php.
Once finished you should be able to open a browser and hit either http://glms:8080, http://clms:8080 or http://gams:8080

NOTE: at some point I anticipate forwarding port 80 from the host to the guest machine, when that time comes you'll no longer need to specify a port in the browser. I will update this document when that time comes.

If you run into any apache or php config issue please let me know so i can update the fix to the chef cookbooks in order to keep this process completly automated.