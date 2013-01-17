ansible-scripts
===============

scripts for ansible.

the scripts are tested under these distributions:

+ CentOS
+ Debian
+ Ubuntu



tips
===============
use virtualenv and virtualenvwrapper to manage the packages:

	$ git clone git@github.com:jhezjkp/ansible-scripts.git
	$ cd ansible-scripts
	$ pip install virtualenv virtualenvwrapper
	$ mkvirtualenv ansible-scripts
	$ pip install -r requirements.txt


run the commands below to set the environment and the reactive the virtualenv:

	$ echo "export ANSIBLE_HOSTS=~/.ansible_hosts" >> ~/.virtualenvs/ansible-scripts/bin/postactivate
	$ deactivate
	$ workon ansible-scripts
	
execute the script on local machine:

	$ ansible-playbook misc.yml --extra-vars "hosts=all user=vagrant" --connection=local
	
__note__:

it seems there will be something wrong with the ansible module if you install ansible under an virtualenv….. so, install ansible normally at present time until it solve this problem.
