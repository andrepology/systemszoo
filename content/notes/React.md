> React is a component-driven framework for building UIs

+ Created an affective mentality of going from components to screens rather than vice versa
	+ [[Storybook]] is a system to focus on one component at a time.
+ Components are atomised UI pieces that render existing properties or newly created state
	+ #separationofconcerns writ large
	+ Properties are [[Passing Down State | passed down state]], data fetched from a server, which re-render on the [[React State | state]] change
		+ most of the work is in `[state, updateState] = useState`
	+ [[Typescript]], with a good parser/linter, makes it 


## Key Concepts: Thinking in React

### Styling with [[CSS]]

### Loading Data From Server
+ #pattern: loading data from server in react is just a matter of `fetch then catch` within the `useEffect` hook. 
	+ Where/how is this more complicated?

### Where State Lives
+ Lowest common ancestor
+ 

## Questions
+ #todo Workflow for converting Figma to components

