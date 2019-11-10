

# Before the cohort

- We can send the following message before cohort gets started

  ```
  By now, I assume everyone can access the course contents
  from the following site
  
   http://course.education.pivotal.io 
  
  Please make sure you receive slack channel message from
  PAL-Cloud-OPS team which provides your own PCF credentials 
  like following:
  
    Hi <Your name>, welcome to Accenture. The below information 
    will be useful throughout the course to access materials and 
    infrastructure. View discussion about your course in 
    #torontoc-nov-2019-cnd.
    Cohort ID: 349803372
    PCF Foundation API: api.sys.evans.pal.pivotal.io
    PCF Org: <your PCF org>
    PCF Username: <your email address>
    PCF Password: <password>
  
  From tomorrow morning, all our communication will be 
  through our #torontoc-nov-2019-cnd slack channel.
  
  BTW, if this is your first time accessing Slack channel, 
  please create an account via http://palexternal.slack.com
  using your Accenture email address.
  ```

# Getting started (logistics)

- Each student receive slack channel message which contains
  PCF account and AWS account information from `PAL-Cloud-OPS`
  
  ```
  Hi Sang Shin, welcome to EMEA - ATOS. The below information will be useful  throughout the  course to access materials and infrastructure. View discussion about your course in #bordeaux-sep-2019-cna.
  Cohort ID: 349803278
  PCF Foundation API: api.sys.evans.pal.pivotal.io
  PCF Org: sashin.pivotal.io
  PCF Username: sashin@pivotal.io
  PCF Password: xxxx
  AWS Credentials:
   * AWS Access Key: xxxx
   * AWS Secret Key: xxxx
   * AWS Bucket Name: sashin.pivotal.io
  ```
  
  ```
  Hi <Your name>, welcome to Accenture. The below information will
  be useful throughout the course to access materials and 
  infrastructure. View discussion about your course in 
  #torontoc-nov-2019-cnd.
  Cohort ID: 349803372
  PCF Foundation API: api.sys.evans.pal.pivotal.io
  PCF Org: <your PCF org>
  PCF Username: <your email address>
  PCF Password: <password>
  ```

- A student can access their slack channel message by
  opening slack or go to `palexternal.slack.com` 

- Does each student receive an email regarding how to
  access CNA course contents? No. They just receive
  slack channel messege that contains PCF and AWS
  credentials
  
