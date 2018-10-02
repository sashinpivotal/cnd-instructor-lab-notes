
## General

### Demo steps

- If you want to demo any lab, follow the steps mentioned below to 
  get to the starting point

   - git checkout master (if current branch is not master)
   - git reset --hard <pipeline-start> (to set master to a starting tag)
   - git push origin master -f (if you need to sync the remote)
   - Do the lab

- If you want to save your "work-in-progress" to a new branch, do the 
  following (as documented in the pairing guide)

   - git checkout -b <wip-mvc>
   - git add .
   - git commit -m "work in progress in mvc lab"
   - git push origin <wip-mvc>
   
## Assignment Submission

### Important

- Students might have to set Gradle to 4.7 using the following command

   ```
   gradle wrapper --gradle-version 4.7
   ```
   
### Semi-important

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

### Semi-important

- Mention that the `pal-tracker` directory is under `workspace` directory

### Errors students make

- Some students did `git clone ..`, which wipes out the git history of local repository



## Deploying a Spring Boot app to PCF

- If the test works in the command line but fails within IntelliJ, make sure you 
  set the Gradle Test Runner under setting

- If you are using STS, try to verify your yml file with `http://www.yamllint.com/`

- If you see something like following, it is because the welcome message is not
  being set with @Value annotation, which triggers Spring to think it has to be a bean
  
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
     
- Travis supports running the job a specific branch by specifying it in the .travis.yml

  ```
  on:
    branch: my-own-branch
  ```
     
### Trouble-shooting

- Travis does not tell the failure detail if there is a
  route issue in the 2nd step
     
## Spring MVC with REST endpoints

### Tell students

- Don't change the test code - that is the contract

- Show how to create remove compile errors also when there two compile 
  errors in a single lin, you have to fix the one inside first
     
- Make sure TimeEntry constructor with the correct naming - otherwise you 
  will have hardtime reading test code
  
- The reason we have a constructor that does not set id is because
  we want to simulate the repository behavior where id gets generated 
  by the database
  
### Things to consider

#### InMemoryRepositoryTest

- How to set the `id` field when user creates a `TimeEntry` with without `id` 

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
  
- @RequestBody and @PathVariable

- If you see the following error in the API testing, it is because

  ```
  expected:<[201]> but was:<[405]>
  Expected :201
  Actual   :405
  ```

### Challenge Questions

- What are the differences between unit testing vs integration testing? 
  In “pal-tracker” project, which tests are integrating testing?
- Why TimeEntryControllerTest code needs mocking while 
  InMemoryTimeEntryRepositoryTesting code doesn’t?
- What is the difference between stubbing and mocking? When
  do you want stubbing over mocking and vice-versa?
- What is the reason controller TimeEntryControllerTest code has “verify” method?
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