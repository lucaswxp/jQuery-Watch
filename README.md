jQuery Watch
============

Keep your dynamic elements synchronized

What it does?
============

It watches for new elements that may be added dynamically and reapply its behaviors.

For example, let's say you are using the jQuery UI DatePicker plugin:

```javascript
jQuery(function(){
    $('input.calendar').datepicker();
});```

This will works great for all inputs with the class "calendar" on it. But what if you need to dynamically add some more .calendar inputs in the page? (direct dom change, ajax, etc)

```javascript
jQuery(function(){
    $('input.calendar').datepicker();


    $('body').append('<input type="text" class="calendar" />');
});```

The appended input will not be initialized, since the jQuery DatePicker call was made BEFORE you added that content.

One solution would be wrap the datepicker call in a function, then execute it whenever you need it, but this can get annoying and overwhelmingly repetitive. Let's get a little DRY?

How to use?
============

A code snippet worth more than a thousand words:

```javascript
jQuery(function(){
    $('input.calendar').watch(function(){
        this.datepicker();
    });


    $('body').append('<input type="text" class="calendar" />');
});```

That's it! Now all new input.calendar added to the DOM will be properly initialized.
