# Frappe Cheat Sheet

## Form
```
frappe.ui.form.on("Item", {
	setup: function(frm) {
		frm.set_query("name_of_your_field", function() {
			return {
				filters: [
					["Item","item_group", "in", ["option1", "option2"]]
				]
			}
		});
	}
});
```
