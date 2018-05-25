# jenkins-tutorial

## Install Jenkins

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

## Create a simple build job.

Click on `New Item`

Enter `simple-build` as the job name and select `Freestyle project`.

Under `Source Code Management` tab:
- Select Git and 
   - for `Repositories -> Repository URL` enter `https://github.com/kurianinc/docker-java-sample.git`
   - for `Branches to build -> Branch Specifier` replace `master` with name of your branch you created during Git tutorial.

Under `Build Triggers` tab:
- Check `Poll SCM` and in the `Schedule` field enter  `* * * * *`. This means Jenkins is scheduled to poll the Git repo/branch every minute for a changes. If there would be any change Jenkins will kick off a build.

Under `Build` tab:
- `Add build step` -> `Execute shell` and in the `Command` field enter:
```
mvn package
mvn exec:java
```

`Save` the job. In a minute you will see that Jenkins would trigger a build. You can also kick off a build manually by clicking on the `Build Now` link.

Check in changes to `docker-java-sample` repo, as you have learned in the Git tutorial, and verify that Jenkins picks that up and builds.