- In order to see the self-evaluation, please go to
  [https://registration.education.pivotal.io/admin/cohorts](https://registration.education.pivotal.io/admin/cohorts)
  
- Brad send out the following information to the class channel
  (Make sure to set the Cohort Id and course Id)

  ```
  Cohort Information:
  Cohort Id: 349803278
  Course Content: https://courses.education.pivotal.io/c/349803278
  MeerKats password: keepitsimple
  Parrit: https://parrit.cfapps.io/bostonma-aug-2019-cnd (password:  keepitsimple)
  ```
  
- Mike G sent out the following

  ```
  Cohort Information:
  Machine username/password: pivotaluser/keepitsimple
  Cohort Id: 349803372
  Course URL: https://courses.education.pivotal.io
  PCF API endpoint: https://api.sys.evans.pal.pivotal.io
  PCF web UI: https://login.sys.evans.pal.pivotal.io
  ```
  
  ```
  @here Do not worry about your pair setting up a github today. we will deal with that tomorrow before we do a pair rotation
  ```
  
  ```
  @here please make sure you are pairing effectively.
  The easiest way is to use a timebox where you switch driving every 20  minutes.
  if you are interested in more pairing information:
  https://stackify.com/pair-programming-styles/
  ```

# Git related

## Demo steps for a particular topic

-   If you want to start "topic" lab from "topic-start", 
    follow the steps mentioned below 
    
    -   git checkout master (if current branch is not master)
    -   git reset --hard topic-start (to force local master to sync with remote master)
    -   change manifest files to reflect correct domain and route in manifest file
        - route: pal-tracker-sang-shin.apps.evans.pal.pivotal.io
    -   git add-commit -m "manifest file changed"
    -   git push origin master -f (to sync the remote master with local master - do not to this in production!)
    -   Do the lab
    -   git push

## Save "in progress" work in a personal branch

```
By the way, before you do the above step, if you need to save your current unfinished work into “work in progress” branch, you do the following:
-   git checkout -b wip-branch
-   git add .
-   git commit -m “work in progress in my lab”
-   git push origin wip-branch --tags
```

-   If you have created github repository with README.md, you
    will experience the following problem when you do 
    `git push origin master`.
    An easy way out is `git push origin master -f`

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

-   If you want to go to a solution project while maintaining
    your code (??? Is this correct?)

```
- git checkout master
- git cherry-pick abort
- git cherry-pick <topic-solution-tag> and handle merge conflict
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

# Pair Programming

- Communicate what you do to your partner - if you are typing or
  moving your mouse without talking, you are doing a disservice 
  to your pair partner

# Pair rotation

- Mention this after `pal-tracker` lab and just before 
  `pal-tracker-distributed` (This is what Brad sent out)

```
@here This morning before we rotate pairs:
1. The other pair should create a Github repository for `pal-tracker`
2. git remote add other-origin <github repo url> 
3. git push --tags -f  -u other-origin master
4. git remote remove other-origin
```

- Before the rotation, please do
	- Ensure both pairs have code on their github

- Sarah used post-it tag to designate a `driver` of the pair
  (ownder of GitHub and PCF account)
  
- My scheme - to make sure non-driver become a driver
  - everyone moves to the right by one position
  - non-driver in the pal-tracker will be become a driver 

- After the rotation, the following need to be changed to
  the pink post-it person (driver
  - Slack
  - PCF
  - GIT
  - Assignment Submission
  - Travis CI (edited) 

```
Pair rotation guide:
- Before the rotation, please ensure that both members of the pair
  save the code to the Github repository
- Log out from PCF, Slack, Travis CI
- Once everyone is ready, everyone moves to the right by one seat. 
  The rightmost person of the table goes to leftmost seat of
  the table behind. (This is to make sure non-driver in the 
  previous lab play the role of the driver)
- Once sitting is complete, use the driver's (the machine with
  the red post-it) credentials of the following:
    - Slack
    - PCF (PAS) 
    - GIT
    - Assignment Submission
    - Travis CI (edited) 
```

# Meerkat

## Meerkat keyboard shortcuts

- [default keymap](https://resources.jetbrains.com/storage/products/intellij-idea/docs/IntelliJIDEA_ReferenceCard.pdf)

- Alt+Enter what is quick fix combination
- Alt+Insert for "generate" (CMD+N for Mac)
- Ctrl+N for "opening a class" (CMD+O for Mac)
- Ctrl+Shift+N for "open a file" 

# Assignment Submission
   
## Talking points

- Note that whenever student submit the lab result, 
  they always have to go to the `assigment-submission` directory

- CND students should ignore `waveland` section

  
# Building a Spring Boot App (lab #1)

## Talking points

- Talk about dependency injection - what it is and why
- Mention that the `pal-tracker` directory is under `workspace` directory

## Project structure
  
- Steps to follow
  - Create a personal GitHub account (if you don't have one yet)
  - Create "pal-tracker" repository 
  - Make sure you have unzipped the `pal-tracker.zip` under `workspace` directory
  - Go to `pal-tracker` directory
  - Execute `git remote add origin <url>`
  - Execute `git push origin master --tags`

## Bootstrap the application

- Why do we say the following?

  ```
  Make sure to use File > Open to open your Gradle project rather than using the import feature.
  ```

- If the test works at the command line but fails within 
  IntelliJ using bootRun task, make sure you 
  set the Gradle Test Runner under setting (?? With
  Spring Boot 2.2, this could cause a problem)

- If you are using STS, try to verify your yml file syntax
  with `http://www.yamllint.com/`
  
