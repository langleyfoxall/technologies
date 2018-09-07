# Web Quality Assurance Handbook

Test extensively against assumptions in Jira, at the end of the day this is what the client is paying for. Below is a list of bullet points for common individual sections of a Laravel web app, although a lot of the core concepts apply regardless of web technology used (events bus, queues etc are all common design patterns)

It should be used as a guide to ensure a great & consistent experience for the end user.

## Blackbox

### General

- All UI scales well and looks good on small form factor devices
- All errors are handled and UI reacts appropriately
- Errors are clear in meaning & reflect what happened
- Activity indicators are used when loading data async
- Empty information is handled correctly in UI (optional fields etc)
- Long running operations give a indication of progress if possible
- Breadcrumbs are used where appropriate

### Navbar

- UI reflects the current active page
- Icon (if applicable) is appropriate for the current page

### Forms

- Invalid inputs correctly trigger validation errors
- All form inputs have associated labels
- Appropriate validation for different inputs (phone number, postcode)
- The forms are not too long & and are grouped logically
- The user is alerted of the form lifecycle (success, error)
- When modals are used in the context of updates, ensure inputs are correctly pre populated.
- Autofill is disabled on inputs where appropriate
- Inputs have correct type property ( emails have email type, phone numbers have tel type)


### Modals

- Modals are animated on both display and dismiss
- Modals are used where appropriate over pages

### Formatting

- Dates are formatted correctly for the appropriate audience.
- Monetary values are formatted correctly for the appropriate audience
- Phone numbers are formatted correctly for the appropriate audience

### Pagination

- UI correctly indicates current page
- UI shows at least 2 page tabs ahead and below the current page

### Login & Auth

- User can only access protected pages when they are logged in & have appropriate permissions
- Login & Logout works as expected
- Reset password works as expected

### Registration
- Email addresses are verified & unique (if applicable)
- Passwords meet minimum standards (min 8 chars)
- Passwords should not have maximum length restrictions (allow at most 255 characters).

### Emails
- Emails look good on small form factor devices
- Ensure correct subject & sender name
- Correct email is sent, information is conveyed appropriately
- Emails are received in a timely manner
- Emails come from the appropriate email (often the clients)
- Links point to the correct address

### Permissions & Roles

- Permissions & Roles
- Ensure permissions & roles match up to possible actions (only admins can create users etc)

## WhiteBox

### General

- File names must follow standard coding conventions (UsersController.php)
- Classes must follow standard coding conventions (UsersController)
- Variables should follow camelCase & be descriptive (myName)
- Ensure each function does not go over 250 lines
- All long running operations (at your discretion) are queued
- APIs follow REST architecture as closely as possible
- Auth middleware is setup & working correctly
- Event system is used for method side effects (Audit trail etc)
- Laravel Notifications are used to notify the user of system events (subscription expired, new friend request etc)
- Sensitive values are either hashed or encrypted (when required by law or common sense)
- Third party API integrations that can & will be re-used across projects should be implemented as external packages, assuming no existing open-source integration exists, to allow for independent testing and code reuse if appropriate.
- Ensure third party API keys (e.g. SES keys) are not present within .env.example and other relevant files outside of the production / development environments.

### Controllers

- Be on the lookout for duplicated code - recommend refactoring into helper classes or models if so
- Ensure all requests are validated using a custom request
- Errors are handled correctly in try catch blocks
- Responses are returned in a consistent & logical format
- Only appropriate & relevant information is returned
- When returning JSON ensure the returned JSON conforms to the JSON spec (http://json-schema.org/specification.html)
- Appropriate status codes are set

### Emails

- Emails use the SES driver unless agreed beforehand
- All emails are queued up for sending
- Only relevant information is passed to the mailable instance

### Views

- Loading of assets (js/html) use the `asset` global helper
- Blade layout system is used where appropriate (@extends, @yield)
- Components are split out logically where appropriate, make use of Laravel’s powerful blade templating system if appropriate (clientCard, navbar etc)

### Service Providers

- Service Providers are utilised where appropriate to bind classes into the container (API interfaces etc)

### File Storage

- Files are stored on S3 unless requested by the client to be stored locally or agreed otherwise beforehand by the project manager
- Ensure appropriate permissions on files in applicable (sensitive documents are private, avatars are public etc)

### Queues

- Queues use Redis unless agreed beforehand by the project manager
- Ensure appropriate measures are in place for handling failed jobs

### Sockets

- When using PHP, sockets are integrated using Laravel Echo unless agreed beforehand by the project manager
- Ensure appropriate authentication & security for each connection

### Database

- All migrations use foreign keys for relations to ensure database integrity
- SQL data types are appropriate
  - Monetary values should either be stored in pence as an INTEGER or as a DECIMAL - Never a FLOAT
  - Long strings (descriptions) should be stored as TEXT, other string can be stored as a VARCHAR - Ensure controller validation for VARCHAR fields have a max string length of 255
  - Tables are named appropriately with underscores in lieu of other word separators
  
  
### Cache

- Ensure appropriate values are cached where appropriate.

### Continuous Integration

- Is used, even if it's just a basic setup
- If Travis CI is being used, ensure third party API keys are input directly into Travis CI’s website relevant to the project and make sure “Display value in build log” is not checked.