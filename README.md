# jenkins-tutorial

Install Jenkins on the AWS EC2 Amazon Linux instance, as root.
```
$ sudo -i
# wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
# rpm --import http://pkg.jenkins-ci.org/redhat-stable/jenkins-ci.org.key
# yum install jenkins
# service jenkins start
# chkconfig jenkins on
```
Access Jenkins UI on the browser at `http://IP-ADDRESS:8080`. When prompted for the password, get that from following file on the EC2 host:
```
$ cat /var/lib/jenkins/secrets/initialAdminPassword
```

Create a new admin user after logged in to Jenkins.

