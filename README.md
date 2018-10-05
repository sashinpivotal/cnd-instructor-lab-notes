## Before Cohort

### Message to send to trainees




## General

### Demo steps

-   If you want to start actuator lab from "topic-start", 
    follow the steps mentioned below 
    
    -   git checkout master (if current branch is not master)
    -   git reset --hard topic-start (to force local master to sync with remote master)
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

-   ?? No Chrome? (Only Firefox?)
-   ?? Postman

- Students might have to set Gradle to 4.7 using the following command

   ```
   gradle wrapper --gradle-version 4.7
   ```
   
-   Make sure mysql

### Meerkat keyboard shortcuts

- Alt+Insert for "generate" (CMD+N for Mac)
- Alt+N for "opening a class" (CMD+O for Mac)
- Alt+Shift+N for "open a file" ?? 
 
## Assignment Submission
   
### Talking points

- Note that whenever student submit the lab result, they always have to go 
  to the assigment-submission project

- CND students should ignore `waveland` section

## Pairing Guide

- Mention that the following statement is general guideline since 
  `pal-tracker` repository has not been created yet.

 ```
 Add the public key as a deploy key to your current  
 repository.
 ```
  
## Spring Boot

### Talking points

- Mention that the `pal-tracker` directory is under `workspace` directory

### Trouble-shooting

- Some students did `git clone ..`, which wipes out the git history of
  local repository



## Deploying a Spring Boot app to PCF

- If the test works in the command line but fails within 
  IntelliJ, make sure you 
  set the Gradle Test Runner under setting

- If you are using STS, try to verify your yml file 
  with `http://www.yamllint.com/`

- If you see something like following, it is because the 
  welcome message is not
  being set with @Value annotation, which triggers Spring to 
  think it has   to be a bean
  
  ```
  ```
  
### Challenge questions

- Do we have to do “cf restage <app-name>” when we set a new environment variable?
- Anybody has an answer to the previously asked question “can a route be assigned 
  to multiple applications?”
- Anybody knows what “blue-green-deployment” is?
- What are the examples of PCF log types? (Google “PCF log types”)
- Speaking “blue-green deployment”, anybody can think of conceptual steps you 
  will take in PCF environment?
- What could be use cases where you will have to do “cf restage” (as opposed 
  to “cf restart”)?
- Try to use “create-app-manifest” command to capture the metadata of your running app 
  into a file and try to use that file to deploy the application

## Pipeline

- Show how to set the environment variable in `travis-ci.org`
   - Recommend to select `Display value in build log` when
     creating an environment variable
     
- Travis supports running the job a specific branch by specifying it 
  in the `.travis.yml` file

  ```
  on:
    branch: my-own-branch
  ```
     
### Trouble-shooting

- Travis does not tell the failure detail if there is a
  route issue in the 2nd step
     
## Spring MVC with REST endpoints

### Talking points

- Don't change the test code - that is the contract

- Show how to create remove compile errors also when there two compile 
  errors in a single lin, you have to fix the one inside first
     
- Make sure TimeEntry constructor with the correct naming - 
  otherwise you will have hardtime reading test code
  
- The reason we have a constructor that does not set id is because
  we want to simulate the repository behavior where id gets generated 
  by the database
  
- Bill mentioned how to create an interface from code??
  
#### InMemoryRepositoryTest

- How to set the `id` field of `TimeEntry` when it gets created with without `id` argument

- When creating a code for `list` method, IDE uses boolean   
  instead of `List<TimeEntry>` - `isEmpty()` method will cause
  compile error in this case
  
- Object comparison with `equals` and `hashCode`  - leverage IDE support on this

- Creating `List` object from `timeEntryMap.values()`

- `timeEntryMap.replace(id, timeEntry)` returns an old value not new value

- Even when `equals` and `hashCode` are provided, if the test results in the following,
  it's time to debug
  
  ```
  Expected :io.pivotal.pal.tracker.TimeEntry@a007329
  Actual   :io.pivotal.pal.tracker.TimeEntry@9f25ba8
  ```
  
#### TimeEntryApi test

- Creating an ResponseEntity object in the TimeEntryController

  ```
  return new ResponseEntity(timeEntryRepository.create(timeEntryToCreate),   
                            HttpStatus.CREATED);
  ```
  
- Make sure @RequestBody and @PathVariable are used appropriately

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
  
## Database Migration

- Make sure to use double underscore when creating migration files

## JDBC 

### Talking points

- ?? One student experience experiencing a problem starting the app from the IDE while things work at the command line

## Actuator

### When you start with actuator-starter

-  We need to provide instruction on how to use curl, httpie, or postman

-  ??You might experience "database not found" problem - you will have 
   to add the following:  (solution does not have do this??)

   ```
   compile("com.h2database:h2")
   ```

-  Install HTTPie using the following command to Meerkat

   ```
   sudo apt install httpie
   ```
   
### Talking points

- For /health value proposition, talk about the case "applicatio hang" - GC hang - CF does just port health check

## Distributed System

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

### Trouble-shooting

-   For service discovery lab, we discovered you need to explicitly 
    unset the environment variable REGISTRATION_SERVER_ENDPOINT from allocations, timesheets, and backlog apps
you can do this either from the cf cli with the command cf unset-env (run cf help unset-env to review the syntax) or via the apps manager, navigate to the app, and look under settings (tab).
Otherwise, you will experience an error when submitting assignment or manually posting 
(this one happened in ford)
cf unset-env tracker-allocations REGISTRATION_SERVER_ENDPOINT

-   if there is an 401 error when runnin "gw clean build", it is 
    likely application.properties of the test did not have the following

    ```
    security.basic.enabled=false
    management.security.enabled=false
    ```
    
## Circuit breaker

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

## Config Server

### Talking points

-   ?? Is this lab dependent on security lab?
-   ?? When to use branch?
-   Fault tolerance
-   Confguration drait