- *IntelliJ - I don't find refresh menu option, and I don't
  see Gradle menu bar option either - I had to
  close and re-import the project to see Gradle menu 
  bar. - this is to use refresh icon from the Gradle bar
  menu on the right.
  
- *What is `buildscript` closure for?

  ```
  The buildScript block determines which plugins, task classes, and  
  other classes are available for use in the rest of the build script.   
  Without a buildScript block, you can use everything that ships with Gradle out-of-the-box. 
  
  If you additionally want to use third-party plugins, task classes, or other classes (in the build script!), you have to specify the corresponding dependencies in the buildScript block.
  ```
  
- ?? Why do we have the following in both buildscript 
  section and regular section of the build.gradle?
  
  ```groovy
  repositories {
    mavenCentral()
  }
  ```

- In step 10, if `create package` option is not available, it 
  is because the Gradle project was not refreshed (as mentioned
  in step 8)
  
- *Somehow, I could not find "bootRun", which means spring
  boot plugin did not work - it is because I missed the
  following:
  
  ```
  apply plugin: 'org.springframework.boot'
  ```
  
## Deploy
  
-  *Somehow, I get the following error when deploying to the PCF:
  it was because I pushed a wrong jar (gradle-wrapper.jar)

  ```
  None of the buildpacks detected a compatible application
  ```
 
## Challenge questions

-  What the purpose of "gradle wrapper"?

  
# Configuring an App
  
## Challenge questions

- Do we have to do “cf restage <app-name>” when we set a new environment variable?
- What are the examples of PCF log types? (Google “PCF log types”)

- What could be use cases where you will have to do “cf restage” (as opposed 
  to “cf restart”)?
- (Related question to the above) What are the differences among 3 different 
  ways of deploying the application on PCF - "pushing", "restaging", and "restart"?
- Try to use “create-app-manifest” command to capture the metadata of your running app into a file and try to use that file to deploy the application


## Slack channel tips

```
Great (concise yet to the point) presentation on 12 factors:  https://content.pivotal.io/slides/the-12-factors-for-building-cloud-native-software
```

## Trouble-shootings

- The document does not include instruction to remove compile
  errors on EnvController before it says to run the app

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

## Misc

- *Is there a way to set environment variables to an application
  through App manager?
  Yes, there is. Click "Settings" link on the left in the application
  page.
  

  
# Deployment Pipelines

## Talking poijnts (used by Mike G.)

- Why we do this lab before we write complete code 
   - deloyment is hard, we want minimum complication
   - get deployment process taken care of in the earlier stage 
   - cannot solve process issues with technology
   
- Travis
   - concept is important, we dn't care which CI tool you use

- What CD mean to you?
   - deployment to production is business decision not Eng decision
   - ??dep to prod is risky, user segregation??
   - github example, users, cost vs risk, regulartory constraint

- Explain the following travis.yml 

  ```
  dist: trusty
  sudo: false
  notifications:
    email: false
  env:
    - RELEASE_TAG="release-$TRAVIS_BUILD_NUMBER"
  if: tag IS blank


  jobs:
    include:
      - stage: build and publish.  // create jar and publish to gihub
        language: java
        jdk: openjdk11
        install: skip
        script: ./gradlew clean build // command to create jar file
        before_deploy:
          - git config --local user.name "Travis CI"
          - git config --local user.email "travis@example.com"
          - git tag -f $RELEASE_TAG
        deploy:                       // publish to github
          provider: releases
          api_key: $GITHUB_OAUTH_TOKEN
          file: "build/libs/pal-tracker.jar"
          skip_cleanup: true
      - stage: deploy to cf       // deploy the jar to the PCF
        language: bash
        script:
          - echo "Downloading $RELEASE_TAG"
          - wget -P build/libs https://github.com/$GITHUB_USERNAME/pal-tracker/releases/download/$RELEASE_TAG/pal-tracker.jar // get the jar file from github
        before_deploy:
          - echo "Deploying $RELEASE_TAG to Cloud Foundry"
        deploy:                   // deploy to PCF
          provider: cloudfoundry
          api: $CF_API_URL
          username: $CF_USERNAME
          password: $CF_PASSWORD
          organization: $CF_ORG
          space: $CF_SPACE

  ```


