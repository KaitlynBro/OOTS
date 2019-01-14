## OOTS FED Questions
1. *Write some CSS in the snippet below that would center the child div vertically*
    ```html
      <div class=”parent”>
        <div class=”child”>
        </div>
      </div>
    ```

    Simplest way:

    ```css
      .child {
        margin: 0 auto;
      }
    ```

    • 0 auto is short-hand for 0 (top), auto (right), 0 (bottom), auto (left). 0 causes 0 margin on the top and bottom of the element, while the left and right sides take auto margin which tells the browser to automatically determine the margins of the left and ride sides itself. The browser does this by setting the margins equally, and in turn, causes the element to be centered

    Alternately, using Flexbox:

    ```css
    .parent {
      display: flex;
      justify-content: center;
    }
    ```

    • **Display**: flex defines a flex container and enables its direct children to be controlled by flex properties. Justify-content:center will center the parent elements children to the page.

    Alternately, using relative and absolute positioning with transform:

    ```css
        .parent {
            position:relative;
        }
        .child {
            position:absolute; left:50%;
            transform:translate(-50%);
        }
    ```

    **Relative positioning**: where the element is positioned relative to its normal position (nothing will automatically happen to this element once its relatively positioned, and only until you apply top/bottom/right/left to it, will it then move).
    **Absolute positioning**: the element is positioned absolutely to its positioned parent, allowing you to change its position using top/bottom/right/left
    **Translate**: applies a transformation to an element, and transform: translate (X%) moves the element up, down, right, or left

2.	*How would you print out the value from the Text setting in this header section? https://cl.ly/567766081e0d*

    <!-- {% raw %} -->
    ```html
      {{ section.settings.phone_number }}
    ```
    <!-- {% endraw %}) -->

    Alternately, you can store it into a variable:

    <!-- {% raw %} -->
    ```html
      {% assign phone_number = section.settings.phone_number %}
    ```
    <!-- {% endraw %}) -->

    Then call the variable:
    <!-- {% raw %} -->
    ```html    
      {{ phone_number }}
    ```
    <!-- {% endraw %}) -->

3.	*If I have an array called myArray, and I want to get the third item in this array and set it to a new variable called thirdItem, how would I do that?*

    ```js
        const myArray = [1,2,3,4,5,6]
        const thirdItem = myArray[2] // 4
    ```
    **Explanation**: Since JavaScript arrays indexes start at 0, in order to access the third item in the array, you need to pass 2 using square bracket notation to myArray.

4.	*Write a function that takes a string and turns it into an array.*

    ```js
        function convertStringToArray(string) {
            return Array.from(string)
        }
        convertStringToArray("hello!") // ["h", "e", "l", "l", "o", "!"]
    ```
    **Explanation**: Passing a string from Array.from will return an array of each character in the string

1. *How could you, in javascript, sum up the total of all the numbers in this array?*

    ```js
        var myArray = [4,2,3,22].reduce((sum, currentNum) => {
            return sum + currentNum
        })
    ```

    **Explanation**: Using reduce on an array allows you to take values in an array and combine them in some way to return one value.
    In the above example, my reduce function is taking the numbers in the array, is adding the numbers up to get the sum of the array. You can also pass an initial value to reduce as a second argument.

2. *What is the benefit of namespacing?*

    Writing in JavaScript makes it simple to create global variables, this can cause issues where one might forget about having previously named a variable or function in their code, and they may create a new variable or function with that same previously used name. Namespacing helps reduce the likelihood of colliding variables by providing a way to create an object literal that holds your functions and variables. You can then access the functions or variables by applying namespacing like so:

    ```js
        let aboutMe = {
            firstName: "Katie",
            lastName: "Brouwers",
            age: 26
        }
    ```

3. *What are the pros and cons of storing jQuery objects in variables?*
    - **Pros**
        1. Convenient if you need to call many jQuery functions on a single selector
        2. More performant because of caching
    - **Cons**
        1.

4. *Please download the following .zip file (https://drive.google.com/file/d/1NairIZCb7KHfsxPMhw3ctMfgkxCfcti8/view?usp=sharing) and upload it to a Shopify development site (https://www.shopify.ca/partners). There are 2 JS errors in this theme that need to be fixed. Write the URL with the corrected theme below and explain what you changed.*
*Note: both errors are not visible in the console.log immediately, but if you fix the first one, you’ll be able to see the second.*
