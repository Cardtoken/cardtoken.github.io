# Using the Cardtoken.js

Cardtoken.js is a common component for adding a card capture iframe to your website. Adding Cardtoken.js enables your website to embed the payment capture on the site. Due to PCI you cannot direct link, nor download the JavaScript for hosting.


```javascript
<script type="text/javascript" src="https://api.cardtoken.io/js/"></script>
```

Embed the HTML form like this.

```html
<form id="payment-form">
    <label>Credit or debit card</label><br />
    <div data-cardtoken="cardelement" id="card-element" style="height: 40px; box-sizing: border-box">
        <!-- secure form will be mounted here -->
    </div>

    <button type="submit">Submit Payment Form</button>
</form>
<div id="card-errors"></div>
```

Trigger the form and capture of card

```javascript
// create cardtoken
var cardToken = CardToken('{merchant private key here}');

// select div element
var $element = document.querySelector('#card-element');

// mount iframe to div element
cardToken.mount($element, { cssUrl: '' });

// Handle form submission.
var form = document.getElementById('payment-form');
form.addEventListener('submit', function (event) {
    event.preventDefault();

    // create form
    cardToken.createToken($element,
        function (result) {
            if (result.error) {
                // Inform the user if there was an error.
                var errorElement = document.getElementById('card-errors');
                errorElement.textContent = result.error;
                $($element).addClass('has-error');
            } else {
                // Send the token to your server.
                alert('valid token: ' + result.token);
                // Submit the form
                form.submit();
            }
        }
    );
});
```
