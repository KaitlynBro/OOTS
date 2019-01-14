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

2.	*How would you print out the value from the Text setting in this header section? [https://cl.ly/567766081e0d](https://cl.ly/567766081e0d)*

    <!-- {% raw %} -->
    ```html
        {{ section.settings.phone_number }}
    ```
    <!-- {% endraw %}) -->

    Alternately, you can store it into a variable:

    <!-- {% raw %} -->
    ```html
        {% assign phone_number = section.settings.phone_number %}
        {% comment %}
            Then call the variable:
        {% endcomment %}
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
        
5. *How could you, in javascript, sum up the total of all the numbers in this array?*

    ```js
        var myArray = [4,2,3,22].reduce((sum, currentNum) => {
            return sum + currentNum
        })
    ```

    **Explanation**: Using reduce on an array allows you to take values in an array and combine them in some way to return one value.
    In the above example, my reduce function is taking the numbers in the array, is adding the numbers up to get the sum of the array. You can also pass an initial value to reduce as a second argument.

6. *What is the benefit of namespacing?*

    Writing in JavaScript makes it simple to create global variables, this can cause issues where one might forget about having previously named a variable or function in their code, and they may create a new variable or function with that same previously used name. Namespacing helps reduce the likelihood of colliding variables by providing a way to create an object literal that holds your functions and variables. You can then access the functions or variables by applying namespacing like so:

    ```js
        let aboutMe = {
            firstName: "Katie",
            lastName: "Brouwers",
            age: 26
        }
    ```

7. *What are the pros and cons of storing jQuery objects in variables?*
    - **Pros**
        - Performance Enhancement: When performing a Dom element search, using `let X = $(‘.element’)` the search is executed only once. Next time it is accessed, it will be faster and without the need for additional functions. Therefore, the more often you have to access an element within jQuery, the more beneficial it is for that element to be stored in a jQuery object. 

    - **Cons**
        - Adding new elements to the code: If you reference all `li`’s on a page and store them into a variable, but then later on, add further `li`’s, the variable will not have them stored. The variable caches the `li`’s but because newer `li`’s are added, they are not cached, and therefore are not stored within the variable. (I used `li`’s as an example, but this explanation is relative for any elements being stored in a jquery object). 

8. *Please download the following .zip file [https://drive.google.com/file/d/1NairIZCb7KHfsxPMhw3ctMfgkxCfcti8/view?usp=sharing](https://drive.google.com/file/d/1NairIZCb7KHfsxPMhw3ctMfgkxCfcti8/view?usp=sharing) and upload it to a Shopify development site [https://www.shopify.ca/partners](https://www.shopify.ca/partners). There are 2 JS errors in this theme that need to be fixed. Write the URL with the corrected theme below and explain what you changed.* 
*Note: both errors are not visible in the console.log immediately, but if you fix the first one, you’ll be able to see the second.*

    **Updated URL: [https://oots-test.myshopify.com](https://oots-test.myshopify.com)**

    **Error 1**: Adding a comma to a key value pair. "imagesLoaded": true did not have a comma at the end. Syntax errors causes the script to stop running until the error is fixed. Only the very last key value pair in an object don’t require a comma at the end.

    ```js
        $('.js-rv-slider').flickity({
          "lazyLoad": 2,
          "imagesLoaded": true, // <- Added comma here
          "draggable": draggable,
          "prevNextButtons": prevNext,
          "wrapAround": wrapAround,
          "cellAlign": cellAlign,
          "pageDots": usePageDots,
          "contain": true,
          "freeScroll": true,
          "arrowShape": arrowSize,
          "initialIndex": initialIndex
        });
    ```

    **Error 2**: Reference error: Changing keywords ‘that’ to ‘this’. The variable ‘that’ was never defined within the scope of the function, causing it unusable. Instead of ‘that’, the keyword ‘this’ was likely meant to be used because they wanted to reference every promo that takes place within the for each loop. 

    ```js
        $('.js-featured-promotions').each(function (index, value){
            var $promos = $(this); // <- Chabged from that
            var animationStyle = $(this).data('promo-animation');
            $promos.waypoint(function() {
                $(this.element).find(".feature-section").addClass("animated " + animationStyle);
            }, { offset: '80%' })
        });
    ```
