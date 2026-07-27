---
tags:
  - AppDev/Design
---
# Mobile App Forms

Forms are used to gather input from the user.

- Good form design in invaluable.
- Form design on mobile is even trickier, it must be correct.
- Form abandonment can be costly on infrastructure.

A form should always strive for a stellar UX. (user experience)

## Types of Forms

| Form Type     | Description                                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------------------------------- |
| Sign in Forms | Simply the interface where the user passes in a username and password for authentication. 1 page handling is ideal. |
|               |                                                                                                                     |
## Sign in Form Considerations

- Auto-focus on the first form field to save a user input, UX will greatly increase.

- The password field should be *masked*. This obscures the password, additionally it should be a legitimate mask. 

	*i.e. copy/paste outside of the form, or inspection with DevTools will not reveal the password contents*

- The password field can have an option to *unmask* the field so the user can verify input. Often in the form of a show/hide toggle.

- Sign in should be *accessible*. Throughout the app it sign in/sign up should be clear and quickly activate-able for users who have not authenticated. This is a UX goal ***not*** a advertising goal.

- **Delay sign in** - common in shopping apps, get out of the way of the user. Allow the user to engage immediately with the app and at the time of purchase prompt for sign in/sign up.

## Field Verification

Critical fields, such as email and password often require a second input for validation. To save the user time you can setup opt-in validation.

Rather than 2 prompts for the same field, the user can tap to reveal their password to self validate. Similarly, for an email the UI can prompt the yes to confirm yes/no that the input email is valid by display their input again on screen.

In general, I would argue forced second field inputs are better - at the very least for the password. I do not hate this alternative for the email field.


## Form Design

Vertical field labels are generally best. They will avoid overlapping field/input areas and general truncation.

Pre-populating an input field with a *hint* is another option to convey meaning and will allow labels to be thrown away. 
	*e.g. A blank text box with no label, with a faint "email address" text placeholder in the text box. This value should wipe entirely at the first user input.*

Intentions for field requirements should be communicated. Think password requirements, the user should not have to discover after the fact that specific restrictions are in place after failing a form submission.


## UX / User Experience

#### Communicate Operations
At form submission, the UI should reflect that it's "thinking" to communicate to the user that the app is functional and processing their request.

#### Communicate Progress
For a multi-stage form, communicate through the UI the progress. (e.g. 1/6 in the top banner, a phase snapshot with a drill down, or communicating the whole process ahead of time)

#### Stay in the App
Keep the user within the application at all times. The user should not have to access an external app to sign up etc. Any operation that requires the user to exit the app, will likely result in the user not returning.

#### Give Direction
If a user commits an action that is invalid and would traditionally result in no UI change, communicate the issue in a secure way with clear next steps.
	*e.g. A user attempts to sign up but the email is already in use, communicate this and send a recovery link to the existing email address*

#### Navigation
The user should be able to proceed forward and backward throughout a multi-stage form to adjust input. This navigation should follow standard intuitive navigation patterns.

#### Data Prepopulation
For returning users, and even guest users without accounts, populate as much data as possible in forms to save the user time and improve the UX.

#### Stay Mobile Focused
Throw out any web conventions, as web should be viewed and developed for your app as a separate platform. Mobile solutions should be developed exclusively.

#### Long Forms
For forms that cannot fit on one page, consider a top level form with expandable, drill down options. Alternatively or concurrently, make a form that is scroll-able rather than routing to a second page.