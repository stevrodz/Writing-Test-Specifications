# Writing-Test-Specifications
### Unit Test Specifications

#### 1. **A function called "multiplication" that returns the product of two input numbers**

- **Basic Functionality Tests**
  - Expect `multiplication(3, 4)` to be equal to `12`
  - Expect `multiplication(0, 5)` to be equal to `0`
  - Expect `multiplication(-3, 4)` to be equal to `-12`
  - Expect `multiplication(-3, -4)` to be equal to `12`
  
- **Type Tests**
  - Expect `multiplication(3, "4")` to be an error (invalid type)
  - Expect `multiplication("a", 4)` to be an error (invalid type)
  - Expect `multiplication(3.5, 2)` to be equal to `7.0` (support for floats)
  - Expect `multiplication([], {})` to be an error (non-numeric inputs)
  
- **Edge Cases**
  - Expect `multiplication(0, 0)` to be equal to `0`
  - Expect `multiplication(1e10, 1e10)` to be a large number without overflow or precision loss

#### 2. **A function called "concatOdds" that takes two arrays of integers and returns a single array with the odd numbers in ascending order**

- **Basic Functionality Tests**
  - Expect `concatOdds([3, 2, 1], [9, 1, 1, 4, 15, -1])` to return `[-1, 1, 3, 9, 15]`
  - Expect `concatOdds([1, 3], [5, 7, 9])` to return `[1, 3, 5, 7, 9]`
  - Expect `concatOdds([], [2, 4, 6])` to return `[]` (no odd numbers)
  
- **Handling Duplicates**
  - Expect `concatOdds([1, 1, 1], [1, 1])` to return `[1]` (no duplicates in result)
  
- **Edge Cases**
  - Expect `concatOdds([3, 2, 5], [7, -9, 11])` to return `[-9, 3, 5, 7, 11]` (negative odd numbers)
  - Expect `concatOdds([], [])` to return `[]` (empty input)
  
- **Type Tests**
  - Expect `concatOdds([1, "a", 3], [5, 7])` to be an error (invalid type inside arrays)
  - Expect `concatOdds([1, 2, 3], "not an array")` to be an error (invalid argument)

### Functional Test Specifications

#### 3. **Shopping cart checkout feature allowing guest checkout or logged-in user checkout**

- **Empty Cart Behavior**
  - When a user clicks "Checkout" with an empty cart, they should be shown a message: "Your cart is empty."
  - When a user tries to proceed to payment with an empty cart, the "Proceed" button should be disabled.

- **Guest Checkout**
  - When a user clicks "Checkout as Guest", they should be asked for shipping and payment information before proceeding.
  - When a guest checks out, they should be asked if they want to create an account before final confirmation, but it should be optional.

- **Logged-in User Checkout**
  - When a logged-in user clicks "Checkout", their saved shipping and payment information should be automatically pre-filled, if available.
  - When a logged-in user clicks "Checkout" without saved payment info, they should be prompted to add payment information before proceeding.

- **Account Prompt for Guest Users**
  - When a guest user checks out, after entering their information, they should be prompted with: "Do you want to create an account?" with options to either create one or proceed as a guest.
  
- **Edge Cases**
  - When a user’s session expires during the checkout process, they should be prompted to log back in, and their cart should be saved.
  - When a guest enters invalid shipping information (e.g., missing address fields), they should be shown an error message highlighting the missing or invalid fields.

- **General Payment Flow**
  - When the user clicks "Proceed to Payment", they should see a summary of their order and a breakdown of costs (including taxes, shipping, and discounts).
  - When a user clicks "Confirm Order" without entering valid payment details, they should be shown an error and not be able to proceed.

These test specs cover basic functionality, edge cases, and error handling for both unit and functional tests.
