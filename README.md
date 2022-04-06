# ansible-cron-play
This is a repo for a simple ansible playbook to execute a cron job to delete the files older than 1 hour by default

## description
This playbook will simply execute a cronjob on the client machine which can be variablised as needed w.r.t to time and user.

 Tested on Linux(Ubuntu) with multple user.

## Variables to be passed
* time = the time interval for deleting the older jobs | default value: 60mins/1hour
* user = configurable user variables to be passed while execution | default value: ubuntu 
* cronUser = The user to be configured for executing the cron job | default value: execution user. The user must be super user to use this feature.

## How to execute
The execution is very simple, a single command calling the ansible playbook play.yml

* ansibile-playbook play.yml -e "user= <<"playbook execution user">> time=<<"Time interval in minutes">> cronUser=<<"execution user for crontab">>"
    * Example: ansible-playbook play.yml -e "user=root time=5 cronUser=ubuntu"
* ansible-playbook play.yml
    * the above command will execute with the defail values.

## How does the output look?
Once the playbook is executed, you will notice the ansible execution output as below,

![alt text](https://github.com/bsk1072/ansible-cron-play/blob/main/outputimages/ansioutput.JPG?raw=true)

The cron output looks similar to this,

![alt text](https://github.com/bsk1072/ansible-cron-play/blob/main/outputimages/cronExecution.JPG?raw=true)

## Alternate Solution
The alternate solution would be to using the ansible-tower with a schedules jobs.