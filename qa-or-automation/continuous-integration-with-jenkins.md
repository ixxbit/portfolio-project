---
description: 'demo with selenium, junit, github'
---

# Continuous Integration with Jenkins

## Continuous Integration with Jenkins \(demo with selenium, junit, github\)

[![Burak Erg&#xF6;ren](https://miro.medium.com/fit/c/96/96/1*bquLb1UUmERiFdgNLyPjOQ.jpeg)](https://medium.com/@burakergoren?source=post_page-----485b53a6cf58----------------------)[Burak Ergören](https://medium.com/@burakergoren?source=post_page-----485b53a6cf58----------------------)Follow[Apr 18, 2018](https://medium.com/@burakergoren/continuous-integration-with-jenkins-demo-with-selenium-junit-github-485b53a6cf58?source=post_page-----485b53a6cf58----------------------) · 4 min read

> **What is CI?**

Continuous integration is the method used to determine that the entire system is in the running state and the changes made have not lead to errors in some parts of the system.

> **What is purpose of CI?**

To ensure that work packages are integrated into the main project successfully while several developers are developing on the same project in different time periods.

> **How CI works?**

![](https://miro.medium.com/max/60/1*Vd3sJvrlAIEzdDqU8Tn1Ew.png?q=20)![](https://miro.medium.com/max/404/1*Vd3sJvrlAIEzdDqU8Tn1Ew.png)

* Well, lets say you are part of a software development team and this team working on a software project
* In this project you are using a version control system. Each developer in your team sends their work packages to VCS when they complete the tasks.
* You have a CI tool running synchronously with this version control system. When a new software package arrives for VCS server, CI server is triggered and fulfills a number of functions that you specify.
* You can build, deliver or deploy the software package, notificate people or you can specify different orders according to your project.

> **What are the benefits of CI?**

* Reduce the risk of integration to minimum level
* Increase code quality. Prevent developing on the faulty code
* For QA teams, having different versions and builds of the developed code makes it easier to follow the bug.
* Significant time is gained during the deployment phase
* Reduce the fear of breaking places in the current market after development. A more focused and energetic work takes place of worry

> **CI Principals**

* Code should be committed frequently
* Incorrect code is never be committed
* Unit test should be written
* Incorrect build should be fixed quickly
* All tests must pass

> **What is Jenkins?**

Jenkins is an open source continuous integration and build automation tool. automation server which can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software.

> **What can be done with Jenkins?**

Jenkins can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software. It can run developed scripts and can archive the results.

## **Jenkins Integration with Github — Demo** <a id="9247"></a>

I wrote sample junit test and push it to github repo. You can find pom.xml and test class below. You can also reach the project from [**here**](https://github.com/burakergoren/jenkinsDemo)

* pom.xml →
* Test class →
* Now we can start to set up jenkins server

> **Step1 - Jenkins Installation and Set Up**

* Download Jenkins from ****[**here**](https://jenkins.io/download/)
* Run downloaded package and start installing jenkins
* In the below step, you should go to specified path to get written special password to unlock Jenkins.

![](https://miro.medium.com/max/60/1*0oMr8U5HMzkvTb1I7OiU_A.png?q=20)![](https://miro.medium.com/max/2468/1*0oMr8U5HMzkvTb1I7OiU_A.png)

* You can get the code as typing;

```text
sudo cat /Users/Shared/Jenkins/secrets/initialAdminPassword
```

* Copy and paste the code to Admin password textbox area and continue
* Install suggested plugins and create admin user.
* That’s all. Now you can start using jenkins! Login by the created admin user.

![](https://miro.medium.com/max/60/1*cuvzn-2_7Yk9CI7KTIW-Lw.png?q=20)![](https://miro.medium.com/max/2470/1*cuvzn-2_7Yk9CI7KTIW-Lw.png)

* You can specify new IP address. As default, jenkins server is running on [http://localhost:8080/](http://localhost:8080/)

> **Step 2 - Tool Configuration: Specify maven installation**

* I presume that maven is already installed. Check maven version \(ex; 3.3.9\) from command prompt as typing;

```text
mvn --version 
```

* Then, open jenkins server and go respectively;

```text
Manage Jenkins > Global Tool Configuration > Add Maven
```

* Select installed maven version on your pc, give a name and save.

![](https://miro.medium.com/max/60/1*MUuuQOkEDnok1Mb4qgvVDA.png?q=20)![](https://miro.medium.com/max/1970/1*MUuuQOkEDnok1Mb4qgvVDA.png)

> **Step 3 - Create new job and integrate with github**

* On jenkins dashboard click New Item &gt;Freestyle Project and name the project
* Job configuration page will be opened
* In the Source Code Management section, select Git
* For repository url; enter project url on github like

```text
https://github.com/burakergoren/jenkinsDemo.git
```

* Secondly, add credential for this github account \(username and password for github account\)

> **Step 4 - Select Build Trigger option**

* Go “Build Triggers” section
* Check Poll Scm and enter five stars with spaces \(\* \* \* \* \* \)
* It means “every minute” for [cron time](http://www.nncron.ru/help/EN/working/cron-format.htm) process. So our jenkins server will check github every minute, if there is any change in the repo it will trigger the job and tests will start. You can set trigger time however you want using cron time.

> **Step 5 - Select Build Option**

* Go “Build” section
* Click “Add Build Step” button
* Select “Invoke top-level maven targets”
* For maven field, select specified maven version before
* For goals field, enter mvn commands to run junit tests.

```text
clean
install
-Dtest=JenkinsDemo
-Dwebdriver.chrome.driver=/opt/chromedriver
```

![](https://miro.medium.com/max/60/1*qCiUM7H33E04b0aUc9_xRA.png?q=20)![](https://miro.medium.com/max/1890/1*qCiUM7H33E04b0aUc9_xRA.png)

**Thats all ! It is ready to go**

Now, our github integrated CI server is ready. You can start job manually from jenkins or you can push any commit to the repo that you specified in the project and jenkins starts the job instead of you.

Hope you like this story

Refs:

[https://www.tutorialspoint.com/jenkins/index.htm](https://www.tutorialspoint.com/jenkins/index.htm)

[http://www.bugrayuksel.com/tag/ci-nedir/](http://www.bugrayuksel.com/tag/ci-nedir/)

[https://jenkins.io/](https://jenkins.io/)