## Tips

- Show how to set the environment variable in `travis-ci.org`
   - Recommend to select `Display value in build log` when
     creating an Travis environment variable
     
- Example Travis environment variables


  ```
  (when using PAL pcf endpoint)
  CF_API_URL https://api.sys.evans.pal.pivotal.io
  CF_ORG sashin.pivotal.io
  CF_SPACE sandbox
  CF_USERNAME sashin@pivotal.io
  CF_PASSWORD xxxxx
  GITHUB_USERNAME sashinpivotal
  GITHUB_OAUTH_TOKEN xxxx

  (when using pws pcf endpoint)
  CF_API_URL https://api.run.pivotal.io
  CF_ORG sashin-org
  CF_SPACE development
  CF_USERNAME sashin@pivotal.io
  CF_PASSWORD xxxxxxxx
  GITHUB_USERNAME sashinpivotal
  GITHUB_OAUTH_TOKEN xxxx
  
  (what gets displayed in the travis log)
  $ export CF_API_URL=https://api.run.pivotal.io
  $ export CF_ORG=sashin-org
  $ export CF_SPACE=development
  $ export CF_USERNAME=sashin@pivotal.io
  $ export CF_PASSWORD=[secure]
  $ export GITHUB_USERNAME=sashinpivotal
  $ export GITHUB_OAUTH_TOKEN=
  ```
     
- Travis supports running the job a specific branch by specifying it 
  in the `.travis.yml` file

  ```
  on:
    branch: my-own-branch
  ```
  
- In order to trigger Travis job without making code change, you can

  ```
  git commit --allow-empty -m "start a new job"
  git push
  ```
  
  A student also says clicking "retry job" option also worked.
     
## Trouble-shooting
   
-  *I got pcf deployment failure - you have to expand the arrow to
   see the failure - it was because the manifest file has a wrong
   domain (i.e. chicken vs evans)

   ```
   Installing deploy dependencies
   Successfully installed dpl-cloud_foundry-1.10.8
   Parsing documentation for dpl-cloud_foundry-1.10.8
   Installing ri documentation for dpl-cloud_foundry-1.10.8
   Deploying application

   The route allocations-pal-sang-shin.cfapps.io did not match any existing domains.
   FAILED
   Logging out sashin@pivotal.io
   OK
   Failed to push app
   failed to deploy
   ```
   
- *If everything worked fine in the 2nd phase but deployment
  tails.
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
  
- ?? What do you do with the following error? (I see several of
  these in students as well)
  
  ```
  $ echo "Downloading allocations server $RELEASE_TAG"
  Downloading allocations server release-28
  $ wget -P applications/allocations-server/build/libs https://github.com/$GITHUB_USERNAME/pal-tracker-distributed/releases/download/$RELEASE_TAG/allocations-server.jar
  
  ...

  HTTP request sent, awaiting response... 404 Not Found
  2019-11-07 15:00:20 ERROR 404: Not Found.
  The command "wget -P applications/allocations-server/build/libs  https://github.com/$GITHUB_USERNAME/pal-tracker-distributed/releases/download/$RELEASE_TAG/allocations-server.jar" exited with 8.
  ```
  
  It is because the Travis is looking for release-28 while
  the github has release-27 - you can edit the release number
  to correct it.
  
  Or "git push" does start the correct version. So in the
  Github, it generates release-29 skipping release-28.

