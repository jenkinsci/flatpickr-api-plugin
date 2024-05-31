# flatpickr API plugin

This plugin exposes [flatpickr.js](https://flatpickr.js.org/) for use in Jenkins plugins.
The included styling supports dark theme out of the box.

## Usage

To load the flatpickr.js library add the following to your jelly:
```xml
<st:adjunct includes="io.jenkins.plugins.flatpickr"/>
```

## Sample

In your jelly create a div that contains an input field and a button. Set the attribute `data-input` on the input field and 
the attribute `data-toggle` on the button.
```xml
<div class="flatpickr-input" style="display: flex; gap: 5px" data-now="${it.minDate}">
  <f:textbox name="date" value="${it.defaultDate}"
             checkDependsOn="" data-input=""/>
  <button class="jenkins-button" type="button" data-toggle="" tooltip="Open datetime picker">
    <l:icon src="symbol-calendar-outline plugin-ionicons-api"/>
  </button>
</div>
<st:adjunct includes="io.jenkins.plugins.flatpickr"/>
```

In javascript attach flatpickr to the div, e.g with
```js
Behaviour.specify(".flatpickr-input", "flatpickr-input", 0, function(fp) {
   flatpickr(fp, {
    allowInput: true,
    enableTime: true,
    wrap: true,
    clickOpens: false,
    dateFormat: "Y-m-d H:i",
    time_24hr: true,
    static: true,
    minDate: fp.dataset.now,
  });
});
```
Set the option `wrap: true` with above sample.


Clicking on the button will now open/close the date-time-picker


## LICENSE

Licensed under MIT, see [LICENSE](LICENSE.md)

