# js-live-validator

## Usage

### Data attributes
This plugin requires you to add data attributes to your form and some data attributes require specific values,
These are the data attributes:
- "data-live-validator-form" - this attribute is added to the form element, it allows you to have multiple forms on one page with the plugin active. The value can be anything you want but should be unique.
- "data-live-validator" - This attribute must be added to the wrapper of a field. The value must be the same as the 'name' attribute of the child field.
- "data-live-validator-rules" - This attribute must also be added to the wrapper of a field, the value of this wrapper contains all the specific rules that apply to the child-field. Below an example and a list of all the rules.


Example form HTML:
```html
<form method="post" action="..." data-live-validator-form="user-add">
    <div data-live-validator="firstname" data-live-validator-rules="min_char:2|alpha">
        <input type="text" name="firstname" class="form-control">
    </div>
    <div data-live-validator="lastname" data-live-validator-rules="min_char:2|alpha">
        <input type="text" name="lastname" class="form-control">
    </div>
    <div data-live-validator="email" data-live-validator-rules="email">
        <input type="text" name="email" class="form-control">
    </div>
</form>
```

Initialization in JS:
```javascript
  let options = {
    event: ["keyup", "change", "focusout"],
    rules: "required",
    msg: _private.msg,
    msgWrapperClass: {
        danger: "lv-val-danger",
        success: "lv-val-success" 
    },
    msgClass: "lv-val-msg",
  }
  let validator = new LiveValidator(options);
  validator.initialize();
```

