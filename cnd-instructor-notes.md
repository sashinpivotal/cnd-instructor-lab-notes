# What is this instructor-note for?

This is a collection of "tips and tricks" I've collected
in teaching PAL CND, which includes

- Additional logistics info that might be useful to the
  the students before/during/after the cohort
- Tips and tricks used by other instructors
- Talking points/Wrap-up points for each topic
- Challenge questions/exercises for each topic
- Additional reference materials
- Trouble-shooting tips


# Getting started (logistics)

## Slack

- We now create Slack channel first and then invite students
  manually

## Course contents access

- Some students did not receive confirmation email
  after they signed up because company firewall blocks the email?
  (Josh can manually confirm on our end through Auth0)

- One Fedex case - somehow Fedex VPN blocks the sign-up

  ```
  Josh, I figured it out. I was on Fedex VPN which was preventing the signup. I tried on my personal laptop and it worked. I’m all good now.

  Regards,
  Dhatri V.
  ```


## Misc.

  ```
  @here Do not worry about your pair setting up a github today.
  we will deal with that tomorrow before we do a pair rotation
  ```

  ```
  @here please make sure you are pairing effectively.
  The easiest way is to use a timebox where you switch
  driving every 20  minutes.
  if you are interested in more pairing information:
  https://stackify.com/pair-programming-styles/
  ```

# Git related

## Normal flow of work in the lab

```
(Save your current changes to a branch)
-   git checkout -b wip-branch
-   git add .
-   git commit -m "work in progress in my REST lab"
-   git push origin wip-branch
-   git checkout main

(Fast-forward to mvc-solution)
-   git cherry-pick mvc-solution 
```

```
git cherry-pick <xyzlab-start>  (pull in the test code in most labs)
(do your lab work)
git add -p  (add any new code to be in the git version control)
git commit -m "done with xyzlab" (commit the change)
git push    (push the local change to the remote repo, which also triggers GitHub Action)
```

## Save "in progress" work in a personal branch

```
If you need to save your current unfinished work into
“work in progress” branch and then start with next
module, please do the following:

-   git checkout -b wip-branch
-   git add .
-   git commit -m “work in progress in my lab”
-   git push origin wip-branch --tags
-   git checkout main
-   git cherry-pick jdbc-solution
```

## Start with "topic-start" for a new lab

```
If you want to start "topic" lab from "topic-start",
follow the steps mentioned below

-   git checkout main (if you are not in main branch)
-   git reset --hard <topic-start>
-   (change manifest files to reflect correct domain and route in manifest file like:)
        - route: pal-tracker-sang-shin.apps.evans.pal.pivotal.io
-   (Do the lab work)
-   git add-commit -m “my work done”
-   git push origin main -f  (to force the remote main to sync with local main - do not to this in production! :-))
```

-   If you have created github repository with `README.md`, you
    will experience the following problem when you do
    `git push origin main --tags`.
    An easy way out is `git push origin main -f --tags`
    (Or ask students to delete/recreate the repository
    without creating README.md file)

```
< workspace/movie-fun - main > git push
To https://github.com/sashinpivotal/movie-fun
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/sashinpivotal/movie-fun'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

- *When a repository is created with README file on, performing
  `git pull` results in the following error:

  ```
  < workspace/pal-tracker-distributed - main > git pull
  fatal: refusing to merge unrelated histories
  ```
  
  You can do the following to move forward. 
  (Or ask students to delete/recreate pal-tracker repo)
  

  ```
  git pull --allow-unrelated-histories
  ```

-   Bill's suggestion on letting students to start with a new module

```
# Fast Forwarding to Solution
## Create a work-in-progress branch for your lab
git status # view your changes
git add <you changes>
git checkout wip-<lab>
git commit -m'<some commit message>'
git push origin wip-<lab> # if you want to save it in your remote
git checkout main
## fast forward to solution
### if you don't know solution tag find it after your start tag
### via `git lola`.
git cherry-pick <lab solution tag>
### merge any conflicts, stage, and `git cherry-pick --continue`
git push origin main
```

# Pair Programming (Not relevant for LOL)---

- Communicate what you do to your partner - if you are typing or
  moving your mouse without talking, you are doing a disservice
  to your pair partner
- Use your mouse rather than using your finger

## Pair rotation

(Not relevant for LOL)

- Before the rotation, please do ensure both pairs
  have code on their own github

- Mention this after `pal-tracker` lab and just before
  `pal-tracker-distributed` (This is what Brad sent out)

```
@here This morning before we rotate pairs:
1. The other pair partner should create a Github repository for `pal-tracker`
2. git remote add other-origin <github repo url>
3. git push --tags -f  -u other-origin main
4. git remote remove other-origin
```

- Sarah used post-it tag to designate a `driver` of the pair
  (owner of GitHub and PAS account)

- My scheme - to make sure non-driver become a driver
  - everyone moves to the right by one position
  - non-driver in the pal-tracker will be become a driver

- Use the following message on slack for pair rotation

```
Pair rotation guide:
- Before the rotation, please ensure that both members of the pair
  save the code to the Github repository
- Log out from PCF, Slack, Github
- Once everyone is ready, everyone moves to the right by one seat.
  The rightmost person of the table goes to leftmost seat of
  the table behind. (This is to make sure non-driver in the
  previous lab play the role of the driver)
- Once sitting is complete, use the driver's (the machine with
  the red post-it) credentials of the following:
    - Slack
    - PCF (PAS)
    - GitHub
    - Assignment Submission
```

# Pairing reference material

```
On topic of remote pairing (Ray brought up Monday AM), this is a nice read, tool, and approach of one of aspects of remote pairing: https://erictsiliacos.medium.com/remote-pairing-with-portal-ba107fcb824f
```

[git-duet](https://github.com/git-duet/git-duet)

# VDI ---------------------------

## Linux keyboard shortcuts within the VDI

- Keyboard shortcut keys within VDI/Remote Desktop

  - SHIFT+CTRL+C (copying from the termimal).  <-------
  - SHIFT+CTRL+V (copying to the terminal) <-------
  - CTRL+C (copying from non-terminal app)
  - CTRL+V (pasting into non-termal app)
  - ALT+Tab (move between windows)
  - CTRL+ALT+D (minimize all windows)
  - ALT+F10 (maximizing window on and off)
  - ALT+F9 (minimize window)

- Keyboard shortcut keys within the VDI-provided IntelliJ

  - CTRL+N (find class)
  - CTRL+Shift+N (find file)
  - ALT+Return (Quick fix)
  - Double SHIFT (global search)

  - F2, SHIFT+F2 (Go to next/previous error)
  - CTRL+SHIFT+F12 (maximize editor window)
  - CTRL+SHIFT+Return (Complete current statement)
  - CTRL+SHIFT+F10 (run the app/test)
  - SHIFT+F10(rerun the app/test)
  - CTRL+SHIFT+F12 (Maximize editor window)
  - CTRL+ALT+V (extract return value into a local variable)
  - CTRL+SHIFT+T (go to target/test code)
  - CTRL+ALT+Left (back - might not work on Mac: 
                   you might have to set it yourself manually)
  - CTRL+ALT+Right (forward - might not work on Mac:
                   you might have to set it yourself manually)
  - ALT+Insert (Generate - might not work on Mac:
                you might have to set it yourself manually) 
  - CTRL+SHIFT+' (Maximize/minimize tool window: 
                you might have to set it yourself manually) 
                
- If VDI does not respond to your keyboard stroke, 
  please try ALT+Tab or ALT+Enter to unlock it

## Native keyboard shortcut keys

- Keyboard shortcut keys for IntelliJ (Mac)

```
  - CMD+O (find class)
  - CMD+SHIF+O (find file)
  - ALT+Return (Quick fix)
  - Double SHIFT (global search)
  - CMD+SHIFT+Return (Complete current statement)
  - CMD+SHIFT+F12 (maximize/minimize editor window)
  - CMD+SHIFT+' (Maximize/minimize tool window)
  - F2, SHIFT+F2 (Go to next/previous error)
  - CTRL+SHIFT+R (run the app/test)
  - CTRL+R(rerun the app/test)
  - CMD+ALT+V (extract return value into a local variable)
  - CMD+SHIFT+T (go to target/test code)
  - CMD+Left (navigate back)
  - CMD+Right (navigate forward)
  - CMD+N (Generate)
  
```

## Misc. tips

- If you are using Firefox, you can bookmark the course
  webpage by right clicking ...
  on the top-right corner and select bookmark
  and save it under "Bookmars toolbar"


- *If you enabled two-factor authentication, you will experience
  the following. Easiest fix is to disable it.  (See "Pair
  programming document" for other suggestions.)

  ```
  pal_user@instructor-demo-sang-large:~/workspace/pal-tracker- distributed$ git push origin main -f
  Username for 'https://github.com': sashinpivotal
  Password for 'https://sashinpivotal@github.com':
  remote: Invalid username or password.
  fatal: Authentication failed for 'https://github.com/sashinpivotal/ pal-tracker-distributed/'
  ```

  It is because as mentioned [here](https://stackoverflow.com/questions/17659206/git-push-results-in-authentication-failed)

  ```
  If you enabled two-factor authentication in your Github account you  won't be able to push via HTTPS using your accounts password. Instead  you need to generate a personal access token. This can be done in the  application settings of your Github account. Using this token as your  password should allow you to push to your remote repository via  HTTPS. Use your username as usual.
  ```
  
- [How to create and use GitHub personal access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)
  - For scope selection, choose repo and workflow


- In the VDI provided Firefox browser, you can bookmark
  it but you have
  to select "show bookmark bar" to see it

## Lab related

- Getting actuator metrics from the VDI provided Chrome
  browser is not formatted
  But using curl command with json_pp works.
  Also Firefox does the formatting automatically.

## ubuntu

- vim or nano are already there as an editor
- Visual Studio is another option
- bash shell - you can check with echo "$SHELL"
- you have to create ~/.bash_profile


# Assignment Submission --------------------

## Talking points

- Note that whenever student submit the lab result,
  they always have to go to the `assigment-submission` directory

- Make sure to change the email address

- CND students should ignore `waveland` section

- Even though Charles said not to do "copying and pasting",
  in this lab, it is OK to copy the contents of build
  script and paste it.

## Challenge questions

- What the purpose of using "gradle wrapper"?

# Building a Spring Boot App (lab #1) -------


https://spring.io/guides
https://www.baeldung.com/start-here

## Talking points
	
- lab project
    - Typically you are going to create Spring Boot project
      from Spring initializr such as start.spring.io.
      But here you are going to create the project from
      scratch 
      - You are going to create build script 
      - You are going to create directory structure as well
    
- We provide starting codebase
           
	 - Mention that the `pal-tracker` directory is 

	   under `workspace` directory

	 - You are going to create `pal-tracker` repository
	   in your Github
	   and sync up with local `pal-tracker` project
	   using `git remote add origin <URL>`

- PCF related
	- You are going to deploy the app to the PCF manually
	  in this lab
	  using `cf push` command:
	  later on, you will
	  deploy the app using a CI/CD pipeline.

## How to set up `pal-tracker` Git project

- Create personal Github account if you have not done so yet

- Steps to follow
  - Create a personal GitHub account (if you don't have one yet)
  - Create "pal-tracker" repository
  - Make sure you have unzipped the `pal-tracker.zip`
    under `workspace` directory
  - Go to local `workspace/pal-tracker` directory
  - Execute `git remote add origin <url>`
  - Execute `git push origin main --tags`

## GitHub  

- *If you enabled two-factor authentication, you will experience
  the following. 

  ```
  pal_user@instructor-demo-sang-large:~/workspace/pal-tracker- distributed$ git push origin main -f
  Username for 'https://github.com': sashinpivotal
  Password for 'https://sashinpivotal@github.com': 
  remote: Invalid username or password.
  fatal: Authentication failed for 'https://github.com/sashinpivotal/ pal-tracker-distributed/'
  ```
  
  It is because as mentioned [here](https://stackoverflow.com/questions/17659206/git-push-results-in-authentication-failed)
  
  ```
  If you enabled two-factor authentication in your Github account you won't be able to push via HTTPS using your accounts password. Instead  you need to generate a personal access token. This can be done in the  application settings of your Github account. Using this token as your  password should allow you to push to your remote repository via  HTTPS. Use your username as usual.
  1. Go to your profile -> Settings-> Developer Settings -> Personal Access Token -> Select repo+workflow
  2. When you do perform "git push origin main", use personal access token instead of password
  ```
  
- [Protocols to choose from when cloning:](https://gist.github.com/grawity/4392747)  
  

## Misc

- *What is `buildscript` closure for?

  ```
  The buildScript block determines which plugins, task classes, and
  other classes are available for use in the rest of the build script.
  Without a buildScript block, you can use everything that ships with
  Gradle out-of-the-box.

  If you additionally want to use third-party plugins, task classes,
  or other classes (in the build script!), you have to specify the
  corresponding dependencies in the buildScript block.
  ```

- ??Why do we have the following in both buildscript
  section and regular section of the build.gradle?

  ```groovy
  repositories {
    mavenCentral()
  }
  ```

- *In step 10, if `create package` option is not available, it
  is because the Gradle project was not refreshed (as mentioned
  in step 8)

## Deploy

-  *Somehow, I get the following error when deploying to the PCF:
  it was because I pushed a wrong jar (gradle-wrapper.jar)

  ```
  None of the buildpacks detected a compatible application
  ```

## Tips

- It display the tags in the reverse order of the check-in

```
git config --global alias.lola "log --graph --decorate --pretty=oneline --abbrev-commit --all"
git lola
```

- In Linux, you can use the following command to find jar files

```
find . -name \*.jar -print
```

## Challenge questions of "Building a Spring Boot App" lab

(Spring Boot related)
- What is purpose of doing "./gradle wrapper"?
- What are the main features of Spring Boot?
- What is a fat jar?  What does it include? How does Spring Boot create one?
- How does Spring Boot helps with dependency management?
- What does `@SpringBootApplication` do?

(Spring related)
- What is Dependency Injection? Why is it useful?
- What is an Application context?
- When do you use @Component annotation?
- When do you use @Autowired annotation?

(Cloud native development)
- What is 12 factor app?  (Google it)
- One of the features of Spring Boot (actually through
  the Spring Boot Maven/Gradle plugin) is to create a fat jar
  that contains everything including Tomcat.
  Among the 12 factors, which factor is relevant to
  creating and deploying the same fat jar over different
  deployment environment?

(PCF related)
- Why do we use "--random-route" in our lab? What happens if you forget it?
- Why do we use "--no-start"?  What happens if you forget it?
- Try the following cf command

```
cf target
cf domains
cf apps
cf app pal-tracker
cf routes
cf help -a | grep delete (to get the list of all commands that contains "delete")
```

## Challenge question answers

- Spring boot features include
  - auto-configuration
  - dependency management via starter
  - embedded tomcat
  - fat jar
  - new testing features

## Challenge exercise

-  Create a Person bean which has name and age fields
-  Create CommandLineRunner that displays the name and age
   of the person when application gets started

## Wrap-up (Sang)

-  Go over build.gradle
-  Go over PalApplication.java
-  Go over WelcomeController.java

-  *What is `io.spring.dependency-management` plugin for?
   It is A Gradle plugin that provides Maven-like dependency management functionality
   https://plugins.gradle.org/plugin/io.spring.dependency-management


# Presentation ---------------

## Student questions

- ??What is PKG for?
  - (Bill) PKG deprecated, replaced by TKG
  - It is K8s platform but does not provide cf experience

- *"Firewall/Load-balancer" vs "cf push/cf scale"

What the slide is trying to say is that in the old days where bare metal (or VM-based) app server is added/removed for scalability or whatever reason, the firewall/load-balancer has to be manually reconfigured while in the PaaS like PCF, there is no manual configuration needed for dynamically added/destroyed app instances.

However, PCF does not prevent organizations from using firewall/load-balancer along with PCF - in fact in a reasonably good size deployment site of PCF foundations, usage of firewall/load-balancer is common. But they are deployed in relation to the PCF foundations not related to app instances.

- *Is environment variable values are part of droplet?


# Configuring an App ------------

## Talking points (Bill K)

(Bill)
- what is the definition of configuration?

- Bill used the learning outcomes as talking point guideline
- What is the problem of the previous codebase where we
  are returning hard-coded string?
- Here we are talking about 'configuration' - external to the code
- We mean "external configuration" here (as opposed to internal configration
  inside spring app like configurating spring beans)
- Bill asked <company-name> how they separate external configuration
  such as database configuration?
  - vault server, spring cloud config server, cf set-env
  - ford is using config server
  - config server is useful but it there is tradeoff and understanging
    these tradeoff is important
- Bill asked how environment variables work in modern apps?
- In cloud native application, we use enviroment variables
- Bill talked about motivation of 12 factors by Heroku
  - run applications in on any cloud environment
- In pal-tracker app, we can externalize the value of the message

- Mention that you have to move to pal-tracker directory
- Talk about "git cherry-pick", we give failing tests

```
https://www.atlassian.com/git/tutorials/cherry-pick
- git cherry-pick is a powerful command that enables arbitrary Git commits to be picked by reference and appended to the current working HEAD. 
- Cherry picking is the act of picking a commit from a branch and applying it to another. git cherry-pick can be useful for undoing changes. For example, say a commit is accidently made to the wrong branch. You can switch to the correct branch and cherry-pick the commit to where it should belong.
```

- This is the first lab we give failing tests
- manifest is a declarative way of deploying an application on PCF

## Challenge questions of "Configuring an App" lab
(Please do these challenge questions after you do the "Extra" part of the lab)

(PCF related)
- Do we have to do “cf restage pal-tracker” when we set a
  new environment variable WELCOME_MESSAGE in PCF? Or
  Or would "cf restart pal-tracker" be sufficient?
- What could be other use cases where you will have to do
  “cf restage” (as opposed to “cf restart”) other than
  changing JBP_* environment variables?
- (Related question to the above) What are the differences
  among 3 different ways of deploying an application
  on PCF - "pushing", "restaging", and "restarting"?
- What are the environment variables that PCF automatically
  create for your application instance?
- What are the examples of PCF log types? (Google “PCF log types”)
- Try to use “create-app-manifest” command to capture
  the metadata of your running app into a file and try
  to use that file to deploy the pal-tracker application again
- If you remove "WELCOME_MESSAGE: Hello from Cloud Foundry" 
  from your manifest.yml file and then do "cf push" again, will 
  the application work correctly or will it fail because
  welcome.message was not set?
  What happens if you delete the pal-tracker application by
  "cf delete pal-tracker" first and then "cf push" again?
  
(Configuration related)
- One of the most common configuration values you need to set
  is database configuration.  For example, you might want
  to use different database configuration for different
  environments such as development, staging, and production.
  Now among the multiple choices you have below, which
  one would you choose and why?
  - Using @Profile with @Configuration to create different 
    DataSource beans
  - Using Spring Boot application property files such as 
    application_dev.properties, application_staging.properties 
    to set the different values for the "spring.datasource.url"
    property
  - Use environment variables - Feed different values to
    SPRING_DATASOURCE_URL environment variables
  
## Challenge exercises

- Currently we have testing code for `WelcomeController` that does
  the testing of the controller class logic but it does not test
  Mvc layer, which is covered by API testing using `@SpringBootTest`.
  But one trade-off of using `@SpringBootTest` is that it is
  slower than Web slice testing because it has to start
  the server.  So you might want to write controller testing code
  using `@WebMvcTest` and `MockMvc`.

- Find out how you can use IntelliJ version control window to
  compare your local code against a branch or a tag.

- Create a WelcomeService that returns a message, WelcomeController
  depends on the HelloService to get that message, Use Mockito in your
  WebControllerMockMvcTest code to mock the service, Write the
  WelcomeServiceTest code to test WelcomeService.

## Reference materials regarding configuration

(12 factors related Reference materials)

- Two factor app
  https://12factor.net/

- Great (concise yet to the point) presentation on 12 factors:  
  https://content.pivotal.io/slides/the-12-factors-for-building-cloud-native-software

- Beyond 12 factoor app
  https://www.cdta.org/sites/default/files/awards/beyond_the_12-factor_app_pivotal.pdf

(Configuration related reference materials)

- Configuration Drift
  http://kief.com/configuration-drift.html

- SnowflakeServer from Martin Fowler
  https://martinfowler.com/bliki/SnowflakeServer.html


```
(Spring related reference materials)

