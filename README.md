*work in progress*

#ko.handlebars.js

ko.handlebars.js is a template engine for [knockoutjs](http://knockoutjs.com). It enables you to use [handlebars.js](https://github.com/wycats/handlebars.js/) template library in place of Knockout's native templating.

Tested with Knockout v2.2.1 and handlebars.js v1.0.0-rc.3.

##Usage


Set default template engine to be used by Knockout. Make sure you do that **before** of your custom Knockout related code (like creating observables, applying bindings etc.).

	// Set ko.handlebars.js as a template engine for knockout
	ko.setTemplateEngine(new ko.handlebarsTemplateEngine());

##Example

	<html>
	<head>
		<title>ko.handlebars.js example</title>
		<script type="text/javascript" src="lib/handlebars.js"></script>
		<script type="text/javascript" src="lib/knockout-2.2.1.js"></script>
		<script type="text/javascript" src="ko.handlebars.js"></script>
		<script>
			ko.setTemplateEngine(new ko.handlebarsTemplateEngine());
		</script>
	</head>
	<body>
		<!-- place for rendered template -->
		<div data-bind='template: "personTemplate"'></div>

		<!-- handlebars template -->
		<script id="person-template" type="text/x-handlebars-template">
			{{ name }} is {{ age }}
			<button data-bind='click: makeOlder'>Make Older</button>
		</script>
	
		<!-- knockout model and bindings -->
		<script type="text/javascript">
			var viewModel = {
				name: 'Martin',
				age: ko.observable(78),
				makeOlder: function () {
					this.age(this.age() + 1);
				}
			};
			ko.applyBindings(viewModel);
		</script>
	</body>
	</html>


##Copyright

Copyright (c) 2013 Reid Lynch. License: MIT (http://www.opensource.org/licenses/mit-license.php)
