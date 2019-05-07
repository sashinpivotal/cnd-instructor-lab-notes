

## General

### Demo steps

-   If you want to start actuator lab from "topic-start", 
    follow the steps mentioned below 
    
    -   git checkout master (if current branch is not master)
    -   git reset --hard topic-start (to force local master to sync with remote master)
    -   change manifest files to reflect correct domain and route in manifest file
        - route: pal-tracker-sang-shin.apps.evans.pal.pivotal.io
    -   git push origin master -f (to sync the remote master with local master)
    -   Do the lab
    -   git push

-   If you want to save your "work-in-progress" to a new branch, do the 
    following (as documented in the pairing guide)
    
    -   git checkout -b my-mvc-branch
    -   git add .
    -   git commit -m "work in progress in mvc lab"
    -   git push origin my-mvc-branch --tags 

## Meerkat

### JDK version issues

- Pushing jar that is created with JDK 10 to PCF will fail. So you
  will have to recreate the jar file with JDK 8 
- Use `sudo update-alternatives --config java` to list the versions
  availale in the machine - choose JDK 8

### Software

-   No Chrome? (Only Firefox?)
-   Postman

- Students might have to set Gradle to 4.7 using the following command

   ```
   gradle wrapper --gradle-version 4.7
   ```
   
-   Make sure mysql is installed

### Meerkat keyboard shortcuts

