
> Storybook suggests a workflow where you can build out a component without needing a server or running the entire frontend application, and test each component state (visually and programmatically) in isolation

Simple Component -> Composite Component -> Data -> Screens

+ #todo: 
	+ how do interfaces link to props?
		+ Where do we put the interface def
	+ automated testing
	+ snapshot testing
	+ figma -> react workflow

### Jargon
+ `actions`
 
### Workflow
1. Define the component, **its props and states**, and write stories for each test
2. **Layer over styling and watch updates take place** 
3. Edit `main.js` and `preview.js` for config. 

```js
//main.js
module.exports = {
// delimit story folder with stories.js
stories: ['../src/components/**/*.stories.js'],
```

```js
// preview.js
// import the stylesheets needed
import '../src/index.css'


export const parameters = { ...
```

### Creating a Story
+ To tell Storybook about the component we are documenting, we create a `default` export in a `component.stories.js` file that contains: 
	+ `component`-- component itself 
	+ `title`-- sidebar name

```js
export default {
	component: TaskList,
	
	title: "TaskList",
	
	decorators: [story => <div style={{ padding: "5rem" }}>{story()}</div>],
}
```
+ We export a function for each of our test states to generate a story. 
	+ The story is a function that returns a rendered element
	+  #pattern As we have multiple permutations of our component, assigning it to a `Template` variable is convenient.
	+ Arguments or [`args`](https://storybook.js.org/docs/react/writing-stories/args) for short, allow us to live-edit our components with the controls addon without restarting Storybook.


#todo : a good ts example


## UI Testing

## Visual Testing


