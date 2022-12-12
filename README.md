# Frappe Cheat Sheet

## Form
### Form Methods
```
frappe.ui.form.on("Item", {
    setup: function(frm) {
    	//write your code here
    }
});
```

### Set filter on Link field
```
frm.set_query("name_of_your_field", function() {
    return {
	filters: [
	    ["Item","item_group", "in", ["option1", "option2"]]
	]
    }
});

```
