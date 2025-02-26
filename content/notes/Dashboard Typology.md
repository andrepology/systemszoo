> Thinking about a spectrum of dashboards, and where ours fits if it fulfills its intended purpose

-   Type 1: **Passive**
    -   These are ad hoc reports, issued periodically. These summarize trends in data over time, often over successive intervals
	    - Ceiling of interactivity is a mousover that prompts a tooltip over charts for more context
    -   These are **useful for generating hypotheses**
        -   For #example: while monitoring annual sales, if we see a spike between Nov-Jan we can attribute it to the holiday season
    -   #example:
    -   Financial Reports, from quarterly to powerBI real time stuff
	    - PowerBI and Tableau dominate this space. 
    -   Bartholomew County Community Dashboard, summarising Education, Health, Financial Stability Indicators for a small county.
-   Type 2: **Active**
    -   We see **dashboards begin to support causal reasoning and interface interaction**
        -   useful for **generate hypothesis → make predictions**
    -   These have a simulation/modeling component
        -   **parameters inputs** → **modeling** -> **distributions over outputs**
    -   #example: Revenue Projections dashboard for an independent school.
        -   IF we add 4 teachers, and in turn can add 25 students to grade 5: what do we expect to see across all enrollment scenarios?
            -   Weak Scenario: We only enroll 3-4 students -> Monte Carlo Sim -> 95%CI says we have reduced profitability by 25-30%
            -   Strong Scenatio: We enroll 20-25 students -> Monte Carlo Sim -> 95%CI says we increase profitability by 12-20%.
-   Type 3: **Affective**
    -   Follows an **"[[the "Affective Loop"]]"**
        -   **Impetus**: Show **Data** // presentation 
            -   #example: Displays a heatmap of Redlining in SF, aggregated to city blocks.
        -   **Interact**: Inform affective action
	        - **parameters inputs** → **modeling** -> **distributions over outputs**
        -   **Affect**: Have **clear feedback** of this contribution, **at the data/presentation level again**
		  - Show a **Mechanism of Affect** or lever
			  -  #example: a donation button to a lending pool for a defi platform that gives loans to excluded minorities
			  - Button to donate _**specifically**_ to a city block of choice
				  - Smart contracts are well-suited to this kind of task
		 -   Answers: *"how does my small part contribute to the whole?"*
		    -   this might necessitate very short timescales between cause and effect.
    - #meta: Despite the Redlining example above we crafted, we don't have good examples for this kind of dashboard, but it happens to be the kind we are aiming to make.
        -   as such, maybe our prototype needs to be just one indicator that credibly achieves affect.
            -   ie, we dont need to cram a bunch of indicators : more is not merrier here.
-   #meta: the conclusion we reached after working out this typology is that we don't have good examples of Affective or Participatory dashboards. But in clarifying the type, we can figure out clear constraints.


## References
-   Abundant housing
    -   ![[Screenshot 2022-03-31 at 8.59.54 PM.png]]
    -   Clearly important indicators, but unclear strategy to be affective.
        -   What are the clear stakes in this?
    -   Can these be things people affect? Why not see this year to year?
        -   How do these connect together or chain or how do we display tractable points of control
-   Batholemew County
    -   ![[Screenshot 2022-03-31 at 10.02.35 PM.png]]ntervention?
-   Introducing Modern Power
    -   Politics as a spectator sport
    -   Roots in small scale, participative organising -> consermist politics
        -   " hands on the levers"
        -   But now
            -   Knowing the rituals/approaches to those with power
                -   #user: **Yufei's point about small enough to understand, large enough to affect change that be traced easily/visually.**