# Cucumber Style Guide


## Table of contents

1.  [Principles](#principles)
2.  [Organization](#organization)
3.  [Naming](#naming)
4.  [Writing Scenarios](#scenarios)
5.  [Links / References](#links)


<a name="principles"></a>
## 1. Principles

> The point of writing Cucumber tests is to create a specification about what the code does that can be understood by the people on your team who can't read code.
> Keep your step descriptions as uncoupled to the interface as possible. Features are not meant to be tied to one particular implementation. Implementation is handled in the step definition.


<a name="organization"></a>
## 2. Organization

* Helper methods go in `/features/helpers`
* Step definitions & Step descriptions should be organized by functionality
* 1 feature per step description file
* The name of the *step description* file should describe the feature (e.g. `cancel_order.feature`)
* The name of the *step definition* file matches the step description (e.g. `cancel_order_steps.rb`)

Example directory structure:
```
  /features
    /helpers
      form_helpers.rb
    /step_definitions
      /admin
        update_catalog_steps.rb
      /online_ordering
        shopping_cart_steps.rb
        check_out_steps.rb
        check_order_status_steps.rb
      /order_fulfillment
        modify_orders_steps.rb
        cancel_order_steps.rb
        edit_order_steps.rb
        ship_order_steps.rb
    /step_descriptions
      /admin
        update_catalog.feature
      /online_ordering
        shopping_cart.feature
        check_out.feature
        check_order_status.feature
      /order_fulfillment
        modify_orders.features
        cancel_order.feature
        edit_order.feature
        ship_order.feature
    /support
      env.rb
```


<a name="naming"></a>
## 3. Naming

Let's build a vending machine application. Here is an example feature:

```
Feature: Serve coffee
  Coffee should not be served until paid for
  Coffee should not be served until the button has been pressed
  If there is no coffee left then money should be refunded

  Scenario: Buy last coffee
    Given there are 1 coffees left in the machine
    And I have deposited $1
    When I press the coffee button
    Then I should be served a coffee
```
Reference: [cucumber wiki](https://github.com/cucumber/cucumber/wiki).

* Features are named by completing this sentence: 'The application (should be able to/have a) \_\_\_\_\_'.
In our case, one requirement is that *the application should serve coffee*.
Let's say that this feature fits under the 'service' category.
Your step description for that feature is `service/serve_coffee.feature`.
Your step definition for that feature would be `service/serve_coffee_steps.rb`.

* The description under the feature is where you put the things that need to happen (or shouldn't happen) in order for this feature to accepted as working properly.
One thing that might go here is that a customer has to pay before they get their coffee.
Also, the coffee should dispense only after a button is pressed.
Finally, if the coffee supply has run dry, the money should be refunded.

* Scenarios are named to describe some kind of user action such as 'buy last coffee' or 'browse coffee choices'.


<a name="scenarios"></a>
## 4. Writing Scenarios

> A scenario should describe the acceptance criteria of the feature instead of a huge number of specific actions the user needs to take to accomplish the task.

Let's look at a feature called 'redirect user login' in the file `/features/authentication/redirect_user_login.features`

```
Feature: Redirect user login
  User should have to log in before accessing restricted content

  Scenario: User accesses restricted content
    Given an unauthenticated user
    When the user tries to navigate to the welcome page
    Then they should be redirected to the login page
    When the user enters a valid name in the Name field
    And the user enters the corresponding password in the Password field
    And the user presses the Login button
    Then they should be directed to the welcome page
```
What happens if we decide to implement authentication differently (perhaps oauth through facebook or something)?
What if we want users to log in using their email address rather than their user name?
We would have to change the step description as well as the step definition even though the objective of the feature itself hasn't changed.

Improve maintainability by keeping implementation details out of the feature:
```
Feature: Redirect user login
  User should have to log in before accessing restricted content

  Scenario: User accesses restricted content
    Given an unauthenticated user
    When the user tries to access a restricted asset
    Then they should be directed to a login page
    When the user submits valid credentials
    Then they should be redirected back to the restricted content
```


<a name="links"></a>
## 5. Links / References

[](http://dannorth.net/2011/01/31/whose-domain-is-it-anyway/)
[](http://benmabey.com/2008/05/19/imperative-vs-declarative-scenarios-in-user-stories.html)
[](http://www.elabs.se/blog/15-you-re-cuking-it-wrong)
