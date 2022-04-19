> Social game. Takes cases, extracts popular words, and you play in timed rounds with friends to build stories out of them. 


#worklog:
[[2022-03-05]]: Typescript and a basic demo. Ideally, a write up of PCA to test caching. There is no reason to be slow.
	+ Write a new fc
		+ useContext [[React]] hook is somethign I want to practice. Should I be refactoring the entire hook? 
			+ can use useEffect multiple times, and this is where you want to refactor to a custom hook. 
		+ For now, convert from class based. this turns out to be harder than I thought. Use existing ?!?!?!?!
		+ Need to get used to reading [[Typescript]] too. 
			+ Might be the time to starting writing ts, as its pretty much everywhere.
			+ #pulse :O.k. gonna rewrite the wrapper to get my feet wet. Going to pee first. 
				+ There is no reason to be slow. 
				+ There is no reason to be slow. 
				+ There is no reason to be slow-----
				+ You are going to make this work. At some points things just click.
				+ So much left to give.
				+ So, imitating this code will immerse you in the thinking. [[Architecture]] is still something you need practive with, and this is a good way to do so. 
			+ Good time to config ESLint and Prettier. I can see the `--save-dev` workflow in front of me!
			+  ![[Screenshot 2022-03-05 at 4.44.23 PM.png]]
				+ First init with npm the package.json file
					+ Vague deja vu with FSO course, might need to review [[Flask]] soon and possibly integrate previous notes!!!!
					+ install and activate be `./node_modules/.bin/eslint --init`
						+ bin has the execs, which are typically helpers in the cli
						+ inspecting bin, we can see the command the script runs//control flow
				+ #pulse : today is slow but you're getting into the weeds of how these things work. 
					+ For example, setting up prettier from bin using cli
				+ React.VFC
					+ first, need `@types/react` to get the types for intellisense
						+ Would type checking be useful without intellisense?
							+ Yes, as its like with the Google API. Its incredibly predicatble.
						+ React.ReactNode are general cases of components, class or functional, that are passed ot children.
					+ `const [renderData, setRenderData] = useState<RenderData>();`
					+ `const renderEvent = event as CustomEvent<RenderData>;`


[[2022-03-04]] First real [[Streamlit]] commits!
+ [x] Starting by downloading the corpus with bs4
	+ Stripping non-ascii chars really just needed a simple trick
		+ I miss her so much and I need to trust her with this, and trust means not having expectations about how this will go down. 
	+ Now to lemmatise and count again
		+ Works! But forgot about `CountVectorizer` in scikitlearn, which doesn't support lemmatization. 
	+ Okay, so the backend could run the preprocessing, while the frontend casts the thing to the #idea: **d3 graph and handles the rendering logic**
		+ Shaders
+ In the interest of doing the *bare minimum*: deploy to streamlit
	+ Cache stopwords to `.txt` to test loading features
	+ [x] Map a slider to each stopword to test interactivity
	+ [ ] Now, embed a React component running D3 to do the same thing
		+ Got distracted. Going to really focus on this now, feel when I'm hungry, and reflect on [[Modes of self]]
		+ The goal here is to experiment with D3 so as to understand its API, a thinking system unto itself. 
			+ A port of this [thing](https://github.com/andfanilo/streamlit-d3-demo)
				+ [x] Get the basic template up and running
				+ [ ] Create a new selection component to understand the communciation API
				+ [ ] Now bring it into your app 
				+ [[Amelia Wattenburger]] #todo has a great d3 tutorial I should have learned with an intention in mind
			+ The d3 outcome can lend directly to this app. 
			+ #idea: for Capstone, have a horizontal scroll with a "Buy Me a Coffee" on the side, persistently
			  