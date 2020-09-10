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



# Before the cohort

- We can send the following message before cohort gets started
  with email subject `PAL for Developer class - a few things to communicate`
  
  ```
  Hello,
  
  My name is <Instructor name>. I am one of the several instructors 
  from Pivotal (now part of VMWare) of this PAL course. A few
  things to communicate before we start.
      
  - Please make sure you can access the course 
    contents from the following site. If this is
    your first time taking a course from Pivotal,
    you will have to "sign up" first.
  
      http://courses.education.pivotal.io 
  
  - I assume everyone received slack channel message from
    PAL-Cloud-OPS team which provides individual 
    PCF (PAS) credentials like following:
  
    Hi <Your name>, welcome to <Company>. The below 
    information will be useful throughout the course to 
    access materials and infrastructure. View discussion 
    about your course in #<slack-channel>.
  
       Cohort ID: <Cohort ID>
       PCF Foundation API:  api.sys.evans.pal.pivotal.io
       PCF Org: <your own PCF org>
       PCF Username: <your own email address>
       PCF Password: <your own PCF password>
     
    (The above credentials can be also accessible from
    http://courses.education.pivotal.io - there is link
    by the PAL Developer course entry)
  
    Once everyone is onboard, all our technology-related 
    communication will be through our #liveon-apr-2020-cnd-4 
    slack channel during the course. (Zoom chat will be used 
    only occasionally for logistics related issues.)
  
    BTW, if this is your first time accessing Slack channel, 
    please create an account via http://palexternal.slack.com
    using your email address.
    
  - Create a personal GitHub account if you don't have one.
    (Using company GitHub is not recommended.)

  - We are going to use IntelliJ (Community version) and
    Gradle in our labs.  If you are new to these, please feel
    free to explore the basic usage of them before coming
    to the class.
   
  - Finally, please make sure you can access the Remote Desktop 
    instance using the provided URL and password. All our lab 
    work will be done through the remote desktop.  See if
    you can open IntelliJ and terminal window.
      
  If you have any questions, please feel free to respond
  to this email at any time.
  
  ```

# Getting started (logistics)

- A student can access their slack channel message by
  opening slack or go to `palexternal.slack.com` 
  
