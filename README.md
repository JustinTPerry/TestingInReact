# TestingInReact

Getting familiar with testing within React. <br>

Given a Feedback Form for the mock restaurant Little Lemon Restaurant, I was instructed to create tests for their form submission. The conditions are as follows:

> If the customer's rating is less than 5, they are required to submit feedback no less than 10 characters long. If the rating is greater than or equal to 5 then no additional feedback is required from the customer.

## Step 1

For the first test: <br>
**User is able to submit the form if the score is lower than 5 and additional feedback is provided.** <br>
The test _score_ is given as "3" and the test _comment_ is given as "The pizza crust was too thick."

A _handleSubmit_ variable is created to hold the Jest function _jest.fn()_ and the feedback form component is rendered with the onSubmit prop assigned to the _handleSubmit_ function.

## Step 2

A variable is created to hold reference to the range input which is obtained through the screen method, _getByLabelText_ and passing in, _/Score:/_ (The label just before the range input is structured as follows in the _FeedbackForm_: Score: {score} ⭐).

Given the range input reference we're able to fire the change event passing in the input reference and the target value provided to us previously in the form of _score_, whose value is "3".

## Step 3

The same process is repeated for the text area input and assigned the value provided to us previously in the form of _comment_ whose value is "The pizza crust was too thick."

## Step 4

A reference to the submit button is retrieved through a similar process as the previous two, except the method on the screen that's invoked is _getByRole_ (It should be noted this method is used to retrieve the submit button in this case, because the form contains a single button whose responsibility is to submit the form.) and passed the value "button".

Once a reference is obtained, the next action is to fire a clicked event with a reference to the submit button.

## Step 5

It's crucial now that we tell the test to expect the _handleSubmit_ function to be called with the _score_ ("3") and _comment_ ("The pizza crust was too thick.") variables.

### **Important**

It should be noted that when this test is run, it results in a pass.

## Step 6

The above processes are implemented for the second test:<br>
**User is able to submit the form if the score is higher than 5, without additional feedback.** <br>
The test _score_ is given as "9" and the test _comment_ is not provided, because the test should pass given no additional comment.

The second part of step 1 is repeated as well as step 2, and step 4.

## Step 7

We tell the test to expect the _handleSubmit_ function to be called with _score_ ("9") variable as well as telling the test to expect a _comment_ with the value of an empty string.

### **Important**

It should be noted that when this test is run, it results in a pass.
