-   #principle : A part of Andre’s design process is to actively maintain documentation, and it helps with maintainability and communication with Finn. This lived in Obsidian but we brought it over to Notion.
-   #meta: A helpful part of the problem decomposition is finding out precise semantics/jargon to keep us aligned (for example, **[[the "Affective Loop"]]**).
    -   I wrote about the importance of this in my application to the Roote Fellowship, referencing the engineering culture at Wiki Research.

> Prompt: A community dashboard for SF that helps citizens begin to interact with and **have agency** over their city.
-   **Metric**: **5% of San Francisco residents looks at this every day**
    -   We’re going to treat this as the most important overarching metric, because it provides us with a lot of constraints on the problem space
    -   **What dashboards, or signals/indicators have we seen that do this?**
        -   Under what **incentives/rationales/behavioral models** do people respond to signals in such a way?
            -   when they have **stakes**, they look at things often
                -   Stocks -> net worth, weather -> carry an umbrella
                -   To look at something every day, you need to feel like you have a stake in it
                    -   **affect it, and/or it effects you** on a regular basis
                    - ![[Screenshot 2022-04-03 at 5.27.07 PM.png]]
                    - This is not a good example: electricity is important, but why check?
            -   When there aren’t **stakes,** our concern for indicators of important issues reduces to infrequent glances.
    -   #todo: there is also a slight concern about the selection bias: how do we ensure representativeness?
        -   Seems like a civic dashboard supported by The Graph might preferentially select for web3 guys, so we need to cast the net wider in terms of the v1 user base ...
            -   A related question is whether our goal is to produce a widely relevant solution and try to capture a small proportion of market share, or whether to **focus on a much smaller issue and trying to create very high uptake levels for the associated demographic**


### Key Areas
1. [[the "Affective Loop"]]: the core user flow that we want this dashboard to support.
2. [[dashConstraints]]: the set of constraints that come from the affective loop
3. [[dashConcerns]] : a collection of inline tags to motivate research
4. [[dashIndicators]]: locating, querying, processing and presenting indicators
5. [[dashStack]]: notes on stack and technologies
6. [[dashComponents]]
7. [[presentation]]: external tl;drs 


### Worklog
+ [[2022-04-03]] : Catloging and Init Figma
	+ [x]  Share Figma drafts for rough aesethetic pointers
		+ [x] Accessibility needs to be considerered better
			+ [x] Context setting/ narrative description
				+ ![[Screenshot 2022-04-03 at 5.03.12 PM.png]]
	+ [x] Begin cataloguing data sources
		+ [x] SFData
			+ Huge data modeling component we might be underestimating, which is why the "do one thing but really well and make sure its actually adding value" is so important 
			+ but yeah theres an underestimation of the modeling process overall (preprocessing, EDA, modeling + viz) that we need to start ASAP and in a lightweight way, so jupyter/streamlit
			+ Added to concerns