- [default keymap](https://resources.jetbrains.com/storage/products/intellij-idea/docs/IntelliJIDEA_ReferenceCard.pdf)

- Alt+Insert for "generate" (CMD+N for Mac)
- Ctrl+N for "opening a class" (CMD+O for Mac)
- Ctrl+Shift+N for "open a file" 
- Alt+Enter what is quick fix combination
 
## Assignment Submission
   
### Talking points

- Note that whenever student submit the lab result, they always have to go 
  to the `assigment-submission` directory

- CND students should ignore `waveland` section

## Pairing Guide

### Tips

- Mention that the following statement is general guideline since 
  `pal-tracker` repository has not been created yet.

 ```
 Add the public key as a deploy key to your current  
 repository.
 ```
- Quotes from text file

 ```
(ssh-keygen is described in the pair rotation guide)
?some students experienced "key is already used" problem
 - he missed the steps of "ssh-add -K ~/.ssh/id_rsa 
?sarah goes through the steps of recreating ssh key with different name
https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

? once you have done ssh-genkey, you have to do ssh-add ~/.ssh/ia_rsa  (this is to add your private key to the system) ?? maybe if you are the only person using the system, you might not have to do it? Or if you are using the one under ~/.ssh directory, you don't have to?

-pick the person who owns the infrastructure use the usb to save the info
-and go through the procedure of https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

-use the default name if you can, when you use ssh-add, you have to enter the directory name otherwise
 ``` 
  
## Building a Spring Boot App (lab #1)

### Talking points

- Mention that the `pal-tracker` directory is under `workspace` directory

### Trouble-shootings

#### Project structure

- Some students did `git clone ..`, which wipes out the git history of
  local repository
  
- Steps to follow
  - Make sure you have unzipped the `pal-tracker.zip` under `workspace` directory
  - You have to have a GitHub account
  - Create `pal-tracker` repository
  - Go to `pal-tracker` directory
  - Execute `git remote add origin <url>`
  - Execute `git push origin master --tags`

#### Bootstrap the application

- ?? It says to select JVM 11, yet the setup guide still points to JDK 8

- After installation of JDK, IntellJ still does not list JDK 11 as one of the JDK options
  - After I set the JAVA_HOME to JDK 11 and restarted the IDE,
    then it worked.
    
- ??? When importing the project into the IntelliJ, I get the following error from IntelliJ

  ```
  Use JDK instead of JRE for Gradle Importer. Open Gradle Settings.
  ```
  
  - I had to choose JDK 8 in order to proceed

- ??? When refreshing Gradle within IntelliJ, I get the following error

  ```
  No such property: GradleVersion for class: JetGradlePlugin
  ```

#### Deploy

- We should add a warning that pushing the app (before setting
  JDK to 11) will fail with the following error message:
  
  ```
  2019-04-24T12:02:26.82-0400 [APP/PROC/WEB/0] ERR Exception in thread "main" java.lang.UnsupportedClassVersionError: io/pivotal/pal/tracker/PalTrackerApplication has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0
   2019-04-24T12:02:26.82-0400 [APP/PROC/WEB/0] ERR 	at java.lang.ClassLoader.defineClass1(Native Method)
   2019-04-24T12:02:26.82-0400 [APP/PROC/WEB/0] ERR 	at java.lang.ClassLoader.defineClass(ClassLoader.java:763)
   2019-04-24T12:02:26.82-0400 [APP/PROC/WEB/0] ERR 	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
   ```
   
   ```
   Java SE 13 = 57,
Java SE 12 = 56,
Java SE 11 = 55,
Java SE 10 = 54,
Java SE 9 = 53,
Java SE 8 = 52,
Java SE 7 = 51,
Java SE 6.0 = 50,
Java SE 5.0 = 49,
   ```

### Trouble-shooting

- If the test works at the command line but fails within 
  IntelliJ, make sure you 
  set the Gradle Test Runner under setting

- If you are using STS, try to verify your yml file 
  with `http://www.yamllint.com/`

- *The following code will faile because Spring looks for
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
  
## Configuring an App

### Tips

- If use @Value annotation at the field level, it did not work

### Trouble-shooting
  
### Challenge questions

- Do we have to do “cf restage <app-name>” when we set a new environment variable?
- Can a route be assigned to multiple applications?
- Anybody knows what “blue-green-deployment” is?
- What are the examples of PCF log types? (Google “PCF log types”)
- Speaking “blue-green deployment”, anybody can think of conceptual steps you 
  will take in PCF environment?
- What could be use cases where you will have to do “cf restage” (as opposed 
  to “cf restart”)?
- Try to use “create-app-manifest” command to capture the metadata of your running app into a file and try to use that file to deploy the application

### Slack channel tips

```
Great presentation on 12 factors https://content.pivotal.io/slides/the-12-factors-for-building-cloud-native-software
```

## Deployment Pipelines

### Tips

- Show how to set the environment variable in `travis-ci.org`
   - Recommend to select `Display value in build log` when
     creating an Travis environment variable
     
- Example Travis environment variables

  ```
  (when using pal pcf endpoint)
  CF_API_URL https://api.sys.evans.pal.pivotal.io
  CF_ORG sashin.pivotal.io
  CF_SPACE sandbox
  CF_USERNAME sashin@pivotal.io
  CF_PASSWORD blue42dragon
  GITHUB_USERNAME sashinpivotal
  GITHUB_OAUTH_TOKEN 636b1fabe74fd5facde093f8c788029a0dc778cb

  (when using pws pcf endpoint)
  CF_API_URL https://api.run.pivotal.io
  CF_ORG sashin-org
  CF_SPACE development
  CF_USERNAME sashin@pivotal.io
  CF_PASSWORD xxxxxxxx
  GITHUB_USERNAME sashinpivotal
  GITHUB_OAUTH_TOKEN 8a5373cbba24e068b45bd34befbe09b43c0bda80
  
  (what gets displayed in the travis log)
  $ export CF_API_URL=https://api.run.pivotal.io
  $ export CF_ORG=sashin-org
  $ export CF_SPACE=development
  $ export CF_USERNAME=sashin@pivotal.io
  $ export CF_PASSWORD=[secure]
  $ export GITHUB_USERNAME=sashinpivotal
  $ export GITHUB_OAUTH_TOKEN=c90c5341527a812b7f152639c45b4366364a1a09
  ```
     
- Travis supports running the job a specific branch by specifying it 
  in the `.travis.yml` file

  ```
  on:
    branch: my-own-branch
  ```
     
### Trouble-shooting

- *When I ran it (even after setting up Travis environment variables),
  I get the following error in the 1st phase. And I cannot see the report. (application
  error like this should be detected during local testing)
  
  ```
  test.pivotal.pal.trackerapi.WelcomeApiTest > exampleTest FAILED
    org.junit.ComparisonFailure at WelcomeApiTest.java:24
2019-04-24 19:11:22.725  INFO 3884 --- [       Thread-5] ConfigServletWebServerApplicationContext : Closing org.springframework.boot.web.servlet.context.AnnotationConfigServletWebServerApplicationContext@84181cf: startup date [Wed Apr 24 19:11:18 UTC 2019]; root of context hierarchy
3 tests completed, 1 failed
> Task :test FAILED
FAILURE: Build failed with an exception.
* What went wrong:
Execution failed for task ':test'.
> There were failing tests. See the report at: file:///home/travis/build/sashinpivotal/pal-tracker/build/reports/tests/test/index.html
  ```

- *I got a failure when I started the 2nd phase - it was because
  I did not do the first phase.  When I check in a new change, 
  the complete phase 1 and 2 are done, which eliminate the problem.
  I think it was because the jar file was not published in the
  1st job.

   ```
   $ wget -P applications/timesheets-server/build/libs https://github.com/$GITHUB_USERNAME/pal-tracker-distributed/releases/download/$RELEASE_TAG/timesheets-server.jar
--2019-05-03 14:13:22--  https://github.com/sashinpivotal/pal-tracker-distributed/releases/download/release-6/timesheets-server.jar
Resolving github.com (github.com)... 192.30.253.112
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2019-05-03 14:13:22 ERROR 404: Not Found.
   ```
   
-  *I got pcf deployment failure - you have to expand the arrow to
   see the failure - it was because the manifest file has wrong
   domain

   ```
   Installing deploy dependencies
Successfully installed dpl-cloud_foundry-1.10.8
Parsing documentation for dpl-cloud_foundry-1.10.8
Installing ri documentation for dpl-cloud_foundry-1.10.8
Deploying application
...
The route allocations-pal-sang-shin.cfapps.io did not match any existing domains.
FAILED
Logging out sashin@pivotal.io...
OK
Failed to push app
failed to deploy
   ```
     
## Spring MVC with REST endpoints

### Talking points

- Don't change the test code - that is the contract

- Show how to create remove compile errors also when there two compile 
  errors in a single line, you have to fix the one inside first
     
- Make sure TimeEntry constructor with the correct naming - 
  otherwise you will have hardtime reading test code
  
- The reason we have a constructor that does not set id is because
  we want to simulate the repository behavior where id gets generated 
  by the persistence layer
  
- Bill mentioned how to create an interface from code??
  
#### InMemoryRepositoryTest

- How to set the `id` field of `TimeEntry` when it gets created with without `id` argument?

  - You can create currentId field

- When creating a code for `list` method, IDE uses boolean   
  instead of `List<TimeEntry>` - `isEmpty()` method will cause
  compile error in this case
  
- In the list() test, IntelliJ gets confused when there are 5 constructor
  arguments and there is already a constructor that takes 4 arguments.
  
- Object comparison with `equals` and `hashCode`  
  - leverage IDE support on this
  - Do you want to include id field?

- Creating `List` object from `timeEntryMap.values()`

  - new ArrayList<>(timeEntryMap.values())

- `timeEntryMap.replace(id, timeEntry)` returns an old value not new value

- Even when `equals` and `hashCode` are provided, if 
  the test results in the following, it's time to debug
  
  ```
  Expected :io.pivotal.pal.tracker.TimeEntry@a007329
  Actual   :io.pivotal.pal.tracker.TimeEntry@9f25ba8
  ```
  
#### TimeEntryController test

- *We are not testing the create operation sets the location 
 response field - verify the solution is something like following:
 (sent a feedback)
 
 ```
    public ResponseEntity<TimeEntry> create(TimeEntry timeEntryToCreate) {
        TimeEntry timeEntry = timeEntryRepository.create(timeEntryToCreate);
//        URI uri = ServletUriComponentsBuilder.fromCurrentRequestUri()
//                                             .path("id")
//                                             .buildAndExpand(timeEntry.getId())
//                                             .toUri();
//        return ResponseEntity.created(uri).build();
        return ResponseEntity.status(HttpStatus.CREATED)
                             .body(timeEntry);
    }
 ```

- Creating an ResponseEntity object in the TimeEntryController

  ```
  return new ResponseEntity(timeEntryRepository.create(timeEntryToCreate),   
                            HttpStatus.CREATED);
  ```
  
- Make sure @RequestBody and @PathVariable are used appropriately

### Trouble shooting

#### Local testing

- *experience the following problem when testing TimeEntryApiTest's
  create and read tests

  ```
  No results for path: $['date']
com.jayway.jsonpath.PathNotFoundException: No results for path: $['date']
  ```
  
  It was because I set the field name to local
  
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
  
- ??? Even if Gradle runner setting is done in IntelliJ, running the app
  within the IDE still results in the following error
  
  ```
  Caused by: java.lang.IllegalArgumentException: Could not resolve placeholder 'welcome.message' in value "${welcome.message}"
  ```

#### Travis

- *Somehow all tests passed but Travis results in the following error
  I had to use different mockito version.

 ```
 > Task :test
test.pivotal.pal.tracker.TimeEntryControllerTest > testList FAILED
    org.mockito.exceptions.base.MockitoException at TimeEntryControllerTest.java:26
        Caused by: java.lang.UnsupportedOperationException at TimeEntryControllerTest.java:26
            Caused by: java.lang.IllegalStateException at TimeEntryControllerTest.java:26
                Caused by: java.lang.NoSuchMethodException at TimeEntryControllerTest.java:26
 ```

### Challenge Questions

- What are the differences between unit testing vs integration testing? 
  In “pal-tracker” project, which tests are integrating testing?
- Why TimeEntryControllerTest code needs mocking while 
  InMemoryTimeEntryRepositoryTesting code doesn’t?
- What is the difference between stubbing and mocking? When
  do you want use stubbing over mocking and vice-versa?
- What is the reason controller TimeEntryControllerTest code 
  has “verify” method?
- From unit-testing standpoint, why is it a bad practice to create a 
  dependency object inside your class using “new” keyword or even using 
  factory (as opposed to getting it injected either through constructor 
  method or setting method)?
- What is the another way of creating InMemoryTimeEntryRepository bean 
  other than using @Bean in the configuration class? What 
  would be pros and cons of each approach?
- What does SOLID (design principles) stand for?
- What are the examples of “Open for extension Closed for 
  modification” design principle in the “pal-tracker” project?
  
### Slack channel tips

- Use of httpie

```
The following is the “curl” command to create a time-entry:

curl -i -XPOST -H”Content-Type: application/json” localhost:8080/time-entries/ -d”{\“projectId\“: 1, \“userId\“: 1, \“date\“: \“2015-05-17\“, \“hours\“: 6}”

Actually HTTPie is a lot easier to use than curl.  In order to install HTTPie, you can do the following:

sudo apt install httpie

Then you can run the following command to add an TimeEntry like following:

http post localhost:8080/time-entries projectId=1 userId=1 date=2018-01-01  hours=20

Of course, if you like GUI REST client, you can use PostMan
```

- Saving work and then change to a tag

```
By the way, before you do the above step, if you need to save your current unfinished work into “work in progress” branch, you do the following:
-   git checkout -b wip-branch
-   git add .
-   git commit -m “work in progress in my lab”
-   git push origin wip-branch
```

```
If you want to start actuator lab from “actuator-start”, follow the steps mentioned below:

-   git checkout master (if current branch is not master)
-   git reset --hard actuator-start (to force local master to sync with actuator-start - NO need to do “cherry-pick”)
-   (change manifest file to reflect correct route)
-   git push origin master -f (to sync the remote master with local master)
-   Do the lab
-   git push 
```

- Install of postman on meerkat

```
sudo snap install postman
```
  
## Database Migration

### Tips

- Make sure to use double underscore when creating migration files
- * How do you see the list of services using brew?  brew services list
- When executing flyway command, username and password will be asked.
  Enter tracker and no password
  
### Trouble-shooting

- ??? It takes more than 20 minutes to get the step 2 to get finished.
  What do we expect students do during this time?  

## JDBC 

### Talking points

-  *One student experience experiencing a problem starting the app from the IDE while things work at the command line

### Trouble-shooting

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
* Try:
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

## Actuator

### Tips

-  We need to provide instruction on how to use curl, httpie, or postman
-  Install HTTPie using the following command to Meerkat

   ```
   sudo apt install httpie
   ```
   
- The META-INF/build-info.properties is under build/resources/main directory

- The code in the HealthApiTest below is not needed

  ```
      @Before
    public void setUp() throws Exception {
        RestTemplateBuilder builder = new RestTemplateBuilder()
                .rootUri("http://localhost:" + port)
                .basicAuthorization("user", "password");

        restTemplate = new TestRestTemplate(builder);
    }
  ```
   
### Talking points

- For /health value proposition, talk about the case "applicatio hang" - GC hang - CF does just port health check

### Trouble-shooting

- * HealthApiTest fails due the following reason even though 
  accessing the endpoint from a browser works fine. Why?
  It was because I reserved the up() and down() logic.

  ```
  org.junit.ComparisonFailure: expected:<[200]> but was:<[503]>
  ```
  
- * Besides the test checks if the db status is UP but the result
  is down when accessed from a browser. Why?
  It was because I reserved the up() and down() logic.



## Distributed System

### Tips

-  Services I need in PWS

   ```
   tracker-allocations-database    ...
   tracker-backlog-database        ...                   
   tracker-database               
   tracker-registration-database   
   tracker-timesheets-database
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

### Talking points

-   Pair rotation, new key
-   Explain what the `${USER_ID}` and `${PROJECT_ID}` variables for 
-   Describe the relationship among the 4 apps
-   Describe how to change the http://FILL_ME_IN - registration server
    endpoint is something you configure in the manifest.yml file 
    of the registration server
-   Demo how to use httpie or postMan
    
### Trouble-shooting

-   ?? Some students were having a problem with "get push" key issue
    when they use new key even after they added ssh-add
    

## Service Discovery

### Talking points

-   Dependency management (using Spring cloud dependency slides)
-   Draw picture of SCS tile, 
-   Service discovery picture
-   Eureka diagram from Spring cloud dev
-   Client side Load balancer diagram
-   Relationship between service discovery and client 
    side load balancer

-   Go through the codebase
    
-   Let stundent to start service registry service before doing the lab
-   The terminology of spring cloud services in the code needs to be explained

### Tips

-  PWS uses the following

   ```
    > curl https://spring-cloud-service-broker.cfapps.io/actuator/info |json_pp
{
   "git" : {
      "branch" : "HEAD",
      "commit" : {
         "time" : "2018-08-17T09:08:06Z",
         "id" : "6af8fcf"
      }
   },
   "build" : {
      "time" : "2018-08-31T15:04:36.801Z",
      "artifact" : "spring-cloud-service-broker",
      "group" : "io.pivotal.spring.cloud",
      "version" : "2.0.2-build.3",
      "name" : "service-broker"
   }
   ```

   ```
   springCloudVersion = SPRING_CLOUD_VERSION
springCloudServicesClientLibrariesVersion = SPRING_CLOUD_SERVICES_CLIENT_LIBRARIES_VERSION
   ```
   
   ```
   springCloudVersion = "Finchley.RELEASE"
   springCloudServicesClientLibrariesVersion = "2.0.2.RELEASE"
   ```
   
   
- apps.evans.pal.pivotal.io is using the following

  ```
  curl https://spring-cloud-broker.apps.evans.pal.pivotal.io/actuator/info
  ```
  
- Adding @EnableEurekaClient takes time to get rid of compile errors

### Trouble-shooting

- * local testing was successful but the travis fails on me
  during deployment (it was because I did not set CF_SPACE)
  
  ```
  0.01s$ cp manifest-allocations.yml manifest.yml
before_deploy.2
0.01s$ echo "Deploying allocations server $RELEASE_TAG"
Deploying allocations server release-3
dpl_0
1.78s$ rvm $(travis_internal_ruby) --fuzzy do ruby -S gem install dpl
Successfully installed dpl-1.10.8
Parsing documentation for dpl-1.10.8
Installing ri documentation for dpl-1.10.8
Done installing documentation for dpl after 0 seconds
1 gem installed
invalid option "--space="
failed to deploy
  ```


## Circuit breaker

### Misc

- commands at the local machine

```
// create account
curl -i -XPOST -H"Content-Type: application/json" localhost:8083/registration -d'{"name": "Pete"}'
curl -i localhost:8083/accounts?ownerId=1

// create projects
curl -i -XPOST -H"Content-Type: application/json" localhost:8083/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"
curl -i -XPOST -H"Content-Type: application/json" localhost:8083/projects -d"{\"name\": \"Project B\", \"accountId\": \"1\"}"

// create allocation assuming projectId is 2
curl -i -XPOST -H"Content-Type: application/json" localhost:8081/allocations/ -d"{\"projectId\": \"2\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

// create allocation assuming projectId is 4
curl -i -XPOST -H"Content-Type: application/json" localhost:8081/allocations/ -d"{\"projectId\": \"4\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

```
- commands at PCF

```
// create account
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.cfapps.io/registration -d'{"name": "Pete"}'
curl -i registration-pal-sang-shin.cfapps.io/accounts?ownerId=1

// create projects
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.cfapps.io/projects -d"{\"name\": \"Project A\", \"accountId\": \"1\"}"
curl -i -XPOST -H"Content-Type: application/json" registration-pal-sang-shin.cfapps.io/projects -d"{\"name\": \"Project B\", \"accountId\": \"1\"}"

// create allocation assuming projectId is 12 and userid is 2
curl -i -XPOST -H"Content-Type: application/json" allocations-pal-sang-shin.cfapps.io/allocations/ -d"{\"projectId\": \"12\", \"userId\": \"2\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

// create allocation assuming projectId is 4
curl -i -XPOST -H"Content-Type: application/json" allocations-pal-sang-shin.cfapps.io/allocations/ -d"{\"projectId\": \"2\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"

```

- siege -c255 -f urls.txt

  ```
  -urls.txt
https://registration-pal-sang-shin.apps.evans.pal.pivotal.io/users/1
https://registration-pal-sang-shin.apps.evans.pal.pivotal.io/accounts?ownerId=1
https://registration-pal-sang-shin.apps.evans.pal.pivotal.io/projects?accountId=1
https://allocations-pal-sang-shin.apps.evans.pal.pivotal.io/allocations?projectId=1
https://backlog-pal-sang-shin.apps.evans.pal.pivotal.io/stories?projectId=1
https://timesheets-pal-sang-shin.apps.evans.pal.pivotal.io/time-entries?userId=1
  ```

- How to start and stop mysql

  ```
  brew services start mysql
  brew services list
  brew services stop --all
  brew services cleanup
  ```

### Talking points

-   The @Hystrix command needs to be duplicated in 3 different places -
    there is a reason for this  
    
      
    
## Securing Distributed Application

### Talking points

### Demo steps

-   Use `security-solution` as base code
-   Change 4 manifest files to reflect route
-   Make sure to create services manually at PCF

### Trouble-shooting tips

-   Just found out why I had failure on my oauth2 testing.  I was running the apps using Spring Boot dashboard, which fails to read the security property values from the build.gradle.
But why  doesn’t IntelliJ honor the setting “Delegate IDE build/run to gradle”?

-  *In the local testing, I am experencing the following problem even 
   though flowtest gets started with .put("APPLICATION_OAUTH_ENABLED", "false") 

   ```
   Caused by:
        org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'projectClient' defined in io.pivotal.pal.tracker.allocations.App: Unsatisfied dependency expressed through method 'projectClient' parameter 0; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'restTemplate' defined in class path resource [io/pivotal/pal/tracker/allocations/OauthResourceServerConfig.class]: Unsatisfied dependency expressed through method 'restTemplate' parameter 0; nested exception is org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type 'org.springframework.security.oauth2.client.resource.OAuth2ProtectedResourceDetails' available: expected at least 1 bean which qualifies as autowire candidate. Dependency annotations: {}
   ```
   
   It is because I should have added the following to the application.properties in the test not the target code
   
   ```
   application.oauth-enabled=false
   ```
   
-  ???I get the following error

   ```
   Updating app tracker-allocations...
Mapping routes...
Binding services...
The service broker rejected the request to https://spring-cloud-broker.apps.evans.pal.pivotal.io/v2/service_instances/d4eca7bf-9532-43bd-b79a-5326e6b8be86/service_bindings/3c73ba10-defc-4873-bad6-47f4937dc053. Status Code: 404 Not Found, Body: 404 Not Found: Requested route ('spring-cloud-broker.apps.evans.pal.pivotal.io') does not exist.
   ```

## Config Server

### Talking points

-   ?? Is this lab dependent on security lab?
-   ?? When to use branch?
-   Fault tolerance
-   Confguration draft