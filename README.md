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

### New Doc Button
```
frm.add_custom_button(__('New Doc'), () => {
	frappe.new_doc("<Doctype>");
}, "fa fa-plus", "btn-default","new_requisition");
```
### Query on Script Report Filters
```
{
	"fieldname":"employee",
	"label": __("Employee"),
	"fieldtype": "Link",
	"options": "Employee",
	get_query: () => {
		var company = frappe.query_report.get_filter_value('company');
		return {
			filters: {
				'company': company
			}
		};
	}
}

// or add
get_query: () => {
	let company = frappe.query_report.get_filter_value("company");
	return {
		filters: {
			...company && {company}
		}
	}
}


```

### Page Buttons 
```
// simple button
this.page.add_button(__("Set Chart"), () => {
	this.open_create_chart_dialog();
});

// like select field
const views_menu = this.page.add_custom_button_group(__('Other Reports'));

this.page.add_custom_menu_item(views_menu, __("Leave Balance Summary"), function() {
	frappe.set_route('query-report', 'Employee Leave Balance Summary Report');
});

this.page.add_custom_menu_item(views_menu, __("Leave Application Delay"), function() {
	frappe.set_route('query-report', 'Leave Application Delay Report');
});

this.page.add_action_icon("refresh", () => {
	this.fetch_and_render(true);
}, "Refresh");

this.page.add_menu_item("New Leave Application", () => {
frappe.new_doc('Leave Application');
});

this.page.add_menu_item("Export", () => {
this.export_excel()
})
```