## Challenge questions

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
    
## Challenges in the blud-green deployment
    
-   Is blue-green deployment suitable for major feature change?
-   What are the challenges for doing blue-green deployment?
    - Brad thinks blue-green deployment is possible for most cases
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

- Don't change the test code - that is the contract

- Demo how to remove compile errors also show what to do
  when there two compile 
  errors in a single line - you have to fix the one inside first
     
- Make sure TimeEntry constructor with the correct naming - 
  otherwise you will have hard time reading test code
  
- The reason we have a TimeEntry constructor that does not set id is because
  we want to simulate the repository behavior where id gets generated 
  by the persistence layer
  
- You can create an interface from a class - refactor->extract

- Make sure to add correct mockito version as described in the
  lab document
  
### InMemoryRepositoryTest

- How to set the `id` field of `TimeEntry` when it gets created 
  without `id` argument?

  - You can create `currentId` field

- When creating a code for `list` method, IDE generates 
  `boolean` return type   
  instead of `List<TimeEntry>` - you need to manually
  change `boolean` to `List<TimeEntry>`
    
- In the list() test, IntelliJ gets confused when there are 5 constructor
  arguments and there is already a constructor that takes 4 arguments.
  
- Object comparison with `equals` and `hashCode`  
  - leverage IDE support on this
  - Do you want to include id field?  Sure.

- Creating `List` object from `timeEntryMap.values()`

  - new ArrayList<>(timeEntryMap.values())

- `timeEntryMap.replace(id, timeEntry)` returns an old value not new value
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
  Chaning the setUp() method as following works.
  
  ```
    @Before
    public void setUp() {
        timeEntryRepository = mock(TimeEntryRepository.class);
        controller = new TimeEntryController(timeEntryRepository);
        MockHttpServletRequest request = new MockHttpServletRequest();
        RequestContextHolder.setRequestAttributes(new ServletRequestAttributes(request));
    }
  ```
  

## Local testing

- ??Running the application within the IDE even though my 2019.1
  is set to use Gradle Test Runner -  ?? need to try with 2019.2

  ```
  Caused by: java.lang.IllegalArgumentException: Could not resolve placeholder 'welcome.message' in value "${welcome.message}"

  ```

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

- What are the differences between unit testing vs integration testing vs end-to-end testing? 
  In “pal-tracker” project, which tests are unit testing?
  integrating testing or end-to-end testing?
- Can you do "integration" or "end-to-end" testing as part of
  CI/CD pipeline?
- What are differences between `RestTemplate` vs `TestRestTemplate`?
- When do you want to use `@SpringBootTest` vs `@ContextConfiguration`
  for your testing?
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
sudo snap install postman
```

- TDD presentation - https://www.youtube.com/watch?v=s9vt6UJiHg4

## Wrap-up discusson

- Discuss pros and cons of @Bean vs component scan
- Discuss pros and cons of using @Bean vs @Repository
- What is extra behavior of @Repository annotation provides
  to your code?

- *Brad went over the 12 factors - we covered 8 of
  12 factors so far
  

  
# Database Migration

## Talking points

- Talk about the need of migration
- Talk about service in PAS

## Tips

- Make sure to use double underscore when creating migration files
- *How do you see the list of services using brew?  `brew services list`
- When executing flyway command, username and password will be asked.
  Enter `tracker` and no password
  
## Slack channel tips

```
A couple of CF plugins I would recommend to install: “open” and “mysql” from https://plugins.cloudfoundry.org/

- “open”plugin opens a browser for you with the right route by typing “cf open pal-tracker”
- “mysql” plugin lets you access the mysql database service in the same way you were able to access your local mysql database by “cf mysql tracker-database”.

The installation instruction is right there in the website above. But they are as following:

cf install-plugin -r CF-Community “open”
cf install-plugin -r CF-Community “mysql-plugin”
```

## Student questions

- Can ssh enabled per space basis?

## Trouble-shooting

- *Somehow I could not display the shell output in the job #2 in
  in Travis.  It just showed the following with (3) on-going.
  
  ```
  (1) Job received (2) Queued (3) Booting virtual machine
  ```
  
  You just have to wait a bit.
  
  
## References

- [Migration stratgies](https://github.com/pivotal-bill-kable/spring-cloud-flyway-migration-demo)
- [Migration stratgies and best practices](https://www.talend.com/resources/understanding-data-migration-strategies-best-practices/)

# Spring JdbcTemplate

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
   
### Challenge questions

-   What are the two conditions that need to be met before
    Spring Boot's auto-configuration create DataSource bean
    that represents MySQL?

-   So when we are running our pal-tracker app locally and in Travis 
    with database, we have to provide database credentials (as 
    environment variables in our lab but could be from property
    file) but we did not have to do that when we are running
    the same application in PCF.  How is it done?  (Hunter
    talked about this.)
    
-   We know that when we are running pal-tracker app locally, Spring Boot
    creates a `DataSource` bean from the environment-variable provided
    database credentials, which is then used to create `JdbcTemplate`
    bean.  Now when we deploy the same application to PCF, 
    somehow different `DataSource`
    bean gets created from database credentials from the VCAP_SERVICES.
    How does PCF do this?
    
    ?? Spring cloud connector

## Wrap-up talking points

-   Self-service
-   No need to set up database credentials
-   Correct DataSource bean automatically created 
    depending on where the application gets deployed

# Actuator

## Tips
   
- The META-INF/build-info.properties is under build/resources/main directory

- The code in the HealthApiTest below is not needed - you will
  need @Autowired TestRestTemplate, then.

  ```
    @Before
    public void setUp() throws Exception {
        RestTemplateBuilder builder = new RestTemplateBuilder()
                .rootUri("http://localhost:" + port)
                .basicAuthorization("user", "password");

        restTemplate = new TestRestTemplate(builder);
    }
  ```
   
## Talking points

- For /health value proposition, talk about the case "applicatio hang" - GC hang - CF does just port health check

## Trouble-shooting

- * HealthApiTest fails due the following reason even though 
  accessing the endpoint from a browser works fine. Why?
  It was because I reversed the up() and down() logic.

  ```
  org.junit.ComparisonFailure: expected:<[200]> but was:<[503]>
  ```

## Prometheus 

- Try prometheus from the [following instruction](https://github.com/sashinpivotal/spring-boot-actuator-micrometer)
  - Ignore the part of `setting actuator/prometheus endpoint` since
    pal-tracker is not using security at the moment 
  
# Scaling lab

- Auto-scaling lab, in the Recent History, you will see something

  ```
  Scaled up from 2 to 3 instances. Current HTTP Latency of 35.92ms is above upper threshold of 3.00ms.
  ```

- ?? When applying auto-scaling, what is is "Percent of traffic to apply - 95% or 99%"?

# App Continnum

## Talking points

- Delay architectural decision to as latest point as possible (Mike)
- Use a single repository for multiple applications as long as possible
  - It is easy to move around domains between applications
  

# Distributed System

## Talking points

-   Explain what the `${USER_ID}` and `${PROJECT_ID}` variables for 
-   Describe the relationship among the 4 apps
-   Describe how to change the http://FILL_ME_IN - registration server
    endpoint is something you configure in the manifest.yml file 
    of the registration server
-   Demo how to use httpie or postMan

## Code review

-   Whenever a new `backlog`, `allocation`, `timesheet` needs to 
    be created, backlog, allocation, and timesheet application has 
    to know if a corresponding `Project` is already enabled or not. 
    
-   Each of these components (backlog, allocation, timesheet) has
    controller class in which it uses `projectIsActive` method
    
    ```
    @PostMapping
    public ResponseEntity<AllocationInfo> create(@RequestBody AllocationForm form) {

        if (projectIsActive(form.projectId)) {
            AllocationRecord record = gateway.create(formToFields(form));
            return new ResponseEntity<>(present(record), HttpStatus.CREATED);
        }

        return new ResponseEntity<>(HttpStatus.SERVICE_UNAVAILABLE);
    }
    
    private boolean projectIsActive(long projectId) {
        ProjectInfo project = client.getProject(projectId);

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
  
- [Postman collection](https://github.com/pivotal-bill-kable/cnd-postman-collections)
  
## Challenge questions
  
- Why are we using a single repository for all 4 microservices?  
  Isn't it a violation of the first rule of 12 factor app? 

- Why are there variations of a domain class, for example,
  why are there `TimeEntryForm`, `TimeEntryInfo`, `TimeEntryRecord`, `TimeEntryFields` classes?
  Where are they used?
  
- In the "pal-tracker-distributed", we use 4 different databases, one for
  each application. 
  - Is it a recommended practice?  Should we have a single database instead?
  - Is it possible to have database inconsistency among the databases if
    there are multiple databases? 
    If it is not possible, what is our alternative?
    (For example, a user is deleted in User database, how does other
    databases reflect that change?)
  - Is it OK to have duplication among the multiple databases?
    (In 'pal-tracker-distributed", we don't have any duplcate data.)

- Application code should be insulated from data access logic?
  How do we achieve that in the "pal-tracker-distributed"? 
  
## Trouble-shooting

- *Somehow `Travis` deployment fails 

  ```
  The command "wget -P  ... exited with 0.


  Deploying application
  failed to deploy
  ```
  
  It was because I was using wrong domain `chicken` instead of `evans`.
  Expand the downward arrow to see what is being used:
  
  
  ```
  Deploying application
  Pushing from manifest to org sashin.pivotal.io / space sandbox as sashin@pivotal.io...
  Using manifest file /home/travis/build/sashinpivotal/pal-tracker-distributed/manifest.yml
  Getting app info...
  The route backlog-pal-sang-shin.apps.chicken.pal.pivotal.io did not match any existing domains.
  FAILED
  Logging out sashin@pivotal.io...
  OK
  Failed to push app
  ailed to deploy
  ```
  
  You have to change both route and registration server address
  
  ```
  applications:
  - name: tracker-timesheets
    path: ./applications/timesheets-server/build/libs/timesheets-server.jar
    routes:
    - route: timesheets-pal-sang-shin.apps.evans.pal.pivotal.io
    memory: 1G
    instances: 1
    env:
      REGISTRATION_SERVER_ENDPOINT: http://registration-pal-sang-shin.apps.evans.pal.pivotal.io
      JBP_CONFIG_OPEN_JDK_JRE: '{ jre: { version: 11.+ } }'
    services:
    - tracker-timesheets-database
  ```
  

# Service Discovery

## Talking points

-   This lab has a lot of moving parts: service discovery/registration,
    client side load-balancing, spring cloud dependencies, end-to-end 
    testing.

-   Service discovery
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

- apps.evans.pal.pivotal.io is using the following


  ```
  curl https://spring-cloud-broker.apps.evans.pal.pivotal.io/actuator/info
  ```
  
  ```
  {
   "git" : {
      "commit" : {
         "id" : "fd850cb",
         "time" : "2019-04-26T15:15:37Z"
      },
      "branch" : "HEAD"
   },
   "build" : {
      "time" : "2019-05-03T15:52:33.869Z",
      "artifact" : "spring-cloud-service-broker",
      "group" : "io.pivotal.spring.cloud",
      "version" : "2.0.8-build.5",
      "name" : "service-broker"
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
   
- Example

   ```
   springCloudVersion = SPRING_CLOUD_VERSION
   springCloudServicesClientLibrariesVersion =   SPRING_CLOUD_SERVICES_CLIENT_LIBRARIES_VERSION
   ```
   
   ```
   springCloudVersion = "Finchley.RELEASE"
   springCloudServicesClientLibrariesVersion = "2.0.3.RELEASE"
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
   build.gradle.  Is this recommended practice? 
   
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

- ?? I get the following error when deploying the app

  ```
  2019-11-07T10:17:53.13-0500 [APP/PROC/WEB/2] OUT Caused by: java.lang.NoClassDefFoundError: org/springframework/cloud/config/client/ConfigServicePropertySourceLocator
  ```

# Circuit breaker

## Talking points

-   The @Hystrix command needs to be duplicated in 3 different places -
    there is a reason for this  
    
## Tips

-   The console for the evans is "login.sys.evans.pal.pivotal.io"

## References

-   [Circuit breaker diagrams](https://github.com/Netflix/Hystrix/wiki)
-   [Hystrix dashboard](https://github.com/Netflix-Skunkworks/hystrix-dashboard/wiki)

## Misc

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
  
## Challenge questions (Circuit breaker lab)

- Can @Hystrix command can be chained?
- When is the suitable usecase where circuit breaker can be used?
  Can it be used for non-idempotent operations?
- How would you handle a case where dependency service simply
  timed out and the calling service's threads get depleted
  (as shown in the [3rd figure in the https://github.com/Netflix/Hystrix/wiki](https://github.com/Netflix/Hystrix/wiki))?

    
# Securing Distributed Application

## Talking points

## Demo steps

-   Use `security-solution` as base code
-   Change 4 manifest files to reflect correct route
-   Make sure to create services manually at PCF

## Trouble-shooting tips

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
   
- I see p-identity with both uaa and p-identity plans. Which should
  we use?  I used uaa and it worked fine.  
  ?? When a student used `System` plan within the `App manager`, 
  then it did not work.

   ```
   p-identity        uaa, p-identity   Provides identity capabilities via UAA as a Service
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

-  Getting token from UAA

   ```
   cf env tracker-registration
   curl -k https://login.sys.evans.pal.pivotal.io/oauth/token -i -u 04f5dae7-0f07-47ca-9776-71e681cb6110:29e9bca4-d08a-47e6-af3c-d30eacf4efd2 -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=client_credentials&response_type=token'
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
	curl -i -XPOST -H"Content-Type: application/json" localhost:8083/projects -d"{\"name\": \"Project B\", \"accountId\": \"1\"}"
	
	// create allocation assuming projectId is 2
	curl -i -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer 82e595e2-62c2-4581-92d1-fe104acbc5b2" localhost:8081/allocations/ -d"{\"projectId\": \"2\", \"userId\": \"1\", \"firstDay\": \"2015-05-17\", \"lastDay\": \"2015-05-18\"}"
	```
	
- Perform operations in PCF using remotely acquired token

   ```
   // get a token from UAA
   cf env tracker-allocation
   curl -k https://login.sys.evans.pal.pivotal.io/oauth/token -i -u ea47b39b-06ab-4c01-a961-d3cec5c6be8f:7ffbc342-d529-42fc-8868-17b897509f1b -X POST -H 'Accept: application/json' -H 'Content-Type: application/x-www-form-urlencoded' -d 'grant_type=client_credentials&response_type=token'
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

## Challenge questions

-   It is a good practice to save security-sensitive data such as
    passwords in the config server? If not, what can we do?
    
-   What happens when a config server is not available?
    
-   Is it a good practice to maintain configuration data in a
    single repository for multiple environments?

## Trouble-shooting

- Setting the management include thing in the manifest files
  with just * fails - use `"*"` not just `*`

## Tips

- Creating `tracker-config-server` service instance in PCF

  ```
  cf create-service p-config-server standard tracker-config-server -c "{\"git\": {\"uri\": \"https://github.com/sashinpivotal/tracker-config.git\", \"label\": \"master\"}}"
  ```
  
- Creating bootRun and