- In order to see the self-evaluation, please go to
  [https://registration.education.pivotal.io/admin/cohorts](https://registration.education.pivotal.io/admin/cohorts)
  
- Brad send out the following information to the class channel
  (Make sure to set the Cohort Id and course Id)

  ```
  Cohort Information:
  Cohort Id: xxxxxx
  Course Content: https://courses.education.pivotal.io/c/xxxxx
  MeerKats password: keepitsimple
  Parrit: https://parrit.cfapps.io/bostonma-aug-2019-cnd (password:  keepitsimple)
  ```
  
- Mike G sent out the following

  ```
  Cohort Information:
  Machine username/password: pivotaluser/keepitsimple
  Cohort Id: 349803460
  Course URL: https://courses.education.pivotal.io
  PCF API endpoint: https://api.sys.evans.pal.pivotal.io
  PCF web UI: https://login.sys.evans.pal.pivotal.io
  ```
  
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

## Demo steps for a particular topic

-   If you want to start "topic" lab from "topic-start", 
    follow the steps mentioned below 
    
```
-   git checkout master 
-   git reset --hard <topic-start>
-   change manifest files to reflect correct domain and route in manifest file like:
        - route: pal-tracker-sang-shin.apps.evans.pal.pivotal.io
-   Do the lab work
-   git add-commit -m “my work done”
-   git push origin master -f  (to force the remote master to sync with local master - do not to this in production! :-))
```

## Save "in progress" work in a personal branch

```
By the way, before you do the above step, if you need to save your current unfinished work into “work in progress” branch so that you can work on that on later time, you do the following:
-   git checkout -b wip-branch
-   git add .
-   git commit -m “work in progress in my lab”
-   git push origin wip-branch --tags
```

-   If you have created github repository with `README.md`, you
    will experience the following problem when you do 
    `git push origin master --tags`.
    An easy way out is `git push origin master -f --tags`

```
< workspace/movie-fun - master > git push
To https://github.com/sashinpivotal/movie-fun
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/sashinpivotal/movie-fun'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

- *When a repository is created with README file on, performing
  `git pull` results in the following error:
  
  ```
  < workspace/pal-tracker-distributed - master > git pull
  fatal: refusing to merge unrelated histories
  ```
  
  You can do the following to move forward.
  
  ```
  git pull --allow-unrelated-histories
  ```

-   If you want to go to a solution project while maintaining
    your code (??? Is this correct?)

```
- git checkout master
- git cherry-pick abort
- git cherry-pick <topic-solution-tag> and handle merge conflict
```

# Pair Programming

(Not relevant for LOL)

- Communicate what you do to your partner - if you are typing or
  moving your mouse without talking, you are doing a disservice 
  to your pair partner
- Use your mouse rather than using your finger

# Pair rotation

(Not relevant for LOL)

- Before the rotation, please do ensure both pairs 
  have code on their own github

- Mention this after `pal-tracker` lab and just before 
  `pal-tracker-distributed` (This is what Brad sent out)

```
@here This morning before we rotate pairs:
1. The other pair partner should create a Github repository for `pal-tracker`
2. git remote add other-origin <github repo url> 
3. git push --tags -f  -u other-origin master
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

# Meerkat

## Meerkat keyboard shortcuts

- [default keymap](https://resources.jetbrains.com/storage/products/intellij-idea/docs/IntelliJIDEA_ReferenceCard.pdf)

- Alt+Enter what is quick fix combination (Option+Enter for Mac)
- Alt+Insert for "generate" (CMD+N for Mac)
- Ctrl+N for "opening a class" (CMD+O for Mac)
- Ctrl+Shift+N for "open a file" 

# VDI

## Linux keyboard shortcuts

```
- Keyboard shortcut keys within Remote Desktop
  - ALT+F10 (maximizing window on and off)
  - ALT+Tab (move between windows)
  - ALT+F9 (minimize window)
  - SHIFT+CTRL+C (copying from termimal) 
  - SHIFT+CTRL+V (copying to the terminal)
  - CTRL+C (copying) 
  - CTRL+V (pasting)

- Keyboard shortcut keys within IntelliJ

  - CTRL+N (find class)
  - CTRL+Shift+N (find file)
  - ALT+Return (Quick fix)*
  - Double SHIFT (global search)
  - CTRL+SHIFT+Return (Complete current statement)*
  - F2, SHIFT+F2 (Go to next/previous error)*
  - CTRL+SHIFT+F10 (run the app/test)*
  - SHIFT+F10(rerun the app/test)*
  - CTRL+ALT+V (extract return value into a local variable)*
  - CTRL+SHIFT+T (go to target/test code)*
  - CTRL+ALT+Left (back - Does not work on Mac - I have to set it myself manually)*
  - CTRL+ALT+Right (forward - Does not work on Mac - I have to set it myself manually)*
  - ALT+Insert (Generate) 
```

## Misc. tips

- You can bookmark the course webpage by right clicking ...
  on the top-right corner and select bookmark
- *If you enabled two-factor authentication, you will experience
  the following. Easiest fix is to disable it.

  ```
  pal_user@instructor-demo-sang-large:~/workspace/pal-tracker- distributed$ git push origin master -f
  Username for 'https://github.com': sashinpivotal
  Password for 'https://sashinpivotal@github.com': 
  remote: Invalid username or password.
  fatal: Authentication failed for 'https://github.com/sashinpivotal/ pal-tracker-distributed/'
  ```
  
  It is because as mentioned [here](https://stackoverflow.com/questions/17659206/git-push-results-in-authentication-failed)
  
  ```
  If you enabled two-factor authentication in your Github account you  won't be able to push via HTTPS using your accounts password. Instead  you need to generate a personal access token. This can be done in the  application settings of your Github account. Using this token as your  password should allow you to push to your remote repository via  HTTPS. Use your username as usual.
  ```
  
- In the browser, you can bookmark it but you have 
  to select "show bookmark bar" to see it

## Lab related

- Getting actuator metrics from the browser is not formatted
  But using curl command with json_pp works
- *I could not see resilience metrics somehow - you have
  to make a call that exercises the circuit breaker 
  
## ubuntu

- vim or nano are already there as an editor
- Visual Studio is another option
- bash shell - you can check with echo "$SHELL"
- you have to create ~/.bash_profile

# Zoom related tips and tricks

- The host role should be played by an instructor who has the
  least amount of work on that day
- The activities host plays include
  - admit participants (this is very important)
  - create breakout rooms
  - assign "ask for help" request to other co-hosts
    (unfortunately co-hosts do not receive "ask for help" notifications)
  - occasionally "lower all hands" 
  - occasionally "mute" everyone
- The first time, you become the host, you should
  - assign other instructors as co-host
  - create a teacher's lounge - this can be done only before you open breakout rooms
- If the host gets disconnected from the Zoom session, for
  whatever reason, the host role will be automatically transfered to
  another co-host
  - host role has to be manually switched back to original host
    by the current host

# Assignment Submission
   
## Talking points

- Note that whenever student submit the lab result, 
  they always have to go to the `assigment-submission` directory
  
- Make sure to change the email address

- CND/CNA students should ignore `waveland` section

  
# Building a Spring Boot App (lab #1)

## Talking points

- Spring related
	- Talk about dependency injection - what it is and why
	
- lab project
	- Mention that the `pal-tracker` directory is under `workspace` directory
	- You are going to create `pal-tracker` repository in your Github
	  and sync up with local `pal-tracker` project using `git remote add origin <URL>`
	  
- PCF related
	- You are going to deploy the app to the PCF manually in this lab 
	  using `cf push` command:
	  later on, you will
	  deploy the app using a CI/CD pipeline

## How to set up `pal-tracker` Git project

- Create personal Github account if you have not done so yet
  
- Steps to follow
  - Create a personal GitHub account (if you don't have one yet)
  - Create "pal-tracker" repository 
  - Make sure you have unzipped the `pal-tracker.zip` under `workspace` directory
  - Go to local `workspace/pal-tracker` directory
  - Execute `git remote add origin <url>`
  - Execute `git push origin master --tags`


## Bootstrap the application

- ?? How do you compare different branches and tags using Github?
  (Use IntelliJ instead)

- If the test works at the command line but fails within 
  IntelliJ using bootRun task, make sure you 
  set the Gradle Test Runner under setting 
  (This is now automatically set in recent version of IntelliJ)

- If you are using STS, try to verify your yml file syntax
  with `http://www.yamllint.com/`
  
- *IntelliJ - I don't find refresh menu option, and I don't
  see Gradle menu bar option either - I had to
  close and re-import the project to see Gradle menu 
  bar. - this is to use refresh icon from the Gradle bar
  menu on the right.
  
- ??What is `buildscript` closure for?

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

## Challenge questions

- What the purpose of using "gradle wrapper"?
- What is a fat jar?  How does Spring Boot creats one?
- What is 12 factor app?  (Google it)
- One of the features of Spring Boot (actually through the Spring Boot
  Maven/Gradle plugin) is to create a fat jar that contains everything
  including Tomcat.  Among the 12 factors, which factor is relevant to
  creating and deploying the same fat jar over different deployment
  environment?
- How does Spring Boot helps with dependency management?
- What does @SpringBootApplication do? What is it made of?
- Why we use random route in our lab?
- Try the following commands
  
```
cf target
cf apps
cf app pal-tracker
cf routes
cf help -a
```

	
## Challenge exercise

-  Create a Person bean which has name and age fields
-  Create CommandLineRunner that displays the name and age
   of the person when application gets started

  
# Configuring an App
  
## Challenge questions

- Do we have to do “cf restage <app-name>” when we set a 
  new environment variable in PCF?
- What could be use cases where you will have to do 
  “cf restage” (as opposed to “cf restart”)?
- (Related question to the above) What are the differences 
  among 3 different ways of deploying an application 
  on PCF - "pushing", "restaging", and "restarting"?
- What are the environment variables that PCF automatically
  create for your application instance?
- Do "cf ssh pal-tracker" and display the value of 
  CF_INSTANCE_INDEX environment variable
  using "echo $CF_INSTANCE_INDEX"
- What are the examples of PCF log types? (Google “PCF log types”)
- Try to use “create-app-manifest” command to capture 
  the metadata of your running app into a file and try 
  to use that file to deploy the application
- If you remove "random-route: true" from your manifest.yml 
  file and then do "cf push", will it work? Why?
- When do you want to use `@ConfigurationProperties` annotation
  as opposed to `@Value` annotation?

## Challenge exercises

- Modify the code so that you are using 
  `@ConfigurationProperties` annotation
  as opposed to `@Value` annotation

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

## Slack channel tips

```
Great (concise yet to the point) presentation on 12 factors:  https://content.pivotal.io/slides/the-12-factors-for-building-cloud-native-software
```

## Trouble-shootings

- The document does not include instruction to remove compile
  errors on `EnvController` before it says to run the app

- *The following code will fail because Spring looks for
  a bean that is a type of String but it is not there.
  
  ```
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

- Why using environment variables is preferred over using property
  files?  For example, setting database credentials for different
  environments(dev, testing, staging, production, etc)?
- We covered several factors so far. What are those?
  - factor 1 - one codebase many deploys
  - factor 2 - explicit declaration of dependencies using Gradle
  - factor 3 - use environment variables for providing different
               property values for different environments   
  - factor 10 - dev/production parity - creating a fat jar
  - factor 11 - logs
  
# Deployment Pipelines

## Talking points (used by Mike G.)

- Why we do this lab before we write complete code 
   - deloyment is hard, we want minimum complication
   - get deployment process taken care of in the earlier stage
     of project life-cycle 
   - cannot solve process issues with technology
   
- Github Actions
   - concept is important, we don't care which CI tool you use

- What CD mean to you?
   - deployment to production should be a business decision 
     not an Eng decision (meaning it should be always 
     `ready to be deploy'able to production`
   - depployment to prod is risky, user segregation
   - ??github example, users, cost vs risk, regulartory constraint

- Use instructor slide to talk about pipeline
  
- Environment set-up in the pipeline (in the Github Actions)

- Why you do not want to do "cf push" yourself? 
  (many org do not allow cf push)
  (jar creation issue - we want to create jar file just once
  and use it in multiple enviroments)
  (jar versioning - in the form of release - is possible via CICD tool)
  (buildpack has nothing to do with creating jar)

## Wrap-up

- Carl discusses "pipeline.yml" (too much is hidden) vs 
  "Bash script" (more control, easier to understand what goes on)

## Tips

- Example Github Actions environment variables

  ```
  (when using PAL pcf endpoint)
  CF_API_URL https://api.sys.evans.pal.pivotal.io
  CF_ORG sashin.pivotal.io
  CF_SPACE sandbox
  CF_USERNAME sashin@pivotal.io
  CF_PASSWORD xxxxxxxxxxx

  (when using PWS pcf endpoint)
  CF_API_URL https://api.run.pivotal.io
  CF_ORG sashin-org
  CF_SPACE development
  CF_USERNAME sashin@pivotal.io
  CF_PASSWORD xxxxxxxx
  ```
    
- In order to trigger Github Actions job without making code 
  change, you can

  ```
  git commit --allow-empty -m "start a new job"
  git push
  ```
  
  Or you can select failed action and select "Redo all jobs"
  
## GitHub Actions

- *I could not locate settings under my repository
  It was because I was looking at the wrong pal-tracker
  repository (PAL's) not sashinpivotal below
  
  ```
  https://github.com/sashinpivotal/pal-tracker
  ```
  
## Trouble-shooting
      
- *If everything worked fine in the 2nd phase but deployment
  fails.
  Manually pusing the app works. ?? accessing ./env results in 404
  It was because I was using wrong target
  
  ```
  The command "wget -P build/libs https://github.com/$GITHUB_USERNAME/pal-tracker/releases/download/$RELEASE_TAG/pal-tracker.jar" exited with 0.
  before_deploy
  0.00s$ echo "Deploying $RELEASE_TAG to Cloud Foundry"
  dpl_0
  1.74s$ rvm $(travis_internal_ruby) --fuzzy do ruby -S gem install dpl
  dpl.1
  Installing deploy dependencies
  dpl.2
  Preparing deploy
  pl.3
  Deploying application
  failed to deploy
  ```
  
## Extra lab exercise

- How do you deploy to a different environment using GitHub
  conditional statement

## Challenge questions on routing

- We know multiple routes can be assigned to an applicationh.
  Now can a route be assigned to multiple applications?
- Anybody knows what “blue-green-deployment” is?
- Speaking “blue-green deployment”, anybody can think of conceptual 
  steps you will take in PCF environment?
-   How can we control the ratio of the traffic between V1.0.1 (blue) 
    vs. V1.0.2 (green)?
-   Can a route exist without an application associated with it? 
    (See “cf routes” and “cf create-route” commands.)
-   What could be the use case of "cf create-route"?
-   When mapping or unmapping routes, do you have to restart
    or restage an application?
-   How can you delete all routes that are not associated with
    any apps?
-   Can you describe which PCF components are responsible for
    updating the routing table whenever a new instance is created
    or old instance gets destroyed?
    
## Challenge questions in the blud-green deployment
    
-   Is blue-green deployment suitable for major feature change?
-   What are the challenges for doing blue-green deployment?
    - What about table change - don't delete field, don't delete tables
    
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
      
# Spring MVC with REST endpoints

## Talking points

- Don't change the test code in this lab - that is the contract

- Demo how to remove compile errors also show what to do
  when there are two compile 
  errors in a single line - you have to fix the one inside first
     
- Make sure TimeEntry constructor with the correct naming - 
  otherwise you will have hard time reading test code
  
- The reason we have a TimeEntry constructor that does 
  not set id is because
  we want to simulate the repository behavior where id gets generated 
  by the persistence layer
  
- You can create an interface from a class - refactor->extract

  
### InMemoryRepositoryTest

- How to set the `id` field of `TimeEntry` when it gets created 
  without `id` argument?

  - You can create `currentId` field

- When creating a code for `list` method, IDE generates 
  `boolean` return type   
  instead of `List<TimeEntry>` - you need to manually
  change `boolean` to `List<TimeEntry>`
    
- In the list() test, IntelliJ gets confused when there 
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

- Show them how to compare code within IntelliJ
  
### TimeEntryController test

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
        MockHttpServletRequest request = new MockHttpServletRequest();
        RequestContextHolder.setRequestAttributes(new ServletRequestAttributes(request));
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

## Local testing

- *experience the following problem when testing TimeEntryApiTest's
  create and read tests

  ```bash
  No results for path: date
  com.jayway.jsonpath.PathNotFoundException: No results for path: date
  ```
  
  It was because fieldname and method name mismatch like following
  
  ```
    public LocalDate getLocalDate() {
        return date;
    }
  ```
  
  instead of
  
  ```
    public LocalDate getDate() {
        return date;
    }
  ```
  
- *Even if Gradle runner setting is done in IntelliJ, running the app
  directly within the IDE still results in the following error
  You should use "bootRun" task from the list of Gradle tasks.
  
  ```
  Caused by: java.lang.IllegalArgumentException: Could not resolve placeholder    
  'welcome.message' in value welcome.message"
  ```

## Challenge Questions

1. What are the differences between unit testing vs integration testing vs end-to-end testing?
1. In “pal-tracker” project, which tests are unit testing? integrating testing or end-to-end testing?
1. Can you do “integration” or “end-to-end” testing as part of CI/CD pipeline?
1. What are differences between `RestTemplate` vs `TestRestTemplate`?
1. From unit-testing standpoint, why is it a bad practice to create a dependency object inside your class using “new” keyword or even using factory (as opposed to getting it injected either through constructor method or setting method)?
1. What is the another way of creating InMemoryTimeEntryRepository bean other than using @Bean in the configuration class? What would be pros and cons of each approach?
1. What does SOLID (design principles) stand for?
1. What are the examples of “Open for extension Closed for modification” design principle in the “pal-tracker” project?
1. When do you want to use `@SpringBootTest` vs `@ContextConfiguration` for your integration testing that involves Spring application context? 
1. Why TimeEntryControllerTest code needs mocking while InMemoryTimeEntryRepositoryTesting code doesn’t?
1. What is the difference between stubbing and mocking? When do you want use stubbing over mocking and vice-versa?
1. What is the reason controller TimeEntryControllerTest code has “verify” method?
1. If you have classes in a tree structure (for example, Class A has dependencies of class B and C and class B has a dependency D, in other words, class A and B has dependencies while class C has no dependencies), which class do you want to do Unit testing and which classes you want to do integration testing?
1. What about a class that depends on backing services such as database? How will you perform the integration testing?
1. What happens to the in-memory data when the application instances come and go?
   
- In the case of testing respository's delete(..), why there is
  no training method? it is because respository's delete method
  returns void.

  ```
    @Test
    public void testDelete() {
        long timeEntryId = 1L;
        ResponseEntity response = controller.delete(timeEntryId);
        verify(timeEntryRepository).delete(timeEntryId);
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.NO_CONTENT);
    }
  ```
  
## Lab tips

- Use jq command to pretty-format the response

## Answers to challenge questions

- (How does verification work?)
  Mockito.verify(MockedObject).someMethodOnTheObject(someParametersToTheMethod);
  verifies that the methods you called on your mocked object are indeed called. 
  If they weren't called, or called with the wrong parameters, or called the 
  wrong number of times, they would fail your test.

- (Why you want to use verify method?)
  The correctness of the unit test of the target class is based on the
  fact that the mock object is called and returns the prescribed 
  value.  So if the mock object is not called, the correctness of
  the unit test is not guaranteed.  
  
## Challenge exercise

- For now, TimeEntryControllerTest is a unit test code, which does
  not use Spring context (and for a good reason).  Now suppose you 
  want to take advantage of Spring context - maybe you want to
  read property files using Spring's @TestPropertySource,
  for example -, how can you change the TimeEntryController.test?
  (Create a new file called TimeEntryController2.test and `@WebMvcTest` and `MockMvc`)
  
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

- Install of postman on meerkat

```
$sudo snap install postman
$postman&
```

- TDD presentation - https://www.youtube.com/watch?v=s9vt6UJiHg4

## Wrap-up discusson

- Discuss pros and cons of @Bean vs component scan
- Discuss pros and cons of using @Bean vs @Repository
- What is extra behavior of @Repository annotation provides
  to your code?

- *Brad went over the 12 factors - we covered 8 of
  12 factors so far
  
## Trouble-shooting

- If Json serialization does not work (TimeEntry from the client
  contains fields set with zero's), make sure you have
  getters in the TimeEntry class - 
  
# Database Migration

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
cf install-plugin -r CF-Community "open"
cf install-plugin -r CF-Community "mysql-plugin"
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

## Challenge questions

- Does database migration include data migration in addition to schema migration?
- Migration should keep backward compatibility - don't delete column, add a column instead

## Wrap-up

- (Dylan: went through migration script)
  - cf create-service-key
  - vcap-services, credhub-ref, but when you cf env, you will see
    username and password
  - jq command for parsing
- Went through format of the migration file
  - you cannot change the migration file - flyway
    keeps track of checksum - create a new one
- development vs production issue (Bill K)
  - do locally first

## Student questions

- Can ssh enabled per space basis?
  
## References

- [Migration strategies](https://github.com/pivotal-bill-kable/spring-cloud-flyway-migration-demo)
- [Migration strategies and best practices](https://www.talend.com/resources/understanding-data-migration-strategies-best-practices/)

# Spring JdbcTemplate

## Talking points

- (Bill K) create-service

### Challenge questions

-   What are the two conditions that need to be met before
    Spring Boot's auto-configuration create DataSource bean
    that represents MySQL? 
    (Answer: MySQL driver in the classpath and credentials)

-   So when we are running our pal-tracker app locally and in GitHub Actions 
    with database, we have to provide database credentials (as 
    environment variables in our lab but could be from property
    file) but we did not have to do that when we are running
    the same application in PCF.  How is it done?  
        
-   We know that when we are running pal-tracker app locally, Spring Boot
    auto-configures a `DataSource` bean from the environment-variable provided
    database credentials, which is then used to auto-configure `JdbcTemplate`
    bean.  Now when we deploy the same application to PCF, 
    somehow different `DataSource`
    bean gets auto-configured from database credentials from the VCAP_SERVICES.
    How does PCF do this?
    
    See [See the Auto-Reconfiguration section in this document](https://docs.run.pivotal.io/buildpacks/java/configuring-service-connections/spring-service-bindings.html#auto)
    
-   Suppose I have some VCAP_SERVICES environment variables that I need to read in my Spring Boot application, is there any helper utility? 

    (See the following for a clue https://stackoverflow.com/questions/50456365/how-to-inject-user-provided-vcap-services-in-spring-boot)
    
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

## Challenge Exercise

- The lab code shows DataSource bean is auto-configured by Spring Boot, meaning you don’t have to configure DataSource bean yourself. Hence the reason we can inject the auto-configured DataSource object into JdbcTimeEntryRepository through constructor injection. And we create JdbcTemplate object ourselves in that constructor.

Now Spring Boot auto-configures JdbcTemplate bean as well so there is no need for us to create a new JdbcTemplate object.  So challenge exercise is to refactor the code to use auto-configured JdbcTemplate bean instead of manually creating it yourself.  Verify that it works by creating a new TimeEntry.

## Misc

-   Regarding the usage of `useTimezone`

    [stackoverflow](https://stackoverflow.com/questions/7605953/how-to-change-mysql-timezone-in-a-database-connection-using-java)
    
    useTimezone is an older workaround. MySQL team rewrote the setTimestamp/getTimestamp code fairly recently, but it will only be enabled if you set the connection parameter useLegacyDatetimeCode=false and you're using the latest version of mysql JDBC connector. So for example:

   ```
   "SPRING_DATASOURCE_URL": "jdbc:mysql://localhost:3306/tracker_dev?user=tracker&useSSL=false&useTimezone=true&serverTimezone=UTC&useLegacyDatetimeCode=false",
   ```
   
- The `create(..)` method

   ```
    @Override
    public TimeEntry create(TimeEntry timeEntry) {
        KeyHolder generatedKeyHolder = new GeneratedKeyHolder();

        jdbcTemplate.update(connection -> {
            PreparedStatement statement = connection.prepareStatement(
                    "INSERT INTO time_entries (project_id, user_id, date, hours) " +
                            "VALUES (?, ?, ?, ?)",
                    RETURN_GENERATED_KEYS
            );

            statement.setLong(1, timeEntry.getProjectId());
            statement.setLong(2, timeEntry.getUserId());
            statement.setDate(3, Date.valueOf(timeEntry.getDate()));
            statement.setInt(4, timeEntry.getHours());

            return statement;
        }, generatedKeyHolder);

        return find(generatedKeyHolder.getKey().longValue());
    }
   ```

## Tips

1. Using curl and httpie for creating time-entry

```
curl -i -XPOST -H"Content-Type: application/json" pal-tracker-sang-shin.cfapps.io/time-entries/ -d"{\"projectId\": 1, \"userId\": 1, \"date\": \"2015-05-17\", \"hours\": 6}"
```

```
curl -i -XPOST -H"Content-Type: application/json" pal-tracker-sang-shin.apps.evans.pal.pivotal.io/time-entries/ -d"{\"projectId\": 1, \"userId\": 1, \"date\": \"2015-05-17\", \"hours\": 6}"
```

```
http post pal-tracker-sang-shin.cfapps.io/time-entries projectId=1 userId=1 date=2018-01-01  hours=20
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

1. *The following line gets red-colored. It was because
   build.gradle is not refreshed.
   

   ```
   import org.flywaydb.gradle.task.FlywayMigrateTask
   ```
   
   Maybe this is IntelliJ issue? Bill suggested
   to do 
   
   ```
   ./gradlew clean build
   ```
   
   and the IDE will fix it.
   

- *What is the reason we have the following code in the test?
  The purpose of this code is to clean up the `time-entries` table
  each time API testing is performed. Otherwise,
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
   

## Wrap-up talking points

-   Self-service
-   No need to set up database credentials
-   Correct DataSource bean automatically created 
    depending on where the application gets deployed

# Actuator

## Tips
   
- The META-INF/build-info.properties is under build/resources/main directory


   
## Talking points

- For /health value proposition, talk about the case "applicatio hang" - GC hang - CF does just port health check

## Trouble-shooting

- * HealthApiTest fails due the following reason even though 
  accessing the endpoint from a browser works fine. Why?
  It was because I reversed the up() and down() logic.

  ```
  org.junit.ComparisonFailure: expected:<[200]> but was:<[503]>
  ```

## Prometheus and Grafana

```
Prometheus and Grafana scripts I’ved used - they are using docker -
can be obtained from https://github.com/sashinpivotal/prometheus-grafana

If you don’t have docker installed on your machine, you can download and run prometheus and grafana individually from https://prometheus.io/download/ and https://grafana.com/grafana/download.  And you can use the same configuration files from the above website.
```

- Show how to create a dashboard using the new counter that was created

## Tips

- In order to set env variable

```
cf set-env pal-tracker MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE "*"
```

## Challenge question

- What is code smell in the following code in the `TimeEntryController`?
  (Does it follow Single Responsibility principle?) 
  What could be the solution? Do implement it if you know how to.

  ```
  @GetMapping
  public ResponseEntity<List<TimeEntry>> list() {
      actionCounter.increment();
      return new ResponseEntity<>(timeEntriesRepo.list(), HttpStatus.OK);
  }
  ```
      
## Challenge exercise

- Use AOP to increment the counter
  
# Scaling lab

- Auto-scaling lab, in the Recent History, you will see something

  ```
  Scaled up from 2 to 3 instances. Current HTTP Latency of 35.92ms is above upper threshold of 3.00ms.
  ```

- ?? When applying auto-scaling, what is "Percent of traffic to apply    
  95% or 99%"?
  
- app manager url https://apps.sys.evans.pal.pivotal.io
  
## Wrap-up

- How do you know how many instances to run?
  - why not 1 instance? availability
- (Bill K) shows apps manager and shows auto-scaling feature
  using JMeter
  

# App Continnum

## Talking points

- Delay architectural decision to as latest point as possible (Mike)
- Use a single repository for multiple applications as long as possible
  - It is easy to move around domains between applications
  

# Distributed System


## Talking points

-   Explain what the `${USER_ID}` and `${PROJECT_ID}` variables for 
-   Describe the relationship among the 4 apps - use Bill Kable's picture
-   Describe how to change the http://FILL_ME_IN - registration server
    endpoint is something you configure in the manifest.yml file 
    of the registration server
-   Demo how to use httpie or postMan

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
   
- siege -c255 urls.txt

  ```
  https://registration-pal-sangshin.apps.evans.pal.pivotal.io/users/1
  https://registration-pal-sangshin.apps.evans.pal.pivotal.io/accounts?ownerId=1
  https://registration-pal-sangshin.apps.evans.pal.pivotal.io/projects?accountId=1
  https://allocations-pal-sangshin.apps.evans.pal.pivotal.io/allocations?projectId=1
  https://backlog-pal-sangshin.apps.evans.pal.pivotal.io/stories?projectId=1
  https://timesheets-pal-sangshin.apps.evans.pal.pivotal.io/time-entries?userId=1
  ```
  
  ```
  https://registration-pal-sang-shin.cfapps.io/users/1
  https://registration-pal-sang-shin.cfapps.io/accounts?ownerId=1
  https://registration-pal-sang-shin.cfapps.io/projects?accountId=1
  https://allocations-pal-sang-shin.cfapps.io/allocations?  projectId=1
  https://backlog-pal-sang-shin.cfapps.io/stories?projectId=1
  https://timesheets-pal-sang-shin.cfapps.io/time-entries?userId=1
  ```
  
- [Postman collection](https://github.com/billkable/cnd-postman-collections)

- Installation and running of postman

```
$sudo snap install postman
$postman&
```

- Tip to replce

  ```
  find ./ -type f -exec sed -i -e 's/\$\{UNIQUE_IDENTIFIER\}\.\$\{DOMAIN\}/sang-shin.apps.evans.pal.pivotal.io/g' {} \;
  ```
  
## Challenge questions
  
```
If you are responsible for a greenfield project, would you start with Microservice architecture or monolith architecture? Why?

In the component architecture, what is the role of component and what is the role of application? How would you divide the required logic between the two?

Why are we using a single repository for all 4 microservices?  Isn't it a violation of the first rule of 12 factor app? 
  
In the "pal-tracker-distributed", we use 4 different databases, one for each application. 

  - Is it a recommended practice?  Should we have a single database instead?
  - Is it possible to have database inconsistency among the databases if there are multiple databases?  (For example, a user is deleted in User database, how does other databases reflect that change?) What would be the consequence to overall application behavior?
  - Is it OK to have duplication among the multiple databases?
    (In 'pal-tracker-distributed", we don't have any duplicate data.)
  - Is distributed transaction possible in micro-service architecture?

Application code should be insulated from data access logic? How do we achieve that in the "pal-tracker-distributed"? 

Why are there variations of a domain class, for example, why are there `TimeEntryForm`, `TimeEntryInfo`, `TimeEntryRecord`, `TimeEntryFields` classes? Where are they used?

When Timesheet server needs to talk to registration server via REST call, where does the Timesheet server finds the address of the registration server?

```
  
## Trouble-shooting

- ?? Somehow port 8081 is taken on my machine and "openPorts"
  does not show if the port is taken by any process
  
  You can try the following command on Mac
  
```
< workspace/pal-tracker-distributed - master > sudo lsof -i tcp:8081
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
 
- If GitHub action is causing too much a problem, just deploy the app using

  ```
  cf push -f manifest-registration.yml
  ```
    
- *When you execute the following command - you have to remove or commit
  the codebase.txt file

  ```
  < workspace/pal-tracker-distributed + master > git cherry-pick pipeline error: your local changes would be overwritten by cherry-pick.
  hint: commit your changes or stash them to proceed.
  fatal: cherry-pick failed  
  ```
  
# Service Discovery

## Talking points

- (Dylan) 
  - talked about problems of microservices
  - in pcf, every routing goes through gorouter - we may need more
    security, and more faster 
  - ?? gorouter (for public facing apps) vs eureka server (use it for
    internal communication)
  - container to container networking (with it even if you are using Eureka
    server, the services are still going through the gorouter)
  - eureka server still gives you client-side load-balancing, 
    eureka server can be used as a monitoring tool (health check)
    
- (Bill)
  - Spring cloud release train - Horton, Greenweech, ..
  - Technical debt because when the version of the tile changes,
    the applications need to be changed
  - How to resolve patch version - go to maven repo and find out

-   This lab has a lot of moving parts: service discovery/registration,
    client side load-balancing, spring cloud dependencies, end-to-end 
    testing.

- Service discovery
	-   Explain why service discovery and registration could be useful
	    in cloud
	    - in the cloud environment, services come and go
	    - you don't want use hard-coded address of target service
	    
	-   Discovery server can also play the role of making sure
	    unresponsive servers are removed from the list
	    
	-   Use service discovery picture (the lab document does not have
	    a link so I might have to draw one)

-   Dependency management (using Spring cloud dependency slides)
    - [Neil's slide](https://docs.google.com/presentation/d/1sY6mz_SRfRO-KFonJDjfEujgTFNmDkddit5l090PEZM/edit?ts=5d5a5860#slide=id.p) is a good one
    - Draw picture of SCS tile SCS client library

-   Client side Load balancer diagram
	-  Relationship between service discovery and client 
    	side load balancer
   -  RestTemplate annotated with @LoadBalanced annotation
      will talk to discovery server and retrieves the
      list of addresses and then perform client-side
      load-balanced

-   ??The terminology of spring cloud services in the code 
    needs to be explained

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
  "git": {
    "commit": {
      "time": "2019-11-25T20:46:52Z",
      "id": "325b9c6"
    },
    "branch": "HEAD"
  },
  "build": {
    "version": "2.1.4-build.4",
    "artifact": "spring-cloud-service-broker",
    "name": "service-broker",
    "group": "io.pivotal.spring.cloud",
    "time": "2020-04-24T15:28:18.633Z"
  }
}
  ```

-  PWS uses the following - see `build/version`

   ```
   > curl https://spring-cloud-service-broker.cfapps.io/actuator/info |json_pp
   {
   "git" : {
      "branch" : "HEAD",
      "commit" : {
         "id" : "6325a90",
         "time" : "2019-11-25T20:49:31Z"
      }
   },
   "build" : {
      "time" : "2019-11-27T00:26:12.716Z",
      "version" : "2.0.13-build.6",
      "name" : "service-broker",
      "artifact" : "spring-cloud-service-broker",
      "group" : "io.pivotal.spring.cloud"
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

## Container to Container networking

- When container-to-container networking is enabled, the
  Eureka server will maintain the addesses of the service
  instances in the form of internal ip addresses, with
  which the calling service can communicate directly
  with the destination service
  
- *Is container to container networking enabled in evans?
  Looks like it does not.
  
  ```
  < workspace/pal-tracker-distributed - master > cf add-network-policy tracker-allocations --destination-app tracker-registration --protocol tcp --port 8080-8090
  Adding network policy to app tracker-allocations in org sashin.pivotal.io / space sandbox as sashin@pivotal.io...
  provided scopes [cloud_controller.read password.write cloud_controller.write openid uaa.user] do not include allowed scopes [network.admin network.write]
  FAILED
  ```

- Add network policy

  ```
  cf add-network-policy SOURCE_APP --destination-app DESTINATION_APP -s DESTINATION_SPACE_NAME -o DESTINATION_ORG_NAME --protocol (tcp | udp) --port RANGE
  ```
  
  ```
  cf add-network-policy tracker-allocations --destination-app tracker-registration --protocol tcp --port 8080-8090
  ```
  
- [Configuring Cross Cloud Foundry Service Registy (route mode)](http://docs.pivotal.io/spring-cloud-services/1-4/common/service-registry/enabling-peer-replication.html)
- [GoRouter does honor Ribbon load balancing algorithm](http://docs.pivotal.io/spring-cloud-services/1-4/common/service-registry/connectors.html#instance-specific-routing-in-ribbon)
- [Configuring PCF Container-to-Container Networking, Service Registry and Client Load Balancing (SpringOne 2017)](https://www.youtube.com/watch?v=1WJhFhBr-0Q)

## Client side load balancing

- [Ribbon](https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-ribbon.html)

## Trouble-shooting

- ?? I get the following error when creating 

  ```
  < workspace/pal-tracker-distributed - master > curl -i -XPOST -H"Content-Type:  application/json" allocations-pal-sang-shin.apps.evans.pal.pivotal.io/allocations/ - d"{\"projectId\": \"1\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\":  \"2015-05-18\"}"
  HTTP/1.1 500 Internal Server Error

  {"timestamp":1587121186241,"status":500,"error":"Internal Server Error","message":"No instances available for registration-pal-sang-shin.apps.evans.pal.pivotal.io","path":"/allocations/"}
  ```
  
  * It was because

  ```
  Ah false alarm.  I had to unset-env REGISTRATION_SERVER_ENDPOINT.
  ```

- ??? the step to refresh gradle is missing again after
  creating build.gradle for platform-services/eureka-server

- ?? I get the following error when deploying the app

  ```
  2019-11-07T10:17:53.13-0500 [APP/PROC/WEB/2] OUT Caused by: java.lang.NoClassDefFoundError: org/springframework/cloud/config/client/ConfigServicePropertySourceLocator
  ```

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
- commands at PCF with PWS

```
// create account
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.cfapps.io/registration -d'{"name": "Pete"}'
curl -i registration-pal-sang-shin.cfapps.io/accounts?ownerId=1

// create projects
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.cfapps.io/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.cfapps.io/projects -d"{\"name\": \"Project B\", \"accountId\": \"1\"}"

// create allocation assuming projectId is 12 and userid is 2
curl -i -XPOST -H"Content-Type: application/json" allocations-pal-sang-shin.cfapps.io/allocations/ -d"{\"projectId\": \"12\", \"userId\": \"2\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

while true; sleep .3; do curl -i -XPOST -H"Content-Type: application/json" allocations-pal-sang-shin.cfapps.io/allocations/ -d"{\"projectId\": \"12\", \"userId\": \"2\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}";  done;
```

- commands at PCF with evans

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
 workspace/pal-tracker-distributed - master > curl localhost:8083 -H"Authorization: Bearer b78147e6-75f6-4a22-8498-26efe95d5dc6"
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
    -c "{\"git\": {\"uri\": \"https://github.com/${YOUR_GITHUB_USERNAME}/tracker-config.git\", \"label\":  \"master\"}}"
    ```
    
    ```
    cf create-service p-config-server standard tracker-config-server \
    -c "{\"git\": {\"uri\": \"https://github.com/sashinpivotal/tracker-config.git\", \"label\": \"master\"}}"
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
  

## Challenge questions

-   It is a good practice to save security-sensitive data such as
    passwords in the config server? If not, what can we do?
    
-   What happens when a config server is not available?
    
-   Is it a good practice to maintain configuration data in a
    single repository for multiple environments?

# Ending the course

-   (From Charles LeRose)

    ```
    As we head toward the end of this class, I’d like to repeat that the course material is available to you indefinitely (the web content with the labs, on the ‘courses’ site.)  You will also continue to have access to this Slack server.  (Be sure to remember you passwords for these.)  And I encourage you to join the #alumni channel here too.
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

```
Got it. My team is using parabol.co for our retros and I like it a lot more than the cfapps retro tool . Might be worth trying sometime!
```

