# 🚦 Langley Foxall Quality Assurance

When building applications that run an entire business end-to-end - it's important that we adhere to high quality
assurance standards in order to consistently deliver a high quality software project.

There are different parts/processes to quality assurance as a whole, and these are not limited to just manual testing and
automated testing.

*   [What makes a good web application?](#what-makes-a-good-web-application)
    *   [Blackbox](#blackbox)  
    *   [Whitebox](#whitebox)  
*   [Processes](#processes)
    *   [Automated Testing](#automated-testing)
    *   [Manual Testing](#manual-testing)

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
* An icon that is appropriate for the page (if applicable)

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
* Users can only access pages they are permitted access to.
* Authentication when they are logged in
* Login, registration (if applicable) and logout works as expected.
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
* Links point to the correct URIs

**Push Notifications**
* Push notifications are received in a timely manner
* They show correct &amp; relevant information

**Permissions Roles**
* Ensure permissions &amp; roles match up to possible actions (only admins can create users etc)

### Whitebox
**General**
* Filenames must follow standard coding conventions (UserController.php)
* Classes must follow standard coding conventions (UserController)
* Variables should follow camelCase &amp; be descriptive (myName)
* All long running operations (at your discretion) are queued
* APIs follow REST architecture as closely as possible and implement our [API Response](https://github.com/langleyfoxall/helpers-laravel#apiresponse)
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
* When returning JSON ensure the returned JSON conforms to the [JSON spec](http://json-schema.org/specification.html)
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

Automated testing should be implemented in a way to confirm functionality specified by the client.
To this end, automated tests should be created to confirm the project user stories and related 
business logic is satisfied and correct. 

#### Unit Testing

Our current policy is that unit tests should be used for:

* Testing of project business logic / rules, that are able to be sufficient abstracted
* Testing of packages, including our open source work

#### Integration, Browser &amp; End-to-End Testing

Integration, browser and end-to-end tests should be used for:

* Testing of project functionality related to client specified user stories
* Testing of critical path functionality, such as the register, login, and checkout process of an
ecommerce site

Since end-to-end tests are slower than browser tests and browser tests are slower than integration 
tests, you should ideally aim to use the fastest possible test type, if appropriate.
### Manual Testing
#### 1 - Developer Testing
During the development of the project, developers will create `feature/*` branches for all features going into the software.
After the initial feature development - the developer should manually test their feature after writing passing 
[automation tests](#automated-testing). This phase should also include a check that ensures the feature does not infringe
any of the items listed in the ["What makes a good web application?"](#what-makes-a-good-web-application) section. 

Once the feature has the thumbs up from the developer - that is when the pull request into the `master` branch should be
made. 

The developers should log any bugs found in this phase into JIRA to improve their ratio of bugs they find VS bugs that
get through to the QA team/customer. 

#### 2 - Sprint Testing (On the master branch)
At the end of each sprint the Lead Developer on the project should arrange some time with a member of the QA team to 
manually test all completed user stories in that sprint.

They should look to give the functionality a complete test, using any available acceptance criteria provided with the 
story. Testers should also ensure that the UX seems correct, that all inputs are validated correctly and data is
retained where appropriate.

#### 3 - S2P Testing (Staging server) 
Staging to production testing should be focused around the user flow of the system. 

Users should start with a fresh, clear database and work on the journey of the system end-to-end. Using the different 
user types, the tests should ensure that the customers workflow is satisfied from input to output.
