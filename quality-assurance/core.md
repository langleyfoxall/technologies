# 🚦 Langley Foxall Quality Assurance

When building applications that run an entire business end-to-end - it's important that we adhere to high quality
assurance standards in order to consistently deliver a high quality software project.

There are different parts/processes to quality assurance as a whole, and these are not limited to just manual testing and
automated testing.

*   [What makes a good web application?](#what-makes-a-good-web-application?)
    *   [Blackbox](#blackbox)  
    *   [Whitebox](#whitebox)  
*   [Processes](#processes)
    *   [Stages of Testing](#stages-of-testing)  
        *   [Automated Testing](#automated-testing)
        *   [Manual Testing](#manual-testing)
    *   [Whitebox](#whitebox)  

## What makes a good web application?
The following is a checklist of things to think about both during development of a product and during the quality 
assurance phase.

### Blackbox
**General**
* All UI scales well and looks good on small form factor devices
* All errors are handled and UI reacts appropriately
* Errors are clear in meaning &amp; reflect what happened
* Activity indicators are used when loading data asynchronously
* Empty information is handled correctly in UI (optional fields etc)
* Long running operations give a indication of progress if possible
* Breadcrumbs are used where appropriate

**Navbar**
* UI reflects the current active page
* Icon is appropriate for the page

**Forms**
* Invalid inputs correctly trigger validation errors
* All form inputs have associated labels
* Appropriate validation for different inputs (phone number, postcode)
* The forms are not too long &amp; and are grouped logically
* The user is alerted of the form lifecycle (success, error)
* When modals are used in the context of updates, ensure inputs are correctly pre populated.
* Autofill is disabled on inputs where appropriate
* Inputs have correct type property ( emails have email type, phone numbers have tel type)

**Modals**
* Modals are animated on both display and dismiss
* Modals are used where appropriate over pages

**Formatting**
* Dates are formatted correctly for the appropriate audience.
* Monetary values are formatted correctly for the appropriate audience
* Phone numbers are formatted correctly for the appropriate audience

**Pagination**
* UI correctly indicates current page
* UI shows at least 2 page tabs ahead and below the current page

**Login &amp; Auth**
* User can only access pages that require 
* Authentication when they are logged in
* Login &amp; Logout works as expected
* Reset password works as expected

**Registration**
* Email addresses are verified &amp; unique (if applicable)
* Passwords meet minimum standards (min 8 chars)
* Passwords should not have maximum length restrictions (allow at least 255 characters).

**Emails**
* Emails look good on small form factor devices
* Ensure correct subject &amp; sender name
* Correct email is sent, information is conveyed appropriately
* Emails are received in a timely manner
* Emails come from the appropriate email (often the clients)
* Links point to the correct address

**Push Notifications**
* Push notifications are received in a timely manner
* They show correct &amp; relevant information

**Permissions Roles**
* Ensure permissions &amp; roles match up to possible actions (only admins can create users etc)

### Whitebox
**General**
* Filenames must follow standard coding conventions (UsersController.php)
* Classes must follow standard coding conventions (UsersController)
* Variables should follow camelCase &amp; be descriptive (myName)
* All long running operations (at your discretion) are queued
* APIs follow REST architecture as closely as possible
* Auth middleware is setup &amp; working correctly
* Event system is used for method side effects (Audit trail etc)
* Laravel Notifications are used to notify the user of system events (subscription expired, new friend request etc)
* Sensitive values are either hashed or encrypted (when required by law or common sense)
* Third party API integrations that can &amp; will be re-used across projects should be implemented as external packages, 
assuming no existing open-source integration exists, to allow for independent testing and code reuse if appropriate.
* Ensure third party API keys (e.g. SES keys) are not present within .env.example and other relevant files outside of the 
production / development environments.
* If Travis CI is being used, ensure third party API keys are input directly into Travis CI's website relevant to the 
project and make sure "Display value in build log" is not checked.
* Log viewers are hidden behind a protected route

**Controllers**
* Ensure each controller function does not go over 250 lines
* Be on the lookout for duplicated code - recommend refactoring into helper classes or models if so
* Ensure all requests are validated either through a validator or custom request
* Errors are handled correctly in try catch blocks
* Responses are returned in a consistent &amp; logical format
* Only appropriate &amp; relevant information is returned
* When returning JSON ensure the returned JSON conforms to the JSON spec (http://json-schema.org/specification.html)
* Appropriate status codes are set

**Emails**
* Emails use the SES driver unless agreed beforehand
* All emails are queued up for sending
* Only relevant information is passed to the mailable instance

**Views**
* Loading of assets (JS/HTML) use the `asset` global helper
* Blade layout system is used where appropriate (@extends, @yield)
* Components are split out logically where appropriate, make use of Laravel's powerful blade templating system if 
appropriate (clientCard, navbar etc)

**Service Providers**
* Service Providers are utilised where appropriate to bind classes into the container (API interfaces etc)

**File Storage**
* Files are stored on S3 unless requested by the client to be stored locally or agreed beforehand
* Ensure appropriate permissions on files in applicable (sensitive documents are private, avatars are public etc)

**Queues**
* Queues use Redis unless agreed beforehand
* Ensure appropriate measures are in place for handling failed jobs

**Broadcasting**
* Broadcasting uses Laravel Echo unless agreed beforehand
* Ensure appropriate authentication & security for each channel

**Database**
* All migrations use foreign keys for relations to ensure database integrity
* SQL data types are appropriate
* Monetary values should either be stored in pence as an INTEGER or as a DECIMAL - Never a FLOAT
* Large tables that are queried often are indexed in order to keep database speed up

## Processes
### Automated Testing
#### Unit Testing
Unit tests are to be utilised more so in our packages than in full products.
#### Integration Testing
Integration tests are to be utilised more so in our full projects than in our packages.
#### Browser Testing
TBC

### Manual Testing
#### 1 - Developer Testing
During the development of the project, developers will create `feature/*` branches for all features going into the software.
After the initial feature development - the developer should manually test their feature after writing passing 
[automation tests](#automated-testing). This phase should also include a check that ensures the feature does not infringe
any of the items listed in the ["What makes a good web application?"](#what-makes-a-good-web-application?) section. 

Once the feature has the thumbs up from the developer - that is when the pull request into the `master` branch should be
made. 

The developers should log any bugs found in this phase into JIRA to improve their ratio of bugs they find VS bugs that
get through to the QA team/customer. 

#### 2 - Sprint Testing
At the end of each sprint the Lead Developer on the project should arrange some time with a member of the QA team to 
manually test all completed user stories in that sprint.

They should look to give the 

OLD: 
At the end of each sprint a member of QA team will look to test the code that is pushed to the `staging` branch. 
This is to ensure that it is working and there are not bugs in the relevant area. 

This is more of a Spotlight Check, testing around each change that has been made and near areas that could be 
affected by this change, this will have a high density of testing to ensure that we catch as many bugs as possible, 
no matter how small or unlikely the bug appears all bugs must be reported and fixed before the code goes to `staging`.

QA should look to test all assumptions that were marked as completed in that sprint by the developers. 

#### 3 - M2P (Production) Testing
--NEED TO REWORD--

Finally, M2P testing is large end to end tests. This means that in terms of testing, we start of as a brand new 
user, with a cleared database (as much as can be cleared), This testing will go through the flows the customer will 
follow, This will require multiple user type testing such as (Client, Admin, User, Engineer, Ect..), This will span 
through to an App if the customer has an App, Even if no changes have been made to the App. This will ensure that the
customer flow will be clear and will be able to with confidence be able to say that this project works.