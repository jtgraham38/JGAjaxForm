# JG Ajax Form
jg_ajax_form.js makes it easy to submit a form via an ajax request, without refreshing the page.  To submit a form using an ajax GET request, simply set the *jg_ajax_method* attribute of the form to *GET* (case-sensitive, for now).

```html
<form action="/" jg_ajax_method="GET">
    <label for="name_input">Name</label>
    <input type="text" id="name_input" name="name">

    <label for="email_input">Email</label>
    <input type="email" id="email_input" name="email">

    <label for="message_input">Message</label>
    <input type="text" id="message_input" name="message">

    <input type="submit" value="submit">
</form>
```

To submit the form using an ajax POST request, simply switch the *jg_ajax_method* attribute to *POST* (again, case-sensitive, for now).

```html
<form action="/" jg_ajax_method="POST">
    
    <!-- form fields here -->

    <input type="submit" value="submit">
</form>
```

You may want to do something with the result returned by the request.  To do that, simply set the *jg_ajax_response_handler* attribute on the form equal to a javascript function handle.  This function accepts two parameters, *event* (the form onsubmit event), and *response* (the data returned by the async request), so be sure your handler accepts those two arguments in that order.

```html
<form action="/" method="jg_ajax_get" jg_ajax_response_handler="handler">
    
    <!-- form fields here -->

    <input type="submit" value="submit">
</form>

<script>
function handler(event, response){
    console.log(response)

    //perform some task here
}
</script>
```

The handler is defined identically on a form that uses the *jg_ajax_post* method.


**NOTE: if you use this script in tandem with either JG Honeypot Form or JG Stripe Form, I highly recommend using this script to initialize all event listeners: https://github.com/jtgraham38/JGJS_Synchronizer**