- Spring Boot external configuration
  https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-external-config

- Spring Boot relaxed binding
  https://spring.io/blog/2018/03/28/property-binding-in-spring-boot-2-0

Spring resources
https://spring.io/guides
https://www.baeldung.com/start-here
```

```
Container vs VMs. What's the difference?
https://www.youtube.com/watch?v=cjXI-yxqGTI&t=23s&ab_channel=IBMCloud
```

```
PCF app manifest attrubute reference
https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html
```


## Trouble-shootings

- Some people experience [refusing to allow an OAuth Appl to create or update workflow…without ‘workflow’ scope](https://stackoverflow.com/questions/64059610/how-to-resolve-refusing-to-allow-an-oauth-app-to-create-or-update-workflow-on)

- *The document does not include instruction to remove compile
  errors on `EnvController` before it says to run the app
  (Actually bootRun just compiles src/main/java and does not
  care compile errors in the src/main/test)

- *The following code will fail because Spring looks for
  a bean that is a type of String but it is not there.

```
(Spring coding related)
Some of you use the @Value annotation on a field like
following and experienced an exception.
What is the problem of this code?

  @RestController
  public class WelcomeController {

    @Value("${welcome.message}")
    private String welcomeMessage;

    public WelcomeController(
             String welcomeMessage
    ) {
        this.welcomeMessage = welcomeMessage;
    }

    @GetMapping("/")
    public String sayHello() {
        return welcomeMessage;
    }
  }
```

- *You will not be able to run the application within the
  IDE, instead, you will have to run it via `bootRun` Gradle
  task in order to pick up enviroment variable settings.

- *One student gets 404 when accessing localhost:8080/env
  even though the code is correct.
  He had to "./gradlew clean bootrun" (instead of ./gradlew bootRun"
  to fix it.

## Misc

- *Is there a way to set environment variables to an application
  through App manager?
  Yes, there is. Click "Settings" link on the left in the application
  page.

## Wrap-up

- We covered several factors so far. What are those?
  - factor 1 - one codebase many deploys
  - factor 2 - explicit declaration of dependencies using Gradle build file
  - factor 3 - use environment variables for providing different
               property values for different environments
  - factor 10 - dev/production parity - creating a fat jar
  - factor 11 - logs

## Wrap-up (Bill)

- @Profile was introduced in the early version of Spring
    for providing different configuration for different deployment environment
  - In his experience, there was code for production only and
    it was not tested and deployed to production, which caused a problem
    when he was using @Profile
- In cloud native development, Enviromnet specific properties
  should not be in the application.properties inside the jar file
  Instead, they should be provided as environment variables
- How @Value("${welcome.message}") is set - by using annotation processor,
  it reads value from properties
- Naming convention of the welcome.message
  - welcome_message
  - WELCOME_MESSAGE
- How many instances of welcomecontroller get created?
- Can you set the environment variable again after the application is reset?
- container vs virtual machine
  - container overhead is small in the range of mili seconds
  - spring boot takes time to get started - in the range of 10 seconds
- shows 4 windows - where changing environement variable to 
  pal-tracker application does not get reflected to 
  a new instance (via cf scale) until the app is restarted and
  restaged - this is by design to avoid "configuration drift"
- configuration drift in the context of multiple instances
  - some instances config changed while others are not 
- In production env, developers are not allowed to do "cf push"
  maybe only allowed with "cf apps" command

- cf ssh
  - cf space-ssh-allowed, cf enable-ssh
  - application process inside a container
  - vcap@xxx. vcap is username, xxx is unique host name
  - container is protected by default, linux isolation, I cannot see other container's process
  - garden-init is part of container runtime
  - see the number of processes (compared to normal linux processes)
  - do "ls -al" and see how small number of folders
  - show java command that is created by java buildpack
  - we delete tuning the app to java buildpack - it knows how to
    best optimize the command
  - show staging_info command
  - what is is logs directory for?  it is dummay directory.
    All logs go to standard output device


```
< workspace/pal-tracker - main > cf ssh pal-tracker
vcap@6101881c-bff1-4da1-4497-2dbc:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:06 ?        00:00:00 /tmp/garden-init
vcap          14       0  0 18:06 ?        00:00:00 /tmp/lifecycle/diego-sshd --allowedKeyExchanges= --address=0.0.0.0:2222 --allowUnau
root          21       0  0 18:06 ?        00:00:00 sh -c trap 'kill -9 0' TERM; /etc/cf-assets/envoy/envoy -c /etc/cf-assets/envoy_con
vcap          22       0  0 18:06 ?        00:00:16 /home/vcap/app/.java-buildpack/open_jdk_jre/bin/java -agentpath:/home/vcap/app/.jav
root         100      21  0 18:06 ?        00:00:09 /etc/cf-assets/envoy/envoy -c /etc/cf-assets/envoy_config/envoy.yaml --drain-time-s
root         143       0  0 18:06 ?        00:00:00 /etc/cf-assets/healthcheck/healthcheck -port=8080 -timeout=1000ms -liveness-interva
vcap         169      14  0 18:49 pts/0    00:00:00 /bin/bash
vcap         179     169  0 18:49 pts/0    00:00:00 ps -ef
```

- health check - we will cover in health monitoring module
- ps -ef |grep java
- staging_info.yaml??
- show /app directory (should reflect the contents of the boot jar file
  - /app/BOOT-INF (dependencies - transitive dependencies, classes), 
  - /app/META_INF)
  - /app/.java-buildpack directory contains extra stuff buildpack adds
- buildpack explodes the directory 
- blue-colored ones are the ones under /app/BOOT_INF/lib that are added by buildpack
  - those are symbolic links to buildpack files
  - buildpack inject extra stuff
- client certificate jar file - used by microservices to communicate each other
  using mutual TLS

- env |grep PORT
- containers are on their private network - network overlay??
- private address not public address - CF_INSTANCE_ADDR is private address
- *What is the difference between CF_INSTANCE_ADDR vs CF_INSTANCE_INTERNAL_IP
  See https://docs.run.pivotal.io/devguide/deploy-apps/environment-variable.html
  - CF_INSTANCE_ADDR - The external IP address of the host running the app instance.
  - CF_INSTANCE_INTERNAL_IP - The internal IP address of the container running the app instance
- there is tls_proxy??
- 12 factor - port binding
  - in modern cloud native app use open protocol, use well known port
- do cf set-env WELCOME_MESSAGE 'hello2' and show 
  increase to 2 instances and then perform curl
  - prevent configyration drift
  - what is the problem "cf restart" - downtime

```
CF_INSTANCE_PORTS=[{"external":61008,"internal":8080,"external_tls_proxy":61010,"internal_tls_proxy":61001},{"external":61009,"internal":2222,"external_tls_proxy":61011,"internal_tls_proxy":61002}]
```

- ??there is VCAP-platform-option credhub??

```
VCAP_PLATFORM_OPTIONS={"credhub-uri":"https://credhub.service.cf.internal:8844"}
```

- if you have firewall, talk to platform operators who maintain
  the network provisioning
- ??In fedex, they use 1G memory containers, which results in only 300M
  heap space, which looks under-resourced
- *why the files are in exploded format rather than jar in
  the container - Bill says it is more efficient?  yes Dave Syer

- *"cf stacks" What does linux file system mean?
  a stack is a pre-built file system, including an operating system, that can run apps

```
> cf stacks
Getting stacks in org sashin.pivotal.io / space sandbox as sashin@pivotal.io...
OK

name            description
cflinuxfs3      Cloud Foundry Linux-based filesystem - Ubuntu Bionic 18.04 LTS
windows2012R2   Microsoft Windows / .Net 64 bit
windows2016     Microsoft Windows 2016
windows         Windows Server
```

- cf logs - show prefixes of [APP/..]
- STG
- refreshing (using spring cloud config) is in general a dangerous operation
  (maybe except a use case of feature flag)

- You don't see port or application index in the output "cf env pal-tracker"
- In pcf, you can use vault server without using config server

# Deployment Pipelines (and routing) ------

## Talking points (used by Mike G.)

- One of the key characteristic of successful modern application
  devops team is being able to change code and then 
  to deploy the application to the staging or ultimately production env as often
  and as soon as possible and as little effort as possible.
  And this requires automating of everything that is involved
  in the development and deployment process.  And this is
  where CI/CD comes in.
  
- Automate everything once code is changed
  - merge with code from other developers
  - integration testing
  - creating and versioning a deploy'able package
  - applying external configuration
  - deploying the app
  
- Why we do this lab before we write complete code
   - deployment is hard, we want minimum complication
   - get deployment process taken care of in the earlier stage
     of project life-cycle
   - cannot solve process issues with technology

- Github Actions
   - concept is important, we don't care which CI tool you use
   - Do the demo of setting the environment variables and 
     (maybe set 4 of them early and the add the 5th one
      and show the output GitHub actions or show the
      result from pal-tracker-distrubuted app)

- What CD mean to you?
   - deployment to production should be a business decision
     not an Engineering decision (meaning it should be always
     `ready to be deploy'able to production`)

- Environment set-up in the pipeline (in the Github Actions)

- Why you do NOT want to do "cf push" yourself?
  (many org do not allow manual cf push)
  (jar creation issue - we want to create jar file just once
  and use it in multiple environments)
  (jar versioning - in the form of release - is possible via CI/CD tool)
  (buildpack has nothing to do with creating jar)

(Bill K)
- Automate deployment of our apps
- We are using GitHub actions in this lab, but the concepts we learn
  should be applicable to other CI/CD tools such as Jenkins or Concourse
- Define CI - why do we automate?
  - how long does it take to get the feedback? check in the code -- get feedback
  - 3 minutes or 4 minutes in Fedex - compare to without CI - it might take days
  - we want developers to move quicky by having fast feedback
  - its more than tools, it is a process - we need tools because we need automation
- Define CD -
- repeatable process - being able to deploy the application
  on multiple deployment environment, QA, staging
- build your pipeline (and infrastructure) early in the project cycle
- Our pipeline example is somewhat naive and does not reflect production-quality
  implementation - it is to explain the CI/CD concept with minimum complexity
- CI and CD serve two different purposes

(Charles)
- How cf push from this diagram
- Explain pipeline.yml
- Each build takes a few minutes - a bit tediousness
- build has to be fast - 10 minute build is max you should tolerate
- CI vs CD:
  - CI - check in the code and make sure the integration works
  - CD - deploy to the PCF
  
## Tips

- In order to trigger Github Actions job without making code
  change, you can

  ```
  git commit --allow-empty -m "start a new job"
  git push
  ```

  Or you can select failed action and select "Redo all jobs"
  
- In order to add a linefeed to the end of curl, do

```
echo -w "\n" > ~/.curlrc
```

-  Semantic versioning

```
Given a version number MAJOR.MINOR.PATCH, increment the:

MAJOR version when you make incompatible API changes, backward compatibility is not guaranteed
MINOR version when you add functionality in a backwards compatible manner, and
PATCH version when you make backwards compatible bug fixes.
```
  
## GitHub Actions Tips

