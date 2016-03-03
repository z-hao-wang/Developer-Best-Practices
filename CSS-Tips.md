##CSS Override Rules

Use a more specific rule to override css rule. ID has higher priority than class.

Examples:
```
<div id="container">
<span class="default">ABC</span>
<span class="default highlight">DEF</span>
</div>
```

```
.default {
  color: black;
}
#container .default {
  color: red; /* this will override rules above */
}
.default.highlight {
  color: white; /* this will override rules above */
  background: blue;
}
span.default.highlight {
  color: white; /* this will override rules above */
  background: yellow;
}
```
CSS Override is very useful for some tasks.

Assume the following HTML represents a dialog
```
<div class="dialog">
<span class="err">Congratulations!</span>
<button class="close">Close</button>
<button class="retry">Try Again</button>
</div>
```
The following css allows us to show the dialog in different state.
```
.dialog .retry{
  display: none; /* by default, the retry button will be hidden */
}
.dialog.show-retry .retry{
  display: block; /* when show-retry class is added into parent DOM, the retry button will be shown */
}
```
In order to show retry button, you can simply add class "show-retry" into the div element.

##Simplify CSS
Since CSS will be downloaded by client, the smaller the file size, the faster your page loads.

### Group "margin", "padding" attributes.
```
.dialog {
  padding-top: 10px;
  padding-bottom: 5px;
  padding-left: 5px;
}
```
Can convert to
```
.dialog {
  padding: 10px 0 5px 5px; // with the order of top right bottom left
}
```

### Group same classes share the same CSS rules
```
.content, .dialog, .tips {
  font-size: 14px;
  color: #eeeeee;
}
```

Or even better, use a generic class for this and add that class into specific DOM elements.
```
<style>
.default-font {
  font-size: 14px;
  color: #eeeeee;
}
</style>
<div class="content default-font"></div>
<div class="dialog default-font"></div>
<div class="tips default-font"></div>
```
