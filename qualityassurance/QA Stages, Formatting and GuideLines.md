# 📚 QA Testing Stages, Formatting and GuideLines

This Section is to instruct on when to test, how you should be formatting the Bugs raised and GuideLines for QA

## Developing with QA in mind

### Commands
When you are developing the project the project might require commands to run and work correctly, these can range from simple set up commands to automatic updating commands, a list of these commands and a breif description of what these commands do will help QA move more smoothly and avoid raising unnecessary questions.

Some projects requires certain status or manipulation of the database to update systems and cause it to do the next stage/part of the system to test. We would like these to be formed into Commands, QA should not need to touch the database side to test the system, this leads to user error and this is leading it away from how the customer would user the system. So these processes need to put into commands where it will update the database for the required data with the correct process to ensure that it is changed to how the system will change it when on live.

### ENV
Ensure that the 'env.example' is update and remove redundant fields/areas that are not required anymore.
		
## QA Stages

For staging we are following a multi stage testing to enable us to ensure that the customer is getting a bug free and fully functioning system. This will be a merge between Agile and Waterfall.
										
### Stage 1 - Dev Testing:
This stage is for the Developers to test and ensure that there are not obvious bugs and that the code is working as expected before they create a PR (Pull Request), This will ensure that QA is not wasting time on obvious bugs that could have easily been spotted during development and be fix them before the pull request is made.
												
### Stage 2 – PR (Pull Request) Testing:
At this stage the PR has been created and this requires 2 steps of acceptance.
One check will be from a member of the Developer Team to check over the code is to review the code itself. 
The other Check will be from QA, that will test the code changes itself, ensure that it is working and there are not bugs in the relevant area. This is more of a Spotlight Check, testing around each change that has been made and near areas that could be affected by this change, this will have a high density of testing to ensure that we catch as many bugs as possible, no matter how small or unlikely the bug appears all bugs must be reported.
Once Both parties have accepted the code we will then go onto Stage 3.
												
### Stage 3 – M2S (Master to Staging) Testing:
This area of testing is large end to end testing, This means that in terms of testing, we start of as a brand new user, with a cleared database (as much as can be cleared), This testing will go through the flows the customer will follow, This will require multiple user type testing such as (Client, Admin, User, Operative, Ect..), This will span through to an App if the customer has an App, Even if no changes have been made to the App. This will ensure that the customer flow will be clear and will be able to with confidence be able to say that this project works.

### Stage 4 - Prod Testing:
This area of testing is to test all key functionally of the application on prod to ensure that the application can function and does function as expected.
If any issues are found on Prod these need to be raised as a HotFix request and to ensure that it get fixes as soon as possible.

#### Staging - Prod Merge Timing
Timing is a very important point in the merge between Staging and Prod, We do not want to do it at peak working hours as if something does go wrong it doesn't effect our customers and doesn't impact on our relationship to them. We also do not want to do it on a Friday or before any period that we will not be in the office for a few days. As we want to be able to fix the issue as fast as possible and not make the customer wait. Preferably this merge would be done at night with both Q/A and Dev in incase something does need fixing, But this is not possible. Every customer is different to when it would be best to merge, So ask if in doubt ask the project lead or a manager to when they would advise the merge.

## Test Data
When testing on Staging and Prod we will require valid data and logons to access the system. These should be stored in a Google Docs that the Project Lead/Manager should have access to, These should be kept up to date. This should contain data that you need or is helpful to have when you are testing the given project. 

## Test Cycle

Test cycles are a collection of tests that need to be ran. Cycles should always be given a time frame and a time estimate to ensure that we are completing them in a timely manner and to enable management to work out work flows.

### Tests
For Stage 2, Stage 3 and stage 4, a list of tests is required, this is to keep track of what needs to be tested and to ensure that all functionality is tested and to ensure we don't do any unnecessary testing.
The structure of the tests are as follows:
- Test Name
- Priority
    - Critical
    - High
    - Medium
    - Low
- Expected Outcome
- Estimated time to complete testing
- Area of Testing (Such as the what Pages/Screens)
- Test Data (If Required)

### Testing Status
Each test requires a status once completed. The Status are as follows;
- Passed – The testing passed and has been confirmed to work as expected.
	- Data Required 
		- Notes.
		- Test data used.
		- Screenshots if relevant.
		- Your Name.
- Failed – The testing failed and is not working as expected.
	- Data Required
		- Notes.
		- Test Data used.
		- Bug Number Raised.
		- Your Name.
- Blocked – Testing has not been started as can’t be tested due to a Bug Already Raised by a failed test.
	- Data Required
		- Notes.
		- Bug Number Raised.
		- Your Name.
- OOS (Out of Scope) – Test has been moved to OOS as it is not in the scope of testing for this Stage of Testing.
	- Data Required
		- Manager who confirmed OOS.
		- Your Name.

### Raising A Bug

When you find a bug, you will need to raise a bug on the Jira Service Desk.
This bug will require multiple areas to be filled in, these are as Below:

![Jira Bug Raising](images/jira/raising-bugs.PNG)