- *I could not locate settings under my repository
  It was because I was looking at the wrong pal-tracker
  repository (PAL's) not sashinpivotal below

  ```
  https://github.com/sashinpivotal/pal-tracker
  ```

- [Differences between environment secrets vs repository secrets]
  (https://stackoverflow.com/questions/65957197/difference-between-githubs-environment-and-repository-secrets)
  
  
## Trouble-shooting
      
  

## Extra lab exercise

- How do you deploy to a different environment using GitHub
  conditional statement

## Challenge questions of "Deployment Pipelines" lab

(Cloud native development)
-   What is the factor (among the 12 factors) that is relevant to
    using a pipeline for deploying an application (instead of you
    manually "cf push'ing" yourself?
-   You will notice the WELCOME_MESSAGE is hardcoded within 
    the manifest.yml file checked in with your codebase.  
    How might you approach externalizing the WELCOME_MESSAGE 
    outside of the codebase repository?

(Routing)
-   What makes up a route?  (It is made of [??]+ {??]).
-   We know multiple routes can be assigned to an application.
    Now can a route be assigned to multiple applications?
    [Ref: https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html]
-   Can a route exist without an application associated with it?
    (See “cf routes” and “cf create-route” commands.)
-   What could be the use case of "cf create-route"?
-   When you add a new route to an application using "map-route"
    command, do you have to "restart" or "restage" an application?
-   What is "cf" command to delete all routes that are not
    associated with any apps?-   Can you describe which PCF component (inside Diego Cell)
    in the following responsible for
    updating the routing table that is being used by "GoRouter"
    whenever a new instance is created
    or old instance gets destroyed?

(Blue Green deployment mechanics)
-   When you redeploy the pal-tracker, would there be any downtime?
-   Anybody knows what “blue-green-deployment” for?
-   Speaking of “blue-green deployment”, anybody can think of conceptual
    steps you would take in order to achieve it in PCF environment?
-   How can we control the ratio of the traffic between V1.0.1 (blue)
    vs. V1.0.2 (green) in PCF environment?
-   There is a blue-green deployment cloud foundry plugin available to
    automate the process with smoke test
    [blue-green-deployment plugin](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html)

(Blue green deployment strategies)
-   Is blue-green deployment suitable for major feature change?
-   What are the challenges for doing blue-green deployment?

## Challenge exercise

-  Exercise blue-green deployment by creating "pal-tracker2"
   with WELCOME_MESSAGE of "Hello from the review environment2"
-  For the sake of quick deployment, use "cf push" command instead of using
   pipeline

## Steps for blue-green deployment

- V1 - R1 is currently running
- Create V2 with R2 and make sure it is working
  (cf push pal-tracker-v2 -p ./build/libs/pal-tracker-v2.jar -n pal-tracker-r2)
- Add R1 to V2 - now V2 handles both R1 and R2
  (cf map-route pal-tracker-v2 apps.evans.pal.pivotal.io -n pal-tracker-r1)
- Remove R1 from V1 - now V2 handles 100% of R1
  (cf unmap-route pal-tracker-v1 apps.evans.pal.pivotal.io -n pal-tracker-r1)
- Remove R2 from V2 - now V2 handles only R1
  (cf unmap-route pal-tracker-v2 apps.evans.pal.pivotal.io -n pal-tracker-r2)


## Student questions

- Should "cf set-env" be as part of pipeline (this is important)
- my job is in the queue of jenkins master and does not give me any 
  feedback for 20 minutes - are they using jenkins 2
- *I like junit5 because it gives me a feature selectively running tests

```
I think Paul mentioned they were using tags and filters to help configure 
what tests run in which stage of their 
CD pipeline: 
https://junit.org/junit5/docs/current/user-guide/#writing-tests-tagging-and-filtering
```

- fedex, it takes about 10 to 15 minutes to do integration testing, in some
  cases 45 mintues to 60 minutes
- One Ford student says it takes ~90 minutes to do all integration testing
  covering different regions, etc
- Bill does not like manifest file because it does not support "apply"
  as in the case of k8s
- Blue green deployment does not work because the CI is broken
  (unreliable, many errors, ) we do release every 4 weeks?
  Bill mentioned his experience of fixing the CI/CD pipeline
  from ~xx hours to 1 hour
- create two pipelines for optimizing the response time, one for
  quick merge conflict and unit testing result and another one
  for integration testing that takes longer

## References

```
Continuous Ingeration by Martin Fowler best practices
https://martinfowler.com/articles/continuousIntegration.html

Continuous Integration Certification
https://martinfowler.com/bliki/ContinuousIntegrationCertification.html

Continuous Delivery by Martin Fowler
https://martinfowler.com/bliki/ContinuousDelivery.html

Continuous Deployment
https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment
```

```
[Blue/Green Deployment Best Practices](https://blog.inedo.com/blue-green-deployment-best-practices)
```

```
PCF Rolling update
https://docs.pivotal.io/application-service/2-7/devguide/deploy-apps/rolling-deploy.html
```

# Spring MVC with REST endpoint ------

## Talking points

- Don't change the test code in this lab - that is the contract

- Demo how to remove compile errors also show what to do
  when there are two compile
  errors in a single line - you have to fix the one inside first

- Show how to use IDE for app development
  - test code and target code side by side using IDE
  - do the development in TDD style
  - Use shortcut key combination for running tests

- Show how to add a bean

## IntelliJ Tips for "REST" lab

(Removing compile errors from TimeEntryControllerTest.java)
- Use F2 key to move to the next compile error
- Use ALT/Return to get quick fix tip
- Position test code and target code side by side
- Use tab keys to place "return null" in the target method

(TDD style development)
- Deal with a single test method (and target method) at a time

(Development)
- Study the test code and understand the dependency
  relationship between TimeEntryController and TimeEntryRepository
  - Take a look at setup() method - you should recognize that
    TimeEntryRepository object is a dependency to the TimeEntryController
    So add code in the TimeEntryController to inject that 
    dependency
  - In each test method, study how the dependency is used
  - In each test method, also show how Mockito mock framework is used

## Instruction on how to get InMemoryTimeRepository

Run the following commands under `pal-tracker` directory to
get the InMemoryTimeEntryRepository related code.
(It is no longer needed)

```
In the "Spring MVC with REST Endpoints" lab, after you cherry-pick the "mvc-start" commit, execute the following to get the repository solution:

git checkout tags/mvc-solution  \
   src/main/java/io/pivotal/pal/tracker/TimeEntry.java  \
   src/main/java/io/pivotal/pal/tracker/TimeEntryRepository.java  \
   src/main/java/io/pivotal/pal/tracker/InMemoryTimeEntryRepository.java
```

```
wget https://raw.githubusercontent.com/billkable/pal-tracker/cherry-pick-in-mem-repo/mvc-start-with-inmem-repo.sh
chmod 755 mvc-start-with-inmem-repo.sh
./mvc-start-with-inmem-repo.sh

or
bash <(curl -s https://raw.githubusercontent.com/billkable/pal-tracker/cherry-pick-in-mem-repo/mvc-start-with-inmem-repo.sh)

And then click the io.pivotal.pal.tracker package to see
newly added files.
```

## InMemoryTimeRepositoryTest (We no longer do this)

- How to set the `id` field of `TimeEntry` when it gets created
  without `id` argument?

  - You can create `currentId` field

- When creating a code for `list` method, IDE generates
  `boolean` return type
  instead of `List<TimeEntry>` - you need to manually
  change `boolean` to `List<TimeEntry>`

- In the `list()` test, IntelliJ gets confused when there
  are 5 constructor
  arguments and there is already a constructor that
  takes 4 arguments.

- Object comparison with `equals` and `hashCode`
  - leverage IDE support on this
  - Do you want to include id field?  Sure.

- Creating `List` object from `timeEntryMap.values()`

  ```
  new ArrayList<>(timeEntryMap.values())
  ```

- `timeEntryMap.replace(id, timeEntry)` returns an old
  value not new value
  You can use one of the following two schemes.

  ```
    @Override
    public TimeEntry update(Long id, TimeEntry timeEntry) {
        if (find(id) == null) return null;

        TimeEntry updatedEntry = new TimeEntry(
            id,
            timeEntry.getProjectId(),
            timeEntry.getUserId(),
            timeEntry.getDate(),
            timeEntry.getHours()
        );

        timeEntries.replace(id, updatedEntry);
        return updatedEntry;
    }
  ```

  ```
    public TimeEntry update(long id, TimeEntry timeEntry) {
        TimeEntry oldTimeEntry = timeEntryRepositoryMap.get(id);
        if (oldTimeEntry == null) return  null;
        oldTimeEntry.setHours(timeEntry.getHours());
        oldTimeEntry.setDate(timeEntry.getDate());
        oldTimeEntry.setUserId(timeEntry.getUserId());
        oldTimeEntry.setProjectId(timeEntry.getProjectId());
        timeEntryRepositoryMap.put(id, oldTimeEntry);
        return oldTimeEntry;
    }
  ```

- Show them how to compare code within IntelliJ (git->log)

## TimeEntryController test

- *We are not testing that the create operation sets the location
 response field - verify the solution is something like following:
 (sent a feedback)

 ```
    @PostMapping("/time-entries")
    public ResponseEntity<TimeEntry> create(@RequestBody TimeEntry timeEntryToCreate) {
        TimeEntry timeEntry = timeEntryRepository.create(timeEntryToCreate);
//        URI uri = ServletUriComponentsBuilder.fromCurrentRequestUri()
//                                             .path("/{id}")
//                                             .buildAndExpand(timeEntry.getId())
//                                             .toUri();
//        return ResponseEntity.created(uri).build();
        return ResponseEntity.status(HttpStatus.CREATED)
                             .body(timeEntry);
    }
 ```

 - Make sure @RequestBody and @PathVariable are used appropriately

## Trouble-shooting

- *Somehow adding the code above results in the following error


  ```
        URI uri = ServletUriComponentsBuilder.fromCurrentRequestUri()
                                             .path("/{id}")
                                             .buildAndExpand(timeEntry.getId())
                                             .toUri();
        return ResponseEntity.created(uri).build();
  ```

  ```
  No current ServletRequestAttributes
  java.lang.IllegalStateException: No current ServletRequestAttributes
  ```

  It is because testing did not set the context right.
  See https://stackoverflow.com/questions/9419606/unit-testing-a-method-dependent-to-the-request-context
  Changing the setUp() method as following works.

  ```
    @Before
    public void setUp() {
        timeEntryRepository = mock(TimeEntryRepository.class);
        controller = new TimeEntryController(timeEntryRepository);
        MockHttpServletRequest request = new MockHttpServletRequest();  //<-- new line
        RequestContextHolder.setRequestAttributes(new ServletRequestAttributes(request));  //<-- new line
    }
  ```

- * Somehow some students experience compile error on the assertThat's
  `containsExactlyInAnyOrderElementsOf` method
  * It was because the student did have wrong return type to
  list() method.

```
    @Test
    public void list() throws Exception {
        InMemoryTimeEntryRepository repo = new InMemoryTimeEntryRepository();
        repo.create(new TimeEntry(123L, 456L, LocalDate.parse("2017-01-08"), 8));
        repo.create(new TimeEntry(789L, 654L, LocalDate.parse("2017-01-07"), 4));

        List<TimeEntry> expected = asList(
                new TimeEntry(1L, 123L, 456L, LocalDate.parse("2017-01-08"), 8),
                new TimeEntry(2L, 789L, 654L, LocalDate.parse("2017-01-07"), 4)
        );
        assertThat(repo.list()).containsExactlyInAnyOrderElementsOf(expected);
    }
```

- *If you import the class within the IDE and then get compile errors,
  you will have to rebuild the class

## Challenge Questions of "REST" lab 

(Testing)
1. What are the differences between unit testing and integration 
   testing? Between integration testing and end-to-end testing?
   (There are other types of testing: UI testing, load testing,
   performance testing, etc.  Here we are mostly focused on
   functional testing.)
2. In “pal-tracker” project, which tests are unit tests?
   integrating tests or "pseudo" end-to-end tests?
3. What is "slice testing" in the context of Spring testing framework?
   What are the examples of slice testing?
4. Can you do “integration” or “pseudo end-to-end” testing as part
   of CI/CD pipeline?
5. From unit-testing standpoint, why constructor injection
   is preferred over field injection?
6. What is the difference between stubbing and mocking?
   When do you want use stubbing over mocking and vice-versa?
7. What are the down-sides of using test doubles such as
   stubbing or mocking especially when the code of dependency
   classes change frequently?

(Testing strategies)
1. If you have classes with dependency relationship as following
   (Class A has dependencies class B and C and class B
   has a dependency D, in other words, class A and B has
   dependencies while class C has no dependencies),
   which class do you want to do Unit testing and
   which classes you want to do integration testing?

               ______
               | A  |
               ------
                 |
                 /\
                /  \
            -----  -----
            | B |  | C |
            -----  -----
              |
              /
            -----
            | D |
            -----
   

2. What about a class that depends on backing services such
   as databases? How will you perform the integration testing?

               ______
               | A  |
               ------
                 |
                 /\
                /  \
            -----  -----
            | B |  | C |
            -----  -----
              |
              /
            -----
            | D | ----> [ Database ]
            -----

(Spring testing)
1. What are differences between `RestTemplate` vs `TestRestTemplate`?
2. When do you want to use `@SpringBootTest` vs
   `@ContextConfiguration` for your integration testing
   that involves Spring application context (so that your
   test code have access of Spring beans)?
3. What is the relationship between `@SpringBootTest` and `@SpringBootConfiguration`?
4. Speaking of the testing of controller code, there are three
   different options you can use as following: What are the
   trade-off's of each testing scheme?
   - Option #1: create POJO test that just test the controller business logic
   - Option #2: use MockMvc to test the interaction with the Mvc layer
   - Option #3: use pseudo end-to-end testing using the
     `@SpringBootTest(webEnvironment = RANDOM_PORT)` and
     `TestRestTemplate`
     
(Exception handling)
1. How do you generate exceptions for abnormal conditions in the following 3 layers?
   - controller layer
   - service layer
   - repository (data) layer
2. How do you handle exceptions in these layers?

   (In our "pal-tracker" sample app, we do have only
   controller layer and repository layer and the repository
   layer returns just null for find() operation and does not 
   generate an exception for other operations.)

(Spring)
1. What is the another way of creating `InMemoryTimeEntryRepository`
   bean other than using `@Bean` in the configuration class?
   What would be pros and cons of each approach (component-scanned
   beans vs. bean definition through configuration)?

(Design principles and patterns)
1. What does SOLID (design principles) stand for?
2. What are the examples of “Open for extension Closed
   for modification” design principle in the
   “pal-tracker” project?

## Challenge exercise

1. For now, TimeEntryControllerTest is a unit test code, which does
   not use Spring context (and for a good reason).  Now suppose you
   want to take advantage of Spring context - maybe you want to
   read property files using Spring's @TestPropertySource,
   for example -, how can you change the TimeEntryController.test?
   (Create a new file called TimeEntryController2.test and
   use `@WebMvcTest` and `MockMvc`)
 
2. Another Challenge for the Spring MVC with REST Endpoints lab:  
   Replace your Annotated Controllers implementation with the 
   Functional Endpoints approach: 
   https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#webmvc-fn
  
3. Play around Spring Boot slice testing example
   https://github.com/sashinpivotal/spring-boot-tdd.git
   

## Lab tips

- Use jq command to pretty-format the response

## Answers to challenge questions

- (How does verification work?)
  Mockito.verify(MockedObject).someMethodOnTheObject(someParametersToTheMethod);
  verifies that the methods you called on your mocked object are indeed called.
  If they weren't called, or called with the wrong parameters, or called the
  incorrect number of times, they would fail your test.

- (Why you want to use verify method?)
  The correctness of the unit test of the target class is based on the
  fact that the mock object is called and returns the prescribed
  value.  So if the mock object is not called, the correctness of
  the unit test is not guaranteed.


## Slack channel tips

- `httpie` is easier to use than `curl` especially for posting.

```
The following shows the “curl” and "httpie" examples to create a time-entry:

curl -i -XPOST -H"Content-Type: application/json" localhost:8080/time-entries/ -d"{\"projectId\": 1, \"userId\": 1, \"date\": \"2015-05-17\", \"hours\": 6}"

http post localhost:8080/time-entries projectId=1 userId=1 date=2018-01-01  hours=20

In order to install Httpie, please do

  sudo apt-get install httpie (Ubuntu)

Of course, if you like GUI REST client, you can use PostMan
```

- Install of postman on VDI

```
$sudo snap install postman
$postman&
```
(This is a new one from bill)
- [Postman collection](https://github.com/billkable/cnd-postman-collections)

- TDD presentation - https://www.youtube.com/watch?v=s9vt6UJiHg4


## Reference materials on RESTful app

- [Understanding API-First development](https://tanzu.vmware.com/developer/guides/microservices/api-first-development/)

- [Modernization with Consumer Driven Contracts](https://tanzu.vmware.com/developer/guides/microservices/consumer-driven-contracts/)

- [Spring Cloud Contract](https://spring.io/projects/spring-cloud-contract)

## References for Spring performance:
Spring performance: https://spring.io/blog/2018/12/12/how-fast-is-spring
Spring Cloud Functions: https://spring.io/blog/2018/10/22/functional-bean-registrations-in-spring-cloud-function
Experimental/Beta (not production ready, but keep in eye on them, they may be in the near future):
       Native Images: https://docs.spring.io/spring-native/docs/current/reference/htmlsingle/
       Spring Fu: https://github.com/spring-projects-experimental/spring-fu

## Wrap-up discusson


- Discuss pros and cons of @Bean vs component scan
- Discuss pros and cons of using @Bean vs @Repository
- What is extra behavior of @Repository annotation provides
  to your code?

- *Brad went over the 12 factors - we covered 8 of
  12 factors so far


# Database Migration -------------------------

## Talking points

- Talk about the need of migration
- Talk about service in PAS

(Dylan)
- suggested to work with DBA (if that is the case in your org) as part of the team
- talked about our codebase why we use interface so that we can swap out inmemory database with real database
- in pcf, you don't directly talk to database, so we use ssh channel
  to talk to the database (but ssh channel might or might not be
  available, in mad hatter, available for dev but not for prod)
- another solution is having one-off application (migration app)
- schema vs data migration (we are mostly talking about
  schema migration) - data migration is typically done using
  different set of tools
- what are the things you don't want to do in migration
  - deleting a column, renaming a column - don't do this
  - never to be destructive, always to add not delete
  - eventually you will clean up
- travis does the migration for us

(Bill)
- What is the process of adding a column to the table?
  (answer) Ford is using DB2
- Creating a backing service

(Charles)
- Charles will do architecture diagram where backing service is described
- container is transient, ephumeral - will impact how you write code
- shopping cart in memory is bad idea - use backing service

(Sang)
- *We perform migration locally and in the pcf but we do not do that
  in the pipeline running in GitHub in this lab?  Because our code is still
  using InMemoryTimeEntryRepository?
  How about the JdbcTemplate lab?  Yes, the pipeline.tml in
  the jdbc-start shows that the "build-and-publish" job includes
  starting mysql "sudo service mysql start" and then performing

```
   mysql -uroot -proot < databases/tracker/create_databases.sql
   ./gradlew testMigrate
```


## Tips

- Make sure to use double underscore when creating migration files
- *How do you see the list of services using brew?  `brew services list`
- *How do you install Java11 to Mac? `brew cask install java11`
- When executing flyway command, username and password will be asked.
  Enter `tracker` and no password

## GitHub Action

- *I get the following problem on the migration: it
  was because I was using tracker-database that was
  created in the previous cohort.

  ```
  Flyway Community Edition 5.2.1 by Boxfuse
  Database: jdbc:mysql://127.0.0.1:63306/ad_a3d2568a1752d06 (MySQL 5.5)
  ERROR: Validate failed: Migration checksum mismatch for migration version 1
  -> Applied to database : 1338248810
  -> Resolved locally    : -1395297860
  Closing tunnel
  ##[error]Process completed with exit code 1.
  ```

## Slack channel tips

A couple of CF plugins I would recommend to install: “open” and “mysql” from https://plugins.cloudfoundry.org/

- “open”plugin opens a browser for you with the right route by typing “cf open pal-tracker”
- “mysql” plugin lets you access the mysql database service in the same way you were able to access your local mysql database by “cf mysql tracker-database”.

The installation instruction is right there in the website above. But they are as following:

```
$ cf install-plugin -r CF-Community "open"
$ cf install-plugin -r CF-Community "mysql-plugin"
```

```
$ cf mysql tracker-database

mysql> show databases;
+---------------------+
| Database            |
+---------------------+
| information_schema  |
| cf_metadata         |
| mysql               |
| performance_schema  |
| service_instance_db |
| sys                 |
+---------------------+
6 rows in set (0.05 sec)

mysql> use service_instance_db;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+-------------------------------+
| Tables_in_service_instance_db |
+-------------------------------+
| flyway_schema_history         |
| time_entries                  |
+-------------------------------+
2 rows in set (0.05 sec)

mysql> select * from time_entries;
Empty set (0.05 sec)
```

## Challenge questions of "migration lab"

- Does database migration include data migration in addition to schema migration?
- Migration should keep backward compatibility - don't delete column,
  add a column instead

## Wrap-up

- (Dylan: went through migration script)
  - cf create-service-key
  - vcap-services, credhub-ref, but when you cf env, you will see
    username and password
  - jq command for parsing
- Went through format of the migration file
  - you cannot change the migration file - flyway
    keeps track of checksum - create a new one

- (Bill K)
- development vs production issue??
  - do locally first
- what is flyway clean or migrate command for?
  (you don't want to use clean command in production)
  migrate command will execute migration scripts that are not executed yet
  you cannot run same migration again.  It has checksum that verifies that it was
  executed already so you will create a new script
- flyway allows other versioning scheme such as semantic versioning
- in production env with existing data, do you want to alter that table?
  no, it might result outage
- if you have legacy db (only dba can make change) - index, performance index
  (environment parity is important) your baseline is the dump of all existing
  databases
- what happens if things fail in the middle of migration?
- what is the tool for migration data like ETL (extract, transform, load)?
  ETL is used for data warehousing
  look for ETL type of tools instead of flyway for data migration
- most customers are using external database (oracle, db2, etc.)
- talk to platform operators to find out what plans are available
- ford typically create small/medium apps

(Bill K -10/01/2020)
- bind-service - show vcap-services
- Can I change migration v1 and then run it again? no,
  use show tables and see history

- disposability in cloud environment, repeatable process - major theme
- how can add a column to a table? any change you take (DDL) is
  captured in a new migration file, once migration file is executed,
  you cannot change it, it creates other tables other than time_entries
  table - flyway-schema-history table
- what could be a problem in adding a column in a table with 5 million rows
- as your data grows, your index grows, it will lock your table for
  a long period time - be careful
  we cannot afford downtime - zero downtime requirement
  - how can we solve this? instead of altering and add a new column,
    use view, whatever - this is not clean cut
- your schema might not in match with your domain class, you might
  have to some mapping??  Impedance mismatch
  - show TimeEnry domain class
  - jdbc has a flexibility to reflect the difference between domain model and tables
- adding a new feature with several migrations - might work in development
  but in production, you can use flyway's baseline (production friendly)
  - 12 factor guideline - dev/prod parity violation - but is acceptable
  - solid principle - open close principle

- service broker,  cf marketplace is a catalog of services
- what is service instance?
- user-provided service
- VCAP (vmware cloud application platform)
- the hostname in the vcap-services is not publicly accessible
- ??PCF uses internal DNS
- how can we execute migration script against the database that is
  not accessible - show migration file - migration-database.sh file
- what is "flyway migration clean" - destroying the tables - you don't do
  this in production but useful for development - explain service key
  in the file
- in the next lab (jdbc lab) - we do use gradle plugin

(Bill K - 10/6/20)
- can you change migration to production database?  large scale database
  - it will block significant amount of time, apps will not be available
    significant amount time - stability
  - flyway provides impedance mismatch - it provides flyway baseline??
    - apply a single migration file (instead of hundreds)
    - what happens if you have hundreds of migration files? how do you
      get a sense of the schema's??
  - performance index in production? it should be part of your migration
    - you might want to have dba
- environment parity between dev and production
  - data
  - resource
- companies typically has a process of changing schema
  - use old db server, do ETL first
  - test with new db server, and switch
  - billions of data situation might not work 
  - use OpenClose principle
    - add column 
- you cannot change the migration file and run it again - checksum mismatch

- how does github actions interact with migration work?
- we don't do fly clean in the github action yaml file
- how are we connecting to the database server? via ssh - we are actually
  tunnelling
- where database credentials coming from? using "cf service-key"
- is having database credentials in the pipeline secure??
- we would not use in production environment using ssh given that
  ssh is highly likely to be disabled - 12 factor - administrative process
  - run flyway on the cloud foundry
- in fedex, they use database (oracle) outside of pcf
- docker exec -it tracker-database sh

- development time vs production time database migration
  - production data (a couple of million data)
  - work with DBA
  - you might not use the same history in the dev - instead of flyway baseline

(Charles)
- Add the service component in the diagram
- Cloud native development - apps that run well on the cloud
- There are apps that are not cloud native - example is an app
  that uses local filesystem or maintains "user visible" state
- external database is not transient
- we do bind service in this lab - information that is needed
  to connect to the service is available to the app in the form
  of environment variable
- create-service - self-service model, multiple plans,
  service can reside outside of cloud foundry

(Sang)
- Go over the key points in the Evolutionary database design
  - All database artifacts are version controlled with application code
  - All database changes should be done through migrations
    (don't try to make changes to the database directly)
  - Everybody gets their own database instance (it is easy with
    cloud platform like pcf)
  - Developers continuosly integrate database changes (just like
    continuously integrating code - incremental changes)
  - Clealy separate all database access code - into a repository layer
    (access to the database always has to go through the repository layer code)
  - release frequently


## Student questions

- ??Martin flower suggests each developer should have his/her own database.
  But for external database such as Oracle or DB2, how can we
  provide separate database?


## Reference materials of "Database Migration lab"

(schema migration)
- [Evolutionary Database Design](https://martinfowler.com/articles/evodb.html)
- [Refactoring Databases: Evolutionary Databases Summary](https://databaserefactoring.com/SplitColumns.html)
- [Migration strategies](https://github.com/pivotal-bill-kable/spring-cloud-flyway-migration-demo)

(data migration)
- [Data Migration strategies and best practices](https://www.talend.com/resources/understanding-data-migration-strategies-best-practices/)

# Spring JdbcTemplate -----------------

## Talking points

- (Bill K) create-service
- (Charles)
  - show create a file in a container instanace, restart the instance
    and the file is gone
  - ps -aef in the container shows a lot smaller number of processes

```
vcap@a370edf1-a159-4ccd-445f-151f:~$ ps -aef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 Sep15 ?        00:00:00 /tmp/garden-init
vcap          14       0  0 Sep15 ?        00:00:00 /tmp/lifecycle/diego-sshd --allowedKeyExchanges= --address=0.0.0.0:2222 --allowUnauthenticatedClients=false --inheritDaemonEnv=true
vcap          20       0  0 Sep15 ?        00:03:56 /home/vcap/app/.java-buildpack/open_jdk_jre/bin/java -agentpath:/home/vcap/app/.java-buildpack/open_jdk_jre/bin/jvmkill-1.16.0_RELE
root          32       0  0 Sep15 ?        00:00:00 sh -c trap 'kill -9 0' TERM; /etc/cf-assets/envoy/envoy -c /etc/cf-assets/envoy_config/envoy.yaml --drain-time-s 900 --log-level cr
root          98      32  0 Sep15 ?        00:11:49 /etc/cf-assets/envoy/envoy -c /etc/cf-assets/envoy_config/envoy.yaml --drain-time-s 900 --log-level critical
root         140       0  0 Sep15 ?        00:00:09 /etc/cf-assets/healthcheck/healthcheck -port=8080 -timeout=1000ms -liveness-interval=30s
vcap         179      14  0 16:23 pts/0    00:00:00 /bin/bash
vcap         192      14  0 16:24 pts/1    00:00:00 /bin/bash
vcap         204     192  0 16:24 pts/1    00:00:00 ps -aef
```

(Charles 10/01/2020)
- shows the spring diagram of "injection container" (application context)
  shows shows beans controller, which needs timeentryrepository
  as a collaborator or dependency, also datasource
- spring boot - autoconfiguration of database, provides tomcat server
- spring mvc, spring jdbc libraries

- shows controller code, jdbctimeenterreposty side by side in intellij
  and @Bean defintion
- mentions how DataSource gets autoconfigured locally and in production (PCF)
- run tests with production-like database, it runs reasonably fast, thousands
  insert still runs in a few seconds
- have seen many problems of using non-production database, dev/production parity
- db2 has community edition
- See step 7 for the build.gradle first and then take the step.

- ?? Charles thinks that our test code of create method does not
  check if the database is in fact updated and it should
- ?? Bill - we don't need Eureka server to do container to container
  networking

(Sang)
- Make sure after changing build.gradle, refresh IntellJ or
  close and open the project

### Challenge questions of "JdbcTemplate lab"
(Please do Extra in the lab document first before tackling these challege questions)

-   What are the two conditions that need to be met before
    Spring Boot's auto-configuration create DataSource bean
    that represents MySQL?

-   We know that when we are running pal-tracker app locally, Spring Boot
    auto-configures a `DataSource` bean from the environment-variable
    provided database credentials.
    Now when we deploy the same application to PCF,
    somehow different `DataSource`
    bean gets auto-configured from database credentials from the VCAP_SERVICES.
    How does PCF do this?
    (Hint 1: Take a look at the log of "cf push" and see
    what additional things are added to the Droplet by the
    buildpack.)
    (Hint 2: See https://docs.run.pivotal.io/buildpacks/java/configuring-service-connections/spring-service-bindings.html#auto)

```
With auto-reconfiguration, Cloud Foundry creates the DataSource or connection factory bean itself, using its own values for properties such as host, port, and username. For example, if you have a single javax.sql.DataSource bean in your application context that Cloud Foundry auto-reconfigures and binds to its own database service, Cloud Foundry does not use the username, password, and driver URL you originally specified. Instead, Cloud Foundry uses its own internal values. This is transparent to the app, which really only cares about having a DataSource where it can write data but does not really care what the specific properties are that created the database. Also, if you have customized the configuration of a service, such as the pool size or connection properties, Cloud Foundry auto-reconfiguration ignores the customizations.
```

-   Suppose I have some VCAP_SERVICES environment variables
    that I need to read in my Spring Boot application, is there any helper utility?

    (Hint: See the following for a clue
    https://stackoverflow.com/questions/50456365/how-to-inject-user-provided-vcap-services-in-spring-boot)

-   *What is Spring cloud connector for?
    (Answer: Spring Cloud Connectors provides a simple abstraction
    that JVM-based applications can use to discover information
    about the cloud environment on which they are running,
    connect to services, and have discovered services registered
    as Spring beans. It provides out-of-the-box support for
    discovering common services on Heroku and Cloud Foundry
    cloud platforms, and it supports custom service definitions
    through Java Service Provider Interfaces (SPI).

    This project is in maintenance mode, in favor of the
    newer Java CFEnv project. We will continue to release
    security-related updates but will not address enhancement requests.)

## Challenge Exercise of "JdbcTemplate" lab

- The lab code shows DataSource bean is auto-configured by Spring Boot,
  meaning you don’t have to configure DataSource bean yourself.
  Hence the reason we can inject the auto-configured DataSource
  object into JdbcTimeEntryRepository through constructor injection.
  And we then create JdbcTemplate object ourselves in that constructor.

  Now Spring Boot auto-configures JdbcTemplate bean as well
  in our sample application since it finds "spring-boot-starter-jdbc"
  in the classpath so there is no need for us to create a new JdbcTemplate object.
  So challenge exercise is to refactor the code to use
  auto-configured JdbcTemplate bean instead of manually creating
  it yourself.  Verify that it works by running the test.
  (You will also have to modify "PalTrackerApplication" and
  "JdbcTimeEntryRepositoryTest" classes.)

## Fast forwarding

```
git cherry-pick jdbc-start
git cherry-pick jdbc-solution
git cherry-pick --abort
git cherry-pick --continue (after git add -p) - will commit for you
```

## Student questions

- How can you support multiple databases in Spring Boot app?
  Will it auto-configure two DataSource beans?

- Where do you maintain password?  Youdon't want to have password
  clear text in the VCap services - use vault or creduhub - during runtithe passworkd

  will be retrived from the vault

- ??Microanaut framework?

## Reference materials on Data Persistence 

- [Domain-driven design with relational database using Spring Data JDBC](https://www.youtube.com/watch?v=GOSW911Ox6s&ab_channel=SpringDeveloper)

- [Spring Data JDBC](https://spring.io/projects/spring-data-jdbc)

- [The new kid on the block: Spring Data JDBC] (https://www.youtube.com/watch?v=AnIouYdwxo0&ab_channel=SpringDeveloper)

- [Stop using JPA/Hibernate](https://www.stemlaur.com/blog/2021/03/30/tech-hibern-hate/)

- Complexity of JPA/Hybernate
   - Lazy loading vs Eager loading,
    work fine in development but in production where there
    are lots of rows things start break down
   - Persisting and Deleting - persistent context
   - Optimistic locking complexity
   - caching behavior


## Misc

-   Regarding the usage of `useTimezone`

    [stackoverflow](https://stackoverflow.com/questions/7605953/how-to-change-mysql-timezone-in-a-database-connection-using-java)

    useTimezone is an older workaround. MySQL team rewrote the setTimestamp/getTimestamp code fairly recently, but it will only be enabled if you set the connection parameter useLegacyDatetimeCode=false and you're using the latest version of mysql JDBC connector. So for example:

   ```
   "SPRING_DATASOURCE_URL": "jdbc:mysql://localhost:3306/tracker_dev?user=tracker&useSSL=false&useTimezone=true&serverTimezone=UTC&useLegacyDatetimeCode=false",
   ```


## Tips

1. Using curl and httpie for creating time-entry


```
curl -i -XPOST -H"Content-Type: application/json" pal-tracker-sang-shin.apps.evans.pal.pivotal.io/time-entries/ -d"{\"projectId\": 1, \"userId\": 1, \"date\": \"2015-05-17\", \"hours\": 6}"
```

```
http post pal-tracker-sang-shin.apps.evans.pal.pivotal.io/time-entries projectId=1 userId=1 date=2018-01-01  hours=20
```

1. Using CUPS for an external database (from Brad)

```
@here Using CUPS for an external Database
Create the CUPS
create the cups json from the information in the env output

cf cups cups-db -p '{"jdbcUrl":"jdbc:mysql://p-mysql-proxy.run.pivotal.io:3306/cf_3b945260_b32e_4912", "name": "cf_3b945260_b32e_4912", "password": "0haBVrHbzeu2hyFd"}'

Configure the application
Notice: that we are using the service name and the properties name from the cups command.

application.yml
spring:
  datasource:
    url: ${vcap.services.cups-db.credentials.jdbcUrl}
    username: ${vcap.services.cups-db.credentials.username}
    password: ${vcap.services.cups-db.credentials.password}

NOTICE: application.properties does not work

Push your app

cf push cups-example -p build/libs/datasource-cups-0.0.1-SNAPSHOT.jar --no-start

bind the cups

cf bs cups-example cups-db

Restart the apps

cf restart cups-example
```

## Trouble-shooting

-  *IntelliJ shows any database table references in red-colored
   I turned off SQL inspection and it is gone.
-  *Also the following in the build.gradle is red-colored.
   It was because I did not refresh build.gradle.

```
import org.flywaydb.gradle.task.FlywayMigrateTask
```

If you are experiencing “import org.flywaydb.gradle.task.FlywayMigrateTask” compile error in the build.gradle, do “./gradlew clean” and then refresh the Gradle.

1. *When running `./gradlew clean build` results in Database not
   found problem, you will have to run the database create script
   and migration in the previous lab

1. *When running a test, I get a flyway problem in the build.gradle

   ```
   FAILURE: Build failed with an exception.
   * Where:
   Build file '/Users/sang/workspace/pal-tracker/build.gradle' line: 48
   * What went wrong:
   A problem occurred evaluating root project 'pal-tracker'.
   > Could not find method flyway() for arguments
   [build_87xx1m7rxvlos7m38s5n54g4k$_run_closure3@2f59647a] on root
    project  'pal-tracker' of type org.gradle.api.Project.
   ```

   It was because I did not add the following to the build.gradle

   ```
   import org.flywaydb.gradle.task.FlywayMigrateTask
   ```

   ```
   plugins {
    id "java"
    id "org.flywaydb.flyway" version "5.0.5"
   }
   ```


- *What is the reason we have the following code in the test?
  The purpose of this code is to clean up the `time-entries` table
  each test method is invoked. Otherwise,
  the api test will fail with duplicate entry.

  ```
    @BeforeEach
    public void setUp() throws Exception {
        MysqlDataSource dataSource = new MysqlDataSource();
        dataSource.setUrl(System.getenv("SPRING_DATASOURCE_URL"));

        JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource);
        jdbcTemplate.execute("TRUNCATE time_entries");

        TimeZone.setDefault(TimeZone.getTimeZone("UTC"));
    }
  ```


## Wrap-up talking points "JdbcTemplate lab"

(Sang)
-   *When you do the demo, make sure you run Gradle bootRun
 	 not within the IDE.  Or use CTRl+SHIFT+R (or CTRL+R - no more 8080 port issue)

-   Self-service - you don't have to use old service-ticket
    based system in which you have to send a service request
    tickte to DBA team for getting database credentials
    and put them into properties file or even worse into
    code and then rebuild the app and then deploy

-   12 factor app - 9. Backing Services
    backing services should be pluggable through
    configuration without any code change

-   Correct DataSource bean automatically created
    depending on where the application gets deployed
    
-   Regarding extra
    
```
Just to recap:  a running pal-tracker application does not source VCAP_* directly from the CCDB.  It does so from the container session.

Regarding the VCAP_SERVICES updates, a restart or restage is still required, so follows the same rules as other environment variables.
```

(Bill K)
- If you are using ORM, you really need to know the internals
  for the apps that need high scalability, ...
- You could easily write ORM apps with lots of unnessary queries
  (This will result in performance problems of your applications)
- ??pagination - one reason why JPA is chosen
- Spring Data JDBC is new kid in the block

(Charles)
- The point of the lab is not jdbc vs jpa
- The point of the lab is to save the state into a backing service
- usage of profile is something dangerous, testing is hard with profile
  uasage of environment is recommended
- what about the database that is not available in cloud foundry?
- databases we used - one locally, one in github, one in pcf


# Health monitoring ---------------

## Tips

- The META-INF/build-info.properties is under build/resources/main directory
- ?? /actuator/beans - what is the "resource"

## Talking points

- (Bill K)
- The point of the lab is not actuator but observability of an application
- what types of monitoring tools do you use? How many of you support apps in prod env?
  - fedex: jmx, api turn off and on, weblogic, now they use actuator
  - pm: loggregator of pcf, reactive alert, appdynamics (apm), enterprise operations
- availability probe
- Actuator metrics is rarely used for cloud native app
  - Probably use it when APM (Application Performance Monitoring)
    tools are not available
- For /health value proposition, talk about the case
  "applicatio hang" - GC hang - CF does just health check on port - probably not
  good enough
- What does Ford use for monitoring applications?
  - One student says her group uses actuator like custom tools
  - Any APM tools? Sonarcube is mostly static code analysis tools
    Dynatrace, New Relic, AppDynamics, etc - Ford use Dynatraces
- keep browser open, keep cranking up code

- (Charles)
- Talk about logging agent, loggregator
- its not transactional, it is best delivery effort
- cf logs --recent, cf program and xxxx establishes tunnel
- gorouter does ssl termination
- Even though actuator logger's endpoint let you change the logging
  level
  - app instances in the cloud are disposable
  - it will change just a single instance unless you use spring clous bus


## Trouble-shooting

- If the number of instances are not increasing, make sure the cf auto-scale
  plugin is installed.

- *what is templated below? It means it has a variable to be set or not

```
"_links": {
"self": {
"href": "http://localhost:8080/actuator",
"templated": false
},
"palTrackerFailure": {
"href": "http://localhost:8080/actuator/palTrackerFailure",
"templated": false
},
```

## Prometheus and Grafana

```
Prometheus and Grafana scripts I’ved used - they are using docker -
can be obtained from https://github.com/sashinpivotal/prometheus-grafana

If you don’t have docker installed on your machine, you can download and run prometheus and grafana individually from https://prometheus.io/download/ and https://grafana.com/grafana/download.  And you can use the same configuration files from the above website.
```


## Tips

- In order to set env variable

```
cf set-env pal-tracker MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE "*"
```

## Wrap-up

(Bill K)
- show actuator endpoints using postman
  - /actuator/beans - look into it and you will understand lots of spring internals
  - take a look at the spring source code
  - ???cglib for the TimeEnteryController, what about other beans?
- you probably do not expose mappings,beans,env in production,
  they are mostly for development - however, you could configure
  your firewall so that only the internal traffic within the firewall
  maybe only admin roles can access them
- dynatrace (ford), appdynamics (fedex) will give you better data than metrics
- actuator endpoint does not persist the data
- ./actuator/beans - show cgLib of the timeEntryController??
- adding your custom metrics is rare??
- spring admin server??
- ./actuator/env - could be useful where configuration come from
  multiple sources this could be useful
- ./actuator/info - you could add git plugin as well to get version info
  - mandatory if you are running legacy app where you do not have
    automation tool??
- show app manager - use developer tool for info endpoint - security
  oauth2 from app manager to endpoint??
- don't set environment variable via app manager - could cause configuration drift
- healthcheck within app manager

- you might get the merge conflict if you do cherry pick
- you are mostly configure and observe - operator role

- availability, scalability demo
- probe - 2 kinds of probes - k8s has 4 or 5 probes??
- example of liveness - threads are all used up even though it is "up"
  on its tcp port
- liveness probes are not enabled by default in spring boot
  - except in k8s, it will enable it by default
  - db in HealthCheck in app manager
  - DBHealthIndicator - show the query statement??
  - If connection pool is used up, db will be changed to down state
- transient failure - db is slowing down, 1 minute duration
  - you might end up "dog pile"?? - in football,
  - see the Special section - don't use temporary trasient failure
    of backing services

- *don't use vanila boot health endpoint as pcf http-based health-check
  - instead use liveness probe for pcf http-based health-check
- spring boot app start-up time is 2-3 seconds, if it uses
  discovery service, it might double digit seconds if it uses ??config server
- spring boot 2.2, Health Check screen, endpoint
- simulate the failure, watch PCF is restarting
- how can I get availablity?  use scaling, scale to 2 instances
- 500 requests per second by now, multiply that by 10, we will
  experience

- ideally we want to make our containers to be small and large number of instances
- so we use horizontal scaling, more efficient usage than vertical scaling

- Bill use script to do auto-scaling
- financial organizations typically do "rotating their infrastructure"
  as a security measure
- don't abuse logging, also do not treat as transactional data

- health-check-type, health-check-http-endpoint in the manifest file

- we have this as a lab,
  cf events pal-tracker, watch cf app pal-tracker, jmeter,
  simulate the failure, observe that
  pcf restarts the app after liveness checks the failure

- how can we improve the availability of the lab? scale it up
- vertical scaling - add resources, horizontal scaling - add processes
- what is lenear scaling? being able to handle number of client
  requests linearly the through?
  can you do achieve linear scaling with vertical scaling? we might
  be able to predict to an extent in the old days when using the
  machine, in the cloud, you cannot predict vertical scaling, cpu usage
  is not accurate

(Charles)
- use splunk (ford, fedex) to get the number of entries in the time-entries table
- logs are youf first choice of diagnosing a problem

(Bill)
- show /logs directory of an instance after cf ssh pal-tracker
- 12 factor - XI Logs - send logs to standard out
  - cf logs pal-tracker ../cloudfoundry/health??
  - RTR/2 - 2 signifies 3rd instance of gorouter instance,
  - same as [APP/PROC/WEB/2] 2 means the 3rd instance of the pal-tracker
  - [CELL/1] OUT Container became unhealthy
  - GoRouter has to be highly available
- pcf does not store logs, has to rely on 3rd party log system
  - splunk
- make sure you don't do "trace-level" logging in production system
  - will impact the performance of the platform
  - changing logging level in app manager - Bill recommends not to use it
    - you do it and you forget and walk away
    - splunk charges 10 times more expensive
    - use new relic tracing feature
    - changing logging level during runtime is power tools and
      you have to be careful in using it

## Student questions

- ??Somehow I don't see how pcf health endpoint enabled - we did not
  enabled for pcf while we did locally - we will cover it during
  wrap-up

# Scaling lab ----------------

- Auto-scaling lab, in the Recent History, you will see something

  ```
  Scaled up from 2 to 3 instances. Current HTTP Latency of 35.92ms is above upper threshold of 3.00ms.
  ```

- You don't need app manager in the latest version of the lab
  since Bill provided scripts
- app manager url [https://apps.sys.evans.pal.pivotal.io](https://apps.sys.evans.pal.pivotal.io)

(Intro: Bill)
- no code in this lab
- stack represents OS that runs in the cell
  - VM can run either linux or windows - cannot run them at the same time
  - memory and disk quota are limits
  - memory-calculator - you don't have to use java options
  - show how to optimize resource consumption - memory, disk, timeout
    - cells in the body come and go, insances come and go - we don't
      really care
  - we do some exploratory testing in this lab
  - we do not use app manager in this lab - but you
    can do the same in app manager

  - load testing we do here is very native, since we accessing
    only a single endpoint
  - set enviroment variables and then copy and paste instruction
    from the lab document
  - the goal of this lab is to make our container size as small as possible
    - vm is limited in resource size
    - vm is set with 32G in our foundation
    - in our foundation, each container is maximum 2G
    - the number of container 16 since 32/2?  But in reality,
      you will get around 10 since there are other things running
      on the vm

  - then experience failures due to availability issue
    - increase availability by spinning more instances
    - scalability is not availability (redundances - replica in k8s)
    - in pcf we don't have replicas  - it has instances
    - platform operator will replace vm - unplanned maintenance
      - spin 3 instances instead of 1 (this is availability)
    - what about a case where an instance can handle only x number of
      requests (this is scalability)

    - user sessions used in web app, this is 20 year pattern
      same instance handles
      the requests from the same user - but we cannot do this in pcf
      because gorouter will do round-robin load balancing
      - green field projects - it should not be a problem
        use spring session project

   - auto-scaler is a bonus project so skip it if you don't have time

## Command

```
docker run -i -t --rm -e DURATION=300 -e NUM_USERS=10 -e REQUESTS_PER_SECOND=5 -e URL=http://pal-tracker-sang-shin.apps.evans.pal.pivotal.io  pivotaleducation/loadtest
```

or set environment variables as following

```
export UNIQUE_IDENTIFIER=sang-shin
export DOMAIN=apps.evans.pal.pivotal.io
docker run -i -t --rm -e DURATION=300 -e NUM_USERS=10 -e REQUESTS_PER_SECOND=5 -e URL=http://pal-tracker-${UNIQUE_IDENTIFIER}.${DOMAIN}  pivotaleducation/loadtest
```

```
2. In the cf app Watch window, monitor the amount of cpu, memory and disk resources taken for the test.

     state     since                  cpu     memory         disk         details
#0   running   2021-01-14T18:50:48Z   10.6%   174.1M of 1G   164M of 1G
```

 - *Does the following to set the failure of a single instance

 ```
 curl -v -XPOST -H "Content-Length:0"  http://${APP_URL}/actuator/palTrackerFailure
 ```

## Slack channel tips

- [JMeter installation on Ubuntu](https://linuxhint.com/install_apache_jmeter_ubuntu/)

## Wrap-up

- See [Scaling rules](https://docs.run.pivotal.io/appsman-services/autoscaler/using-autoscaler.html#metric) for scaling rules detail
- See [Autoscaler decision timing](https://docs.pivotal.io/application-service/2-10/appsman-services/autoscaler/about-app-autoscaler.html)
- The following blog post is a good read on Cloud Foundry CPU resource management: https://www.cloudfoundry.org/blog/better-way-split-cake-cpu-entitlements/
- See [PCF Autoscaler advisory for scaling Apps based on the CPU utilization](https://community.pivotal.io/s/article/PCF-Autoscaler-Advisory-for-Scaling-Apps-Based-on-the-CPU-utilization?language=en_US)
- *When applying auto-scaling, what is "Percent of traffic to apply
  95% or 99%"?
- How do you know how many instances to run?
  - why not 1 instance? availability
- (Bill K) shows apps manager and shows auto-scaling feature
  using JMeter now with load test

(Bill K)
-   what do you mean by scaling?  we are talking about greenfield app
-   what is vertical scaling? add more resources to a container
-   what is horizontal scaling? add more containers,
    cheap to do it on modern platform
    - Bill talked about diego cell memory size
    - higher utilization of resources on cloud platform
    - make instances as small as possible
    - 2G per container constraint - write your app to fit
    - pcf quota applies to spaces
    - capacity planning
-  auto-scaler - use it until you get some experience on the app charactertistics
    - it is not as smart as you
    - you can create autoscale.yml for auto-scaling

-  cf configure-autoscaling pal-tracker <yaml file>
-  watch autoscaling-events pal-tracker

-  loadtest (node based app)
-  auto-scaling is not instantaneous - it collects data and then act
-  use auto-scaling only after you get some performance data

-  3 instances minimum per foundation, 1 instance is never a good idea
   (if operator has to update security patch, it will be down)
   foundations are not co-ordnadint
   - plan unplanned outages, we kept 5 because pcf is resouce bound
   - 32g memory
   auto-scalling is not solving everything, it is not a magic
   more tools you bring, you have something else to break
-  operator can take the cell out for security patch (planned outage)
   network reconfiguration could cause unplanned failure
-  part of cloud native application to make appliation small if possible
   then you can scale out

-  why choose throughput over latency/cpu in our auto-scaling lab??
   why not use cpu?
   - it has get metrics from somewhere? 3 layers of abstraction,
     which is not reliable - at the container level - same at virtual
     machine level
   - latency - not a good indicator for blocking app
     - your app might wait for database access or response from other services
   - throughput is predictable - much more reliable
-  autoscaling takes time to respond - 20 to 30 seconds
   - it is not instatneous - it is like cruise control - it is not
     meant to react to sudden chagnes
   - use it when application behavior is well known??
   - read the article from reddit, read Release It book

-  rabbitmq queue is a good rule when ordering is not required?

-  don't use resource-based auto-scaling because you are running
   container over vm - 3 levels of abstraction - you cannot
   get accurate resource consumption data because there are
   many abstractions - virtual machine, container
   - so use throughput for blocking applications
   - there used to be an vmware advisory for not recommending to use
     throughput because there was a bug in auto-scaler, which is now
     fixed
-  for messaging applications, use number of messages in a queue (queue depth)
   - however it is tricky to get the accurate data
-  disk quota - you don't want write anything to disk - it is used
   for mostly housekeeping stuff, 1G is too high
   these figures are per instance
   - also space and organization also have quota

-  ?? Bill showed some demo of showing off a special request header
   Telling the go router to route to a specific instance.


# App Continnum

## Talking points

(Mike)
- Delay architectural decision to as latest point as possible
- Use a single repository for multiple applications as long as possible
  - It is easy to move around domains between applications

(Charles)
- Feature groups
  - allocaiton code has date format code
  - timesheets code decides to use that date format code

```
Fallacies of networking computing: https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing
```

```
Dealing with consistency in microservices: https://microservices.io/patterns/data/saga.html
```

```
Native images:
-   GraalVM
    - Limitations: https://github.com/oracle/graal/blob/master/substratevm/Limitations.md
- GraalVM integration for boot:
    - https://blog.indrek.io/articles/running-spring-boot-apps-as-graalvm-native-images/
    - https://github.com/spring-projects-experimental/spring-native/releases/tag/0.8.3
    - https://repo.spring.io/milestone/org/springframework/experimental/spring-graalvm-native-docs/0.8.3/spring-graalvm-native-docs-0.8.3.zip!/reference/index.html
- Micronaut (Spring competitor): https://micronaut.io/
```

- [App Continuum Slides](http://deck.appcontinuum.io)
- [App Continuum website](http://appcontinuum.io)

# Distributed System


## Talking points

-   Explain what the `${USER_ID}` and `${PROJECT_ID}` variables for
-   Describe the relationship among the 4 apps - use Bill Kable's picture
-   Describe how to change the http://FILL_ME_IN - registration server
    endpoint is something you configure in the manifest.yml file
    of the registration server
-   Demo how to use httpie or postMan
-   (Bill) ??he does not want to use the term Microservices

-	??? What was the reason we do pull in the pipeline

## "pal-tracker-distributed" Code review suggestions

(Review component structure)
- How is each component built? - check build.gradle of each component
- What is the domain model of each component (bounded context)?
  (Refer to "graph.dot.png" and the "pal-tracker-distributed" application
  architecture diagram posted to the slack)
- Are there any circular dependencies among components?
- How do you define the build order of the components?
- Why are there variations of a domain class, for example,
  why are there `TimeEntryForm`, `TimeEntryInfo`, `TimeEntryRecord`,
  `TimeEntryFields` classes? Where are they used?

(Review Micro-services architecture)
- How each application is built - check build.gradle and server.gradle
- Check configuration of each application (refer to graph.dot.png)
  - where do you configure your beans in each application?
  - how does it specify component-scanning base packages?

(Interaction of Micro-services)
- How does each component expose its functionality? Does it
  has a controller?
- What is the calling relationship among 4 micro-services?
  (Refer to the "pal-tracker-distributed" application
  architecture diagram)
- When "allocation-server" needs to call "registration-server"
  using RestTemplate, where does it find the address of the latter?
- What is the class in each of the calling applications
  ("allocation-server", "backlog-server", "timesheets-server")
  that captures interaction logic with callee application?
  (Refer to the "pal-tracker-distributed" application
  architecture diagram posted)
- Why is ProjectClient code duplicated in backlog, timesheets, allocation
  server apps?
- Why do we have projects, accounts, users in a registration server?
  (In other words, why we did not have separate server for each of domain
  objects?)

(Testing)
- How does each component get tested?
- How does each application get tested?
- How are interactions among the micro-services tested?

## Code review

-   Review component architecture

-   Whenever a new `backlog`, `allocation`, `timesheet` needs to
    be created, backlog, allocation, and timesheet application has
    to know if a corresponding `Project` is already enabled or not.

-   Each of these components (backlog, allocation, timesheet) has
    controller class in which it uses `projectIsActive` method

    ```
    @PostMapping
    public ResponseEntity<AllocationInfo> create(@RequestBody AllocationForm form) {

        if (projectIsActive(form.projectId)) {   // <--------------
            AllocationRecord record = gateway.create(formToFields(form));
            return new ResponseEntity<>(present(record), HttpStatus.CREATED);
        }

        return new ResponseEntity<>(HttpStatus.SERVICE_UNAVAILABLE);
    }

    private boolean projectIsActive(long projectId) {. // <--------------
        ProjectInfo project = client.getProject(projectId); // See ProjectClient class

        return project != null && project.active;
    }
    ```

-  Each of these component has `ProjectClient` class, in
   which `getProject(..)` method is provided

   ```
   public class ProjectClient {

    private final RestOperations restOperations;
    private final String registrationServerEndpoint;

    public ProjectClient(RestOperations restOperations, String registrationServerEndpoint) {
        this.restOperations= restOperations;
        this.registrationServerEndpoint = registrationServerEndpoint;
    }

    public ProjectInfo getProject(long projectId) {
        return restOperations.getForObject(registrationServerEndpoint + "/projects/" + projectId, ProjectInfo.class);
    }
   }
   ```

-   Variation of domian class

    - TimeEntryForm (under .timesheets package)
    - TimeEntryInfo (under .timesheets package)
    - TimeEntryRecord (under .timesheets.data package)
    - TimeEntryFields (under .timesheets.data package)

-   4 different databases vs a single database

    - take a look at schema files under `databases`

-   Data access abstraction

    - TimeEntryDataGateway
    - AllocationDataGateway
    - ProjectDataGateway
    - AccountDataGateway
    - UserDataGateway
    - StoryDataGateway

## Tips

- To clean up the pal-tracker resource to conserve resources in evans

```
cf delete pal-tracker -f -r
cf delete-service-key tracker-database flyway-migration-key -f 
cf delete-service-key tracker-database cf-mysql -f 
cf delete-service tracker-database -f
```

```
curl -v -XPOST -H"Content-Type: application/json" localhost:8081/allocations -d"{\"projectId\": 1, \"userId\": 1, \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

```

- siege -c255 urls.txt

  ```
  https://registration-pal-sangshin.apps.evans.pal.pivotal.io/users/1
  https://registration-pal-sangshin.apps.evans.pal.pivotal.io/accounts?ownerId=1
  https://registration-pal-sangshin.apps.evans.pal.pivotal.io/projects?accountId=1
  https://allocations-pal-sangshin.apps.evans.pal.pivotal.io/allocations?projectId=1
  https://backlog-pal-sangshin.apps.evans.pal.pivotal.io/stories?projectId=1
  https://timesheets-pal-sangshin.apps.evans.pal.pivotal.io/time-entries?userId=1
  ```

- [Postman collection](https://github.com/billkable/cnd-postman-collections)

- Installation and running of postman

```
$sudo snap install postman (or snap install --candidate postman)
$postman&
```

- Tip to replace - ?? somehow the following does not work

  ```
  find ./ -type f -exec sed -i -e 's/\$\{UNIQUE_IDENTIFIER\}\.\$\{DOMAIN\}/sang-shin.apps.evans.pal.pivotal.io/g' {} \;
  ```
  
- changing manifest files

```
For those of you wanting to configure your routes and registration server endpoint in your manifests from the command line, you can run the following with your unique combination of ${UNIQUE_IDENTIFIER}.${DOMAIN}
sed -i 's/${UNIQUE_IDENTIFIER}.${DOMAIN}/<your unique id and domain>/g' manifest*.yml
sed -i 's/${REGISTRATION_SERVER_ROUTE}/registration-pal-<your unique id and pcf domain>/g' manifest*.yml
```

- Bill's script

```
You can get the set up script here: https://raw.githubusercontent.com/billkable/pal-tracker-distributed/main/scripts/set-user-env.sh
cd ~/workspace/pal-tracker-distributed
wget https://raw.githubusercontent.com/billkable/pal-tracker-distributed/main/scripts/set-user-env.sh





11:01
It takes a single parameter associated with your unique route specification you used in the pal-tracker application: {UNIQUE_IDENTIFIER}.{DOMAIN}
```

## Challenge questions of "Distributed Systems" lab

```
(Component-based application architecture)
1. If you are responsible for a greenfield project, would
   you start with Microservice architecture or monolith
   architecture? Why?
2. In the component architecture, what is the role of
   component and what is the role of application? How
   would you divide the required logic between the two?
3. Why are we using a single repository for all 4 microservices?
   Isn't it a violation of the first rule of 12 factor app guidelines?

(Database related)
1. In the "pal-tracker-distributed", we use 4 different
   databases, one for each application.

  - Is it a recommended practice?
    Should we have a single database instead?
    What factors would you consider?
  - Is it possible to have database inconsistency among
    the databases if there are multiple databases?  (For example,
    a user is deleted in User database, how does other databases
    reflect that change?) What would be the consequence to
    overall application behavior?
  - Is it OK to have duplication among the multiple databases?
    (In 'pal-tracker-distributed", we don't have any duplicate data.)
  - Is distributed transaction possible in micro-service architecture?

2. Application code should be insulated from data access logic?
   How do we achieve that in the "pal-tracker-distributed"?

(Monolith to Microservices - Database related)
1. What strategies can we take to break up tangled database schema
   (maybe with foreign key relationship among themselves)
   when migrating monolithic application to micro services?
  
(Interaction between services)
1. What does "API First" mean to you?
   (Read "API First" section of https://www.cdta.org/sites/default/files/awards/beyond_the_12-factor_app_pivotal.pdf)
2. How do you develop "API First" services?
   (Read https://tanzu.vmware.com/developer/guides/microservices/api-first-development/)

(Event-driven architecture and/or non-blocking call)
1. What would be the use cases where even-driven architecture
   is preferred?
2. Would it make sense to use event-driven architecture
   in the current form of pal-tracker-distributed app?
   (In other words, would it make sense
   to make the invocation of the registration server
   from other 3 servers event-driven?)
3. What about non-blocking call?

```

- Some answers to the above questions

```
(Single repository for all apps)
- it's tradeoff - pros
  - easier to change domain models especially when bounded contexts
    are still in fluctuation
  - easier to deploy since they are all deployed together
- cons
  - making a small change might triger the complete build process
- recommendation
  - stay with a single repository model until the size of the
    project requires different apps being maintained and
    deployed by different team
  - wait until bounded contexts are well-established
(App vs component role)
- App
  - Spring boot wrapper
  - Enabling spring features such as @EnableTransaction
  - logical place for configuration including component scanning
  - setting properties
- Component
  - Capture most business logic
  - make it as POJO as possible, independence from spring framework
(Database)
- In general, the benefit of microservices is maximized when each
  service has its own database
- The worst case scenario is when micro services are directly
  sharing a single database - they all talk to directly to the
  database
- Many patterns to address these, but a couple of relatively
  easy options could be through some abstractions
  - one abstraction could be using separate views for separate apps
  - abstracting the access to the database in the form of
    another service (performance implication)
(Transaction)
- In distributed applications, achieving 100% of ACID properties
  or 100% consistency would be hard.
  However, for many applications, eventual consistency could
  be good enough.
  In the scheme of eventual consistenty, 100% of consistency
  at a single point in time is not possible, but eventually
  they will be consistent.
```

## Reference materials on Microservices

- [MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html)
- [Don’t start with a monolith](https://martinfowler.com/articles/dont-start-monolith.html)
- [Microservice Prerequisites](https://martinfowler.com/bliki/MicroservicePrerequisites.html)
- [Microservices and Microservices Architecture](https://www.atlassian.com/continuous-delivery/microservices/building-microservices)

## Reference materials on Database refactoring

- [Chapter 5: Splitting the Monolith" from "Building Microservices"
  written by Sam Newman (O'Reilly)]
 (https://smile.amazon.com/Building-Microservices-Designing-Fine-Grained-Systems/dp/1491950358/ref=sr_1_3?crid=O30N4C7P4G8&dchild=1&keywords=building+microservices&qid=1602278414&sprefix=building+mi%2Caps%2C155&sr=8-3)
  
- [Monolith to Microservices: Evolutionary Patterns to Transform Your Monolith]
  (https://smile.amazon.com/Monolith-Microservices-Evolutionary-Patterns-Transform/dp/1492047848/ref=sr_1_3?crid=3DNLL2GV8BVND&dchild=1&keywords=microservices+sam+newman&qid=1602278452&sprefix=microservices+sam%2Caps%2C159&sr=8-3)
  
- [Refactoring Databases](https://smile.amazon.com/Refactoring-Databases-Evolutionary-paperback-Addison-Wesley/dp/0321774515/ref=sr_1_3?dchild=1&keywords=database+refactoring&qid=1602278543&sr=8-3)

## Reference materials on distributed transaction

- [Microservices Pattern: Saga](https://microservices.io/patterns/data/saga.html)

## Reference matrials on Microservices workflow

- [Choreography vs Orchestration in serverless microservices](https://www.youtube.com/watch?v=rDSWHNdYx6E&ab_channel=AngelbeatRonGerber)
- [Google Cloud Workflow](https://cloud.google.com/workflows)


## Misc

- [REST API testing strategies](https://www.sisense.com/blog/rest-api-testing-strategy-what-exactly-should-you-test/)


## Trouble-shooting

- *Somehow port 8081 is taken on my machine and "openPorts"
  does not show if the port is taken by any process
  (It is because the MaAfee is installed by VMware security team
  on my machine.)

  You can try the following command on Mac

```
< workspace/pal-tracker-distributed - main > sudo lsof -i tcp:8081
Password:
COMMAND  PID USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
macmnsvc  69  mfe   20u  IPv6 0x607ea1e1983cb26d      0t0  TCP *:sunproxyadmin (LISTEN)
```

- *Where is the migration step in the pal-tracker-distributed app?
  It is at the end (after deployment) of the pipeline.yml

  ```
    migrate-databases:
    needs:
      - deploy-allocations
      - deploy-backlog
      - deploy-registration
      - deploy-timesheets
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Install Cf
        run: |
          wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
          echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
          sudo apt-get update
          sudo apt-get install cf-cli
      - name: Migate tracker-database
        run: |
          cf login -a "$CF_API_URL" -o "$CF_ORG" -s "$CF_SPACE" -u "$CF_USERNAME" -p "$CF_PASSWORD"
          ./gradlew cfMigrate
        env:
          CF_API_URL: ${{ secrets.CF_API_URL }}
          CF_ORG: ${{ secrets.CF_ORG }}
          CF_SPACE: ${{ secrets.CF_SPACE }}
          CF_USERNAME: ${{ secrets.CF_USERNAME }}
          CF_PASSWORD: ${{ secrets.CF_PASSWORD }}
  ```

- *When you execute the following command - you have to remove or commit
  the codebase.txt file

  ```
  < workspace/pal-tracker-distributed + main > git cherry-pick pipeline error: your local changes would be overwritten by cherry-pick.
  hint: commit your changes or stash them to proceed.
  fatal: cherry-pick failed
  ```

# Service Discovery -----------------

## Talking points

- (Dylan)
  - talked about problems of microservices - services come and go
  - in pcf, every routing goes through gorouter - we may need more
    security, and more faster
  - gorouter (for public facing apps) vs eureka server (use it for
    internal communication)
  - container to container networking (with it even if you are using Eureka
    server, the services are still going through the gorouter)
  - eureka server still gives you client-side load-balancing,
  - eureka server can be used as a monitoring tool (health check)


(Bill, 12/11/2020)
-   This lab has a lot of moving parts: service discovery/registration,
    client side load-balancing, spring cloud dependencies, end-to-end
    testing.
-  GoRouter plays a role of service registry in the form of
   DNS server and it does load-balancing
-  Issues of using gorouter
   -  latency issue
   -  Exposing your app to the public

- Service discovery
	-   Explain why service discovery and registration could be useful
	    in cloud
	    - in the cloud environment, services come and go
	    - you don't want use hard-coded address of target service

	-   Discovery server can also play the role of making sure
	    unresponsive servers are removed from the list

- Client side Load balancer diagram
	-  Relationship between service discovery and client
    	side load balancer
   -  RestTemplate annotated with @LoadBalanced annotation
      will talk to discovery server and retrieves the
      list of addresses and then perform client-side
      load-balanced

-   Dependency management (using Spring cloud dependency slides)
    - [Neil's slide](https://docs.google.com/presentation/d/1sY6mz_SRfRO-KFonJDjfEujgTFNmDkddit5l090PEZM/edit?ts=5d5a5860#slide=id.p) is a good one
    - Draw picture of SCS tile SCS client library
      - Spring cloud release train - Horton, Greenweech, ..
    - Technical debt because when the version of the tile changes,
    the applications need to be changed
    - How to resolve patch version - go to maven repo and find out


## Tips

- When you run "./gradlew clean build", the following is a expected behavior

  ```
  com.netflix.discovery.shared.transport.TransportException: Cannot execute request on any known server
  ```

In order to find right version of "springCloudVersion"
and "springCloudServicesClientLibrariesVersion", you have
to do the following

1. Get the Tile version installed in PCF as descried in the
   guide.  Right now it is "2.1.4-build.4", which has to match with "springCloudServicesClientLibrariesVersion" (Spring Client Starters)

2. From the the table from https://docs.pivotal.io/spring-cloud-services/3-1/common/client-dependencies.html#including-spring-cloud-services-dependencies, we are supposed to use 2.1.x of "springCloudServicesClientLibrariesVersion" (Spring Client Starters) and 2.1.x of Spring Boot something like following:

```
springBootVersion = "2.1.6.RELEASE"
springVersion = "5.1.8.RELEASE"

springCloudVersion = "Greenwich.RELEASE"
springCloudServicesClientLibrariesVersion = "2.1.2.RELEASE"
springCloudCommonsVersion = "2.1.1.RELEASE"
```

Unfortunately, a consequence of using Spring Boot 2.1.x is that from  Spring Boot 2.1.x, bean overloading is disabled.  (In order to enable it, you have to enable it using a property.)  Since we use bean overloading in the subsequent labs (like security lab), and our lab document does not mention bean overloading, we can use the versions in the solution lab, which works. So please use the following:

```
springBootVersion = "2.0.6.RELEASE"
springVersion = "5.0.9.RELEASE"

springCloudVersion = "Finchley.SR2"
springCloudServicesClientLibrariesVersion = "2.0.2.RELEASE"
springCloudCommonsVersion = "2.0.0.RELEASE"
```

- apps.evans.pal.pivotal.io is using the following


  ```
  curl https://spring-cloud-broker.apps.evans.pal.pivotal.io/actuator/info
  ```

```
{
   "git" : {
      "commit" : {
         "id" : "325b9c6",
         "time" : "2019-11-25T20:46:52Z"
      },
      "branch" : "HEAD"
   },
   "build" : {
      "version" : "2.1.5-build.6",
      "name" : "service-broker",
      "time" : "2020-06-02T20:45:31.537Z",
      "group" : "io.pivotal.spring.cloud",
      "artifact" : "spring-cloud-service-broker"
   }
}
```

- Example

   ```
   springCloudVersion = SPRING_CLOUD_VERSION
   springCloudServicesClientLibrariesVersion =   SPRING_CLOUD_SERVICES_CLIENT_LIBRARIES_VERSION
   ```

   The following worked with SCS was 2.0.8

   ```
   springCloudVersion = "Finchley.RELEASE"
   springCloudServicesClientLibrariesVersion = "2.0.3.RELEASE"
   ```

   In the solution project??

   ```
   springCloudVersion = "Finchley.SR2"
   springCloudServicesClientLibrariesVersion = "2.0.2.RELEASE"
   springCloudCommonsVersion = "2.0.0.RELEASE"
   ```

   Now evanss SCS is 2.1.3 and guide says

   2.1.x (uses Spring Cloud Connectors)	 2.1.x Spring Boot). Greenwich.x

   ```
   ext {
        springBootVersion = "2.1.13.RELEASE"
        springVersion = "5.1.14.RELEASE"
        mysqlVersion = "8.0.13"
        jacksonVersion = "2.9.7"
        slf4jVersion = "1.7.25"
        mockitoVersion = "2.23.0"
        assertJVersion = "3.11.1"
        hikariVersion = "3.1.0"
        logbackVersion = "1.2.3"
        junitVersion = "4.12"
        okhttpVersion = "3.12.0"
        jsonPathVersion = "2.4.0"
        springCloudVersion = "Greenwich.SR5"
        springCloudServicesClientLibrariesVersion = "2.1.7.RELEASE"
        springCloudCommonsVersion = "2.1.5.RELEASE"
    }
   ```

- In order to find out the latest versions of the above two,
  either use mvnrepository.com or google

  `spring cloud services starter service registry maven`

  and see [maven repository for Spring cloud services starter service registry](https://mvnrepository.com/artifact/io.pivotal.spring.cloud/spring-cloud-services-starter-service-registry)


-  Verification of the Health endpoint (after all work is done)

   ```
         "discoveryComposite" : {
         "status" : "UP",
         "details" : {
            "eureka" : {
               "status" : "UP",
               "details" : {
                  "applications" : {
                     "BACKLOG-SERVER" : 1,
                     "TIMESHEETS-SERVER" : 1,
                     "ALLOCATIONS-SERVER" : 1,
                     "EUREKA-SERVER" : 1,
                     "REGISTRATION-SERVER" : 1
                  }
               },
               "description" : "Remote status from Eureka server"
            },
            "discoveryClient" : {
               "details" : {
                  "services" : [
                     "eureka-server",
                     "allocations-server",
                     "backlog-server",
                     "registration-server",
                     "timesheets-server"
                  ]
               },
               "status" : "UP"
            }
         }
   ```

## Challenge questions

-  Can discovery service and client-side loadbalancing be used
   independently from each other?

-  What are the differences between client-side loadbalancing and
   server-side loadbalancing?  When do we want to use one
   over the other?

-  One of the benefits of client-side loadbalancing is being
   able to choose different load-balancing schemes at runtime.
   What are the example client-side loadbalancing schemes?

-  What does `@LoadBalanced` annotation used over `RestTemplate`
   do for the application?

-  In the early presentation, we talked about one of the
   benefits of using Spring Boot is its dependency management.
   But somehow in this lab (Discovery lab), we were asked to do
   manual dependency management such as finding out the version
   of spring-cloud-commons and add it to the rest-support's
   build.gradle.  Is this a recommended practice?

## Challenge exercise

-  Retrieve the list of apps using rest call

   ```
   Challenge exercise on Discovery lab:
   Use curl command to get the list of apps registered to the Eureka server.
   Use the info from the following website: (but remove the "v2" from the url)
   https://github.com/Netflix/eureka/wiki/Eureka-REST-operations
   ```

## Container-to-Container networking

- When container-to-container networking is enabled, the
  Eureka server will maintain the addesses of the service
  instances in the form of internal ip addresses, with
  which the calling service can communicate directly
  with the destination service

- *Is container to container networking enabled in evans? It is now.

  ```
  < workspace/pal-tracker-distributed - main > cf add-network-policy tracker-allocations --destination-app tracker-registration --protocol tcp --port 8080-8090
  ```

- Add network policy

  ```
  cf add-network-policy SOURCE_APP --destination-app DESTINATION_APP -s DESTINATION_SPACE_NAME -o DESTINATION_ORG_NAME --protocol (tcp | udp) --port RANGE
  ```

  ```
  cf add-network-policy tracker-allocations --destination-app tracker-registration --protocol tcp --port 8080-8090
  ```



## References

- [Configuring Cross Cloud Foundry Service Registy (route mode)](http://docs.pivotal.io/spring-cloud-services/1-4/common/service-registry/enabling-peer-replication.html)

- [GoRouter does honor Ribbon load balancing algorithm](http://docs.pivotal.io/spring-cloud-services/1-4/common/service-registry/connectors.html#instance-specific-routing-in-ribbon)

- [Configuring PCF Container-to-Container Networking, Service Registry and Client Load Balancing (SpringOne 2017)](https://www.youtube.com/watch?v=1WJhFhBr-0Q)

## Client side load balancing

- [Ribbon](https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-ribbon.html)

## Trouble-shooting

- *I get the following error when creating

  ```
  < workspace/pal-tracker-distributed - main > curl -i -XPOST -H"Content-Type:  application/json" allocations-pal-sang-shin.apps.evans.pal.pivotal.io/allocations/ - d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\":  \"2015-05-18\"}"
  HTTP/1.1 500 Internal Server Error

  {"timestamp":1587121186241,"status":500,"error":"Internal Server Error","message":"No instances available for registration-pal-sang-shin.apps.evans.pal.pivotal.io","path":"/allocations/"}
  ```

  *It was because I did not perform `cf unset-env REGISTRATION_SERVER_ENDPOINT`
  as instructed in the lab document

- *If you experience the following problem, when you do
  `./gradlew clean build`

  ```
  [Request processing failed; nested exception is  java.lang.IllegalStateException: No instances available for localhost] with root cause

  java.lang.IllegalStateException: No instances available for localhost

  ```

  It was because you missed one in the application's
  `application.properties` file. The `application.properties`
  file of the test in theory does not need to be changed.

  ```
  registration.server.endpoint=http://registration-server
  ```

- *When I deploy the app in the PCF, I get the following error
  It was because I was running the apps with config server
  bindings in the PCF.

  ```
  2020-04-09T13:08:24.11+0000 [APP/PROC/WEB/0] OUT Caused by: java.lang.NoClassDefFoundError: org/springframework/cloud/config/client/ConfigServicePropertySourceLocator
  ```

# Circuit breaker

## Talking points

-   The circuit breaker prevents the calling service from
    sending more traffice to the callee service

## Tips

-   The console for the evans is "login.sys.evans.pal.pivotal.io"

## References

-   [Circuit breaker diagrams](https://github.com/Netflix/Hystrix/wiki)
-   [Hystrix dashboard](https://github.com/Netflix-Skunkworks/hystrix-dashboard/wiki)

## Test locally

- commands at the local machine

- You can clean up the local databases using the following
  commands which is described in the "distributed system lab".
  Otherwise, create a new user will result in duplicate key,
  which is OK.

```
mysql -uroot < databases/create_databases.sql
./gradlew devMigrate testMigrate
```

```
// create account
curl -i -XPOST -H"Content-Type: application/json" localhost:8083/registration -d'{"name": "Pete"}'
curl -i localhost:8083/accounts?ownerId=1

// create projects
curl -i -XPOST -H"Content-Type: application/json" localhost:8083/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"
curl -i -XPOST -H"Content-Type: application/json" localhost:8083/projects -d"{\"name\": \"Project B\", \"accountId\": \"1\"}"

// ***You can start from here if you are not recreating tables***

// create allocation assuming projectId is 1 (which is from Project A)
curl -i -XPOST -H"Content-Type: application/json" localhost:8081/allocations/ -d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

// Stop registration server

// create allocation assuming projectId is 2 (which is from project B)
// this should fail
curl -i -XPOST -H"Content-Type: application/json" localhost:8081/allocations/ -d"{\"projectId\": \"2\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

// create allocation assuming projectId is 1 (which is from project A)
// this should succeed
curl -i -XPOST -H"Content-Type: application/json" localhost:8081/allocations/ -d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"
```

- You should see the logging message like following:

```
2020-02-20 21:44:23.806  INFO 22098 --- [nio-8081-exec-2] i.p.p.tracker.allocations.ProjectClient  : ---> getProject(2)
2020-02-20 21:44:23.813  INFO 22098 --- [nio-8081-exec-2] i.p.p.tracker.allocations.ProjectClient  : ---> getProjectFromCache(2)
2020-02-20 21:44:34.878  INFO 22098 --- [nio-8081-exec-3] i.p.p.tracker.allocations.ProjectClient  : ---> getProject(1)
2020-02-20 21:44:34.880  INFO 22098 --- [nio-8081-exec-3] i.p.p.tracker.allocations.ProjectClient  : ---> getProjectFromCache(1)
```

- REST commands at PCF with evans

```
// create user and account
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.apps.evans.pal.pivotal.io/registration -d'{"name": "Pete"}'

curl -i registration-pal-sang-shin.apps.evans.pal.pivotal.io/accounts?ownerId=1

// create 2 projects
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.apps.evans.pal.pivotal.io/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"

curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.apps.evans.pal.pivotal.io/projects -d"{\"name\": \"Project B\", \"accountId\": \"1\"}"

// create allocation assuming projectId is 1 and userid is 1
curl -i -XPOST -H"Content-Type: application/json" allocations-pal-sang-shin.apps.evans.pal.pivotal.io/allocations/ -d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

// create backlog assuming projectId is 1 and userid is 1
curl -i -XPOST -H"Content-Type: application/json" backlog-pal-sang-shin.apps.evans.pal.pivotal.io/stories -d"{\"projectId\": 1, \"name\": \"Find some reeds\"}"


// keep creating allocation assuming projectId is 1 and userid is 1
while true; sleep .3; do curl -i -XPOST -H"Content-Type: application/json" allocations-pal-sang-shin.apps.evans.pal.pivotal.io/allocations/ -d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}";  done;
```


- How to start and stop mysql on Mac

  ```
  brew services start mysql
  brew services list
  brew services stop --all
  brew services cleanup
  ```

## Trouble-shooting

- *When performing local testing, I experience the following problem

```
java.lang.NoSuchMethodException: class io.pivotal.pal.tracker.allocations.ProjectInfo class io.pivotal.pal.tracker.allocations.ProjectClient.getProjectFromCache(long,class java.lang.Throwable)
        at io.github.resilience4j.fallback.FallbackMethod.create(FallbackMethod.java:92) ~[resilience4j-spring-1.2.0.jar!/:1.2.0]
        at io.github.resilience4j.circuitbreaker.configure.CircuitBreakerAspect.circuitBreakerAroundAdvice(CircuitBreakerAspect.java:110) ~[resilience4j-spring-1.2.0.jar!/:1.2.0]
```

  It was because I did not provide the `Throwable cause` argument

  ```
    public ProjectInfo getProjectFromCache(long projectId, Throwable cause) {
        logger.info("Getting project with id {} from cache", projectId);
        return projectsCache.get(projectId);
    }
  ```

## Challenge questions (Circuit breaker lab)

- Can @CircuitBreaker command can be chained?
- When is the suitable use case where circuit breaker can be used?
  Can it be used for non-idempotent operations?
- How would you handle a case where dependency service simply
  timed out and the calling service's threads get depleted
  (as shown in the [3rd figure in the https://github.com/Netflix/Hystrix/wiki](https://github.com/Netflix/Hystrix/wiki))?


# Securing Distributed Application

## Talking points

- [OpenID Connect](https://hackernoon.com/demystifying-oauth-2-0-and-openid-connect-and-saml-12aa4cf9fdba)

```
OpenId Connect is a set of defined process flows for “federated authentication”. OpenId Connect flows are built using the Oauth2.0 process flows as the base and then adding a few additional steps over it to allow for “federated authentication”.
```

- [OAuth2 and OpenID Connect](https://blog.runscope.com/posts/understanding-oauth-2-and-openid-connect)

```
The OAuth 2.0 Framework describes overarching patterns for granting authorization but does not define how to actually perform authentication. The application using OAuth constructs a specific request for permissions to a third party system - usually called an Identity Provider (IdP) - which handles the authentication process and returns an Access Token representing success. The IdP may require additional factors such as SMS or email but that is entirely outside the scope of OAuth. Finally, the contents and structure of that Access Token are undefined by default. This ambiguity guarantees that Identity Providers will build incompatible systems.

Luckily, OpenID Connect or OIDC brings some sanity to the madness. It is an OAuth extension which adds and strictly defines an ID Token for returning user information.  Now when we log in with our Identity Provider, it can return specific fields that our applications can expect and handle. The important thing to remember is that OIDC is just a special, simplified case of OAuth, not a replacement. It uses the same terminology and concepts.
```

## How to get started with security lab

```
[Save your changes to another branch first}
-   git checkout -b wip-branch
-   git add -p (Don't use git add .)
-   git commit -m “work in progress in my lab”
-   git push origin wip-branch --tags

[Then do the following}
-   git checkout main
-   git reset --hard security-solution
-   (change manifest files of all 4 applications to reflect
    correct domain and route in manifest file like:)
        - route: pal-tracker-sang-shin.apps.evans.pal.pivotal.io

[Create service discovery service]
-   cf create-service p-service-registry standard tracker-service-registry

[Do the security lab]
-   (Do the lab work)
-   git add-commit -m “end of security lab”
-   git push origin main --force  (to force the remote main
          to sync with local main - do not to this in production! :-))
```


## Demo steps

-   Use `security-solution` as base code
-   Change 4 manifest files to reflect correct route
-   Make sure to create services manually at PCF

## Trouble-shooting

- *I use security-solution project and run the following locally
  after successfuly got the token for auth server.  (Answer:
  it was because I was running the application using Spring Boot
  services tab.  Using boorun with --parallel works.)

```
 workspace/pal-tracker-distributed - main > curl localhost:8083 -H"Authorization: Bearer b78147e6-75f6-4a22-8498-26efe95d5dc6"
<!doctype html><html lang="en"><head><title>HTTP Status 500 – Internal Server Error
```

  I can see registration-server log has the following, so
  somehow registration-server thinks that the caller is
  not authenticated.

```
org.springframework.web.client.HttpClientErrorException: 401 null
```

  But running on PCF works. *Even if it sends incorrect token,
  it still works? Actually changing jti value works but chaning
  real token value results in 500 response

  server.gradle has the following which needs to be picked
  up by the servers when they run


  ```
  bootRun.environment([
    "APPLICATION_OAUTH_ENABLED": true,
    "SECURITY_OAUTH2_CLIENT_CLIENT_ID": "tracker-client",
    "SECURITY_OAUTH2_CLIENT_CLIENT_SECRET": "supersecret"
  ])
  ```

-  (Same as above) Just found out why I had failure on my oauth2 testing.  I was running the apps using Spring Boot dashboard, which fails to read the security property values from the build.gradle.
But why  doesn’t IntelliJ honor the setting “Delegate IDE build/run to gradle”?

- *I am experiencing the following problem on PCF (using PWS's p-dentity/pal). Somehow this problem occurs only in PWS and does
  not occur on evans.  (Answer) It is because on evans,
  when you bind your
  app with sso service, it correctly configures the client-credentials while in PWS, it configures with authorization-code
  credential

  ```
  pal_user@instructor-demo-sang-large:~$ curl -k "https://pal.login.run.pivotal.io/oauth/token"
  -i -u "75216cc6-2d28-4990-89c5-c0572dc166a0:4a327ca2-2c25-4a64-a4cf-e29fe545c90b"
  -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded'
  -d 'grant_type=client_credentials&response_type=token'
  HTTP/1.1 401 Unauthorized
  ```

- When running integration testing via `./gradlew clean build`,
  tell students to ignore the following

  ```
  com.sun.jersey.api.client.ClientHandlerException: java.net.ConnectException: Connection refused (Connection refused)


  com.netflix.discovery.shared.transport.TransportException: Cannot execute request on any known server
  ```

## Tips

-  Getting token from local authorization server

   ```
   curl 'http://localhost:8999/oauth/token' -i -u 'tracker-client:supersecret' -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=client_credentials&response_type=token&token_format=opaque'
   ```

-  Getting token from UAA (using Evans)

   ```
   cf env tracker-registration
   curl -k https://p-identity.login.sys.evans.pal.pivotal.io/oauth/token -i -u <client-id>:<client-secret> -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=client_credentials&response_type=token'
   ```

-  How to access your allocation server with security in PCF

   ```
   curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.apps.evans.pal.pivotal.io/registration -H"Authorization: Bearer <token>" -d'{"name": "Pete"}'
   ```

-  Getting token from local authorization server

   ```
   curl 'http://localhost:8999/oauth/token' -i -u 'tracker-client:supersecret' -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=client_credentials&response_type=token&token_format=opaque'
   ```

- Perform operations locally using locally acquired token

	```
	// create account
	curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer 82e595e2-62c2-4581-92d1-fe104acbc5b2" localhost:8083/registration -d'{"name": "Pete"}'
	curl -i -H"Authorization: Bearer 82e595e2-62c2-4581-92d1-fe104acbc5b2" localhost:8083/accounts?ownerId=1

	// create projects
	curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer 82e595e2-62c2-4581-92d1-fe104acbc5b2" localhost:8083/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"

	// create allocation assuming projectId is 1
	curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer 82e595e2-62c2-4581-92d1-fe104acbc5b2" localhost:8081/allocations/ -d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"
	```

- Perform operations in PCF using remotely acquired token

   ```
   // get a token from UAA
   cf env tracker-registration
   curl -k https://p-identity.login.sys.evans.pal.pivotal.io/oauth/token -i -u <cliend-id>:<client-secret> -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=client_credentials&response_type=token'

   // create accounts
   curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer <token>" registration-pal-sang-shin.apps.evans.pal.pivotal.io/registration -d'{"name": "Pete"}'

   // create projects
	curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer <token>" registration-pal-sang-shin.apps.evans.pal.pivotal.io/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"

   // create allocation assuming projectId is 1
   curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer <token>" http://allocations-pal-sang-shin.apps.evans.pal.pivotal.io/allocations/ -d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

   ```

### Useful presentations on OAuth2

-  [OAuth2 overview presentation](https://www.slideshare.net/SangShin1/spring4-security-oauth2?qid=2163e6e6-ae99-48b0-afcc-88380b8724d8&v=&b=&from_search=1)

-  [OAuth2 in cloud native environment presentation (slides 7 to 37)](https://www.slideshare.net/WillTran1/enabling-cloud-native-security-with-oauth2-and-multitenant-uaa?qid=2c77ae8e-b2d5-4319-baad-1cd1eb8fec42&v=&b=&from_search=1)

-  [OAuth and OpenID Connect](https://www.youtube.com/watch?v=996OiexHze0&ab_channel=OktaDev)
-  [Explain it to Me I'm 5: OAuth2 and OpenID](https://www.youtube.com/watch?v=5th6CSQTdpM&ab_channel=SpringDeveloper)


# Config Server

## Talking points

-   *Is this lab dependent on security lab? Yes, you can do this
    lab without doing security lab
-   ?? When to use branch?
-   Fault tolerance
-   Confguration drift

## Tips

-   Use the following command for creating config-server instance (PWS)

    ```
    cf create-service ${CONFIG_SERVER_SERVICE_NAME} ${PLAN_NAME} tracker-config-server \
    -c "{\"git\": {\"uri\": \"https://github.com/${YOUR_GITHUB_USERNAME}/tracker-config.git\", \"label\":  \"main\"}}"
    ```

    ```
    cf create-service p-config-server standard tracker-config-server \
    -c "{\"git\": {\"uri\": \"https://github.com/sashinpivotal/tracker-config.git\", \"label\": \"main\"}}"
    ```

-   After getting a token, send refresh post

    ```
    curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer <token>" registration-pal-sang-shin.apps.evans.pal.pivotal.io/actuator/refresh -d"{}"
    ```

## Trouble-shooting

- *If you experience when you send refresh request, it is because
  you did not send -d

  ```
  HTTP/1.0 411 Length Required Content-Type: text/html; charset=UTF-8 Referrer-Policy: no-referrer
  ```

- *Setting the management include thing in the manifest files
  with just * fails - use `"*"` not just `*`

  Now instruction actually uses concrete set of endpoints like

  ```
  management.endpoints.web.exposure.include=info,health,metrics,circuitbreakers,env
  ```

- *The extra exercise needs to use @RefreshScope, which results in
  "unresolvable symbol" error

  I need to add the following to the rest-support's build.gradle

  ```
  compile "org.springframework.cloud:spring-cloud-context:2.0.0.RELEASE"
  ```


## Challenge questions (on config server lab)

-   It is a good practice to save security-sensitive data such as
    passwords in the config server? If not, what can we do?

-   What happens when a config server is not available?

-   Is it a good practice to maintain configuration data in a
    single repository for multiple environments?

# Ending the course

```
A few words regarding Course materials after the training:

- The course materails in the http://courses.education.pivotal.io will
  be available at the minimum for a few months from today
  (The ePub from MyLearn will be available in "indefinite" basis)
- The "evans" PCF foundation will be destroyed after the class
- The Remote desktop will be also destroyed after the class
  (Make sure you push your changes to your Github before leaving the class.)
- The slack channel will be available after the training. It
  will be "archived" meaning you will be able to read but
  will not be able to post
- Bill and myself can be reached via email after the training
  if you have any questions on course materials
```


-   (From Charles LeRose)

    ```
    As we head toward the end of this class, I’d like to repeat that the course material is available to you indefinitely (the web content with the labs, on the ‘courses’ site.)  You will also continue to have access to this Slack channel.  (Be sure to remember you passwords for these.)  And I encourage you to join the #alumni channel here too.
‘Evans’ will be torn down after the class ends, as will your remote desktops that we provided.
Hopefully, you all have access to some sort of developer sandbox Cloud Foundry foundation.  If not, or if your sandbox lacks some of the services on ‘Evans’, you can use a Cloud Foundry foundation called Pivotal Web Services at  run.pivotal.io.  This is a for-pay service, but creating an account is free, and it comes with quite a bit of free service credit to get started.  There will be a few differences from Evans, such as the API endpoint, so keep your eye out for those.
    ```

- (From Bill Kable)

```
Pivotal EDU offerings
- List of certifications: https://tanzu.vmware.com/training/certification
- List of Product Trainings: https://tanzu.vmware.com/training
- List of Platform Acceleration Labs Trainings: https://tanzu.vmware.com/platform-acceleration-lab
```

- [Survey](https://www.surveymonkey.com/r/3GKNTN8?coid=pri)

# Retro

- Create a retro from https://retros.cfapps.io/

https://retros.cfapps.io/retros/pal-ford-sep-2020

```
Got it. My team is using parabol.co for our retros and I like it a lot more than the cfapps retro tool . Might be worth trying sometime!
```

# Misc

```
[Michael Barinek](https://www.linkedin.com/in/barinek/)
```

# Pre-class email

```
Hello, folks

A few things to let you know before we start a new class
("Master class for Java developers") tomorrow morning 
(Monday May 17th, 9AM CST).
 
1. In this class, you are going to use virtual desktop, 
   which is accessible through a browser.
   And a link is provided to each of you. 
   (Please make sure to click the one that is assigned to you.)
   The username/password is same for everyone and it is
   ubuntu/keepitsimple - all lowercase.
  
  https://aanand-shah-349803974.vdi.pal.pivotal.io/
  https://davon-davis-349803974.vdi.pal.pivotal.io/
  https://gregory-brothers-349803974.vdi.pal.pivotal.io/
  https://joseph-gerstenberger-349803974.vdi.pal.pivotal.io/
  https://joshua-schoonover-349803974.vdi.pal.pivotal.io/
  https://joshua-white-349803974.vdi.pal.pivotal.io/
  https://majid-lowe-349803974.vdi.pal.pivotal.io/
  https://richard-elerick-349803974.vdi.pal.pivotal.io/
  https://robert-payne-349803974.vdi.pal.pivotal.io/
  https://robert-scalzo-349803974.vdi.pal.pivotal.io/
  https://sidney-hall-349803974.vdi.pal.pivotal.io/
  https://vincent-logiudice-349803974.vdi.pal.pivotal.io/
  https://varadarajan-vivek-349803974.vdi.pal.pivotal.io/  
  
  The virtual desktop provides everything that is needed 
  for the class:
  
  - Course materials (click the "Link to Course Materials" icon)
  - IntelliJ, MATE terminal, MySQL, Browser, unzip, cf-cli, etc     
                
2. As for the cloud platform for application deployment, 
   we are going to use TAS (Tanzu Application Service).
   Please find TAS credential assigned to each of you.
   You will need just username, password, and API endpoint 
   when you log in to TAS. (Type "cf login" in a terminal window)
   The API endpoint is same for everyone and it is
   api.sys.evans.pal.pivotal.io

Aanand Shah, email=aanand.shah@austincc.edu, password=c6mkxeuy, username=aanand-shah-afc
Davon Davis, email=davon.davis@austincc.edu, password=c7xbt7x7, username=davon-davis-afc
Gregory Brothers, email=gregory.brothers@austincc.edu, password=sfbsfgyb, username=gregory-brothers-afc
Joseph Gerstenberger, email=joseph.gerstenberger@austincc.edu, password=5yhvgydn, username=joseph-gerstenberger-afc
Joshua Schoonover, email=joshua.schoonover@austincc.edu, password=2mg58p3w, username=joshua-schoonover-afc
Joshua White, email=joshua.white@austincc.edu, password=cy877mps, username=joshua-white-afc
Majid Lowe, email=majid.lowe@austincc.edu, password=yrf2hh3r, username=majid-lowe-afc
Richard Elerick, email=richard.elerick@austincc.edu, password=dvpfkvsc, username=richard-elerick-afc
Robert Payne III, email=robert.payne@austincc.edu, password=xc3nnfe2, username=robert-payne-afc
Robert P. Scalzo, email=robert.scalzo@austincc.edu, password=jypxfb5w, username=robert-scalzo-afc
Sidney Hall, email=sidney.hall@austincc.edu, password=225h2cx7, username=sidney-hall-afc
Vincent Renzo LoGiudice, email=vincent.logiudice@austincc.edu, password=c3v8nugt, username=vincent-logiudice-afc
Vivek Varadarajan, email=varadarajan.vivek@gmail.com, password=k3h89yd2, username=varadarajan-vivek-afc
 
3. You are going to use your personal GitHub account for pushing your code.
   If you don't have your personal GitHub account yet, please make
   sure to create one before coming to the class.
   
4. We are going to use the same Zoom and Slack channel (this channel) 
   we used for Core Spring class for the new class.
   
   https://VMware.zoom.us/j/92444949782?pwd=UTBwWmJwTjcvTU5zNi9CR0dCcWNQdz09
   
We will go over these things tomorrow morning.  But please feel free to
try them out.

If you have any questions before the class, please 
don’t hesitate to contact instructor team through either 
this Slack channel or email (sashin@vmware.com, bkable@vmware.com).

Thanks.  See you tomorrow.
 
-Instructor Team (Bill, Sang, Carlton, Sam, Omeed) 

```

-  Ford

```
Hello, folks
 
This is Sang Shin from VMware.  My colleague, Bill Kable, and myself
are two instructors for the next week’s class.

A few things to let you know before the pre-class meeting today.
(We will go over all these during the pre-class meeting – 
Slides for the pre-class meeting is also attached for your reference.)
 
1. Please find Virtual Desktop link that is assigned to each of you. 
   (Please make sure to click the one that is assigned to you.)
   The username/password is same for everyone and it is
   ubuntu/keepitsimple.
  
   https://bkable-349803962.vdi.pal.pivotal.io/
   https://sashin-349803962.vdi.pal.pivotal.io/
   https://sgoli3-349803962.vdi.pal.pivotal.io/
   https://vjakka-349803962.vdi.pal.pivotal.io/
   https://mjira-349803962.vdi.pal.pivotal.io/
   https://skaruman-349803962.vdi.pal.pivotal.io/
   https://pkotari-349803962.vdi.pal.pivotal.io/
   https://okyrylen-349803962.vdi.pal.pivotal.io/
   https://cleeman-349803962.vdi.pal.pivotal.io/
   https://cmarin27-349803962.vdi.pal.pivotal.io/
   https://smata5-349803962.vdi.pal.pivotal.io/
   https://mmayoral-349803962.vdi.pal.pivotal.io/
   https://kpalakur-349803962.vdi.pal.pivotal.io/
   https://mrawat-349803962.vdi.pal.pivotal.io/
   https://msanc266-349803962.vdi.pal.pivotal.io/
   https://rsudars3-349803962.vdi.pal.pivotal.io/
   https://jtellode-349803962.vdi.pal.pivotal.io/
   https://syu4-349803962.vdi.pal.pivotal.io/      
                
2. Please find PCF (TAS) credential assigned to each of you.
   You will need just API endpoint, username, and password 
   when you log in to PCF(TAS). 
   
   The API endpoint is the same for everyone and it is
   https://api.sys.evans.pal.pivotal.io

Sunil Kumar Goli <sgoli3@ford.com>: username: sgoli3-ford, password: weq32yn6
Venkat Jakka <vjakka@ford.com>: username: vjakka-ford, password: p5wbjgjw
Matthew Jira <mjira@ford.com>: username: mjira-ford, password: bngpm32k
Sai Subhash Karumanchi <skaruman@ford.com>: username: skaruman-ford, password: e2ymbwuj
Praveen Kotari <pkotari@ford.com>: username: pkotari-ford, password: je26uqbv
Oleg Kyrylenko <okyrylen@ford.com>: username: okyrylen-ford, password: g9ndwse9
Cody Leeman <cleeman@ford.com>: username: cleeman-ford, password: mrbfh8u3
Carlos Marin <cmarin27@ford.com>: username: cmarin27-ford, password: ytepj75p
Shankar Rao Mata <smata5@ford.com>: username: smata5-ford, password: 7h3m8gme
Miguel Angel Mayoral Bustos <mmayoral@ford.com>: username: mmayoral-ford, password: mgdyhvbd
Krushna Palakurti <kpalakur@ford.com>: username: kpalakur-ford, password: 7bu75nyg
Manoj Trilok Rawat <mrawat@ford.com>: username: mrawat-ford, password: p6559v3g
Macarena Sanchez Casado <msanc266@ford.com>: username: msanc266-ford, password: juttxhhk
Rao Sudarshan <rsudars3@ford.com>: username: rsudars3-ford, password: 6b65rpmd
Juan Tello del Rosal <jtellode@ford.com>: username: jtellode-ford, password: nhtvfjgt
Sharon Yu <syu4@ford.com>: username: syu4-ford, password: knh79fdh
 
3. Another email inviting each of you to join the class Slack channel 
   (“ford-lol-june-2021-cnd” under “palexternal.slack.com”) was sent out
   this morning.  Please accept it.

4. The Zoom link for today’s pre-class meeting and 
   next week’s class (same link) is the following:
 
   https://VMware.zoom.us/j/91408289978?pwd=Qmpmd3o2MHNEOUxhUGxNNUZ3bUQwQT09

5. If you have any questions before the class, please don’t hesitate to contact me or Bill through either class Slack channel mentioned above or email (sashin@vmware.com, bkable@vmware.com).

Thanks.  See you soon.
 
-Sang & Bill
```

