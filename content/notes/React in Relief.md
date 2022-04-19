
#idea: write as a diff between the standard flask implementation and the react-flask implementation

+ Objectives
	+ 
+ Setup
	+ Proxying

+ Instead of writing a template for an *entire* page, we decompose the page into a series of subcomponents, each of which is responsible for one thing #separationofconcerns 
	+ Kanban.html becomes
		+ App
			+ TodoForm
			+ Kanban

+ How do we go about the component architecture? We simply follow the Figma! 
	+ The design in Figma already enforces both a component architecture and design system.
		+ For example, Text Styles `Base` becomes `var(text-300)` in code. 
	+ There might be some CSS banter that might be lost in translation, but that itself is just a matter of making finicky updates, and preserving them with maintainability in mind. 
	+ I think taming complexity is vital here. Stick to a design system that enforces consistency. 
		+ Storybook is a tool that lets you focus on one component at a time. Ideally, you don't want to be zooming into a full screen and duplicating a user flow just to see how a button expands when there is a fairly complicated state dependency.
			+ Say we're trying to modify or choose between this version of the Viewer and this one. With Storybook, we can view and interact with their states in isolation, and swap them into the app as we see fit. 
		+ Naming 
			+ [BEM](http://getbem.com/introduction/)
				+ block-element-modifier chaining for concise and clear CSS naming
				+ `block--modifier-value` for buttons `button--state-active`
		+ [Box Model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
			+ Essential for thinking about responsiveness. 
			+ Positioning
			+ Media queries 
		+ Flexbox
		+ [Sizing](https://www.w3schools.com/cssref/css_units.asp)
			+ Pad components in multiples of 4px. 
			+ Relative units might be better for scaling

		+ Specificity && the notion of "cascading"
			+ Specificity is based on the assumption that more narrowly targeted styles (like IDs that are only used once) are likely more important than more generic and reusable styles (like classes and attributes)
			+ Selectors (hover!)
				+ Two part series on Modern CSS selectors, good patterns[Modern CSS](https://moderncss.dev/)
				+ [Smol CSS](https://smolcss.dev/) on responsive layouts, which have reproducible, terse patterns we can use in our app. 
					+ #idea: Present drawings as small scroll snap from SmolCss

+ Higher order functions and decorators, composition