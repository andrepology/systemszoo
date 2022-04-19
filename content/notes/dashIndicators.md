> Process notes for querying, processing and presenting indicators

1. [[Indicator Decompostion]] : overall approach to locating indicators
2. [[Indicator Catalogue]]: list of examples of dashboards 
3. [[Indicator Modeling]]: Processing one or more sources of data to credible indicators

### References 
1. [DataSF](https://datasf.org/)
	+ "Showcase Stories"
	+ #meta: lots of dashboards have this utopian vision of **"making what we measure"**
		+ This is SFData's "DataSF's mission is to empower use of data. We seek to transform the way the City works through the use of data. We believe **use of data and evidence can improve our operations and the services we provide**. This ultimately leads to increased quality of life and work for San Francisco residents, employers, employees and visitors. [Learn more about our work.](https://datasf.org/about)"
		+ An encompassing dashboard might not do the job
		+ One that does one precise thing might be better
	+ [Streamlining Property Tax Appraisals](https://datasf.org/showcase/datascience/streamlining-property-tax-appraisals/)
		+ Predictive model of property value of homes
	+ [Energy Performance Report](https://datasf.org/showcase/powerbi/energy-performance-report/)
		+ **Background**: each year building owners are required to report energy usage data to the Department for benchmarking purposes. **SF Environment** uses this data to engage and collaborate with building owners to reduce energy use.
			+ SF Environment fulfilled this by publishing and maintaining a dataset on the open data portal
			+ SF Environment wanted not just transparency, but engagement. The public report, though well designed, was 30 pages long and static. 
		+ **Outcome**: [PowerBI dashboard](https://sfenvironment.org/energy/san-francisco-existing-buildings-performance-report). 
			+ San Francisco was the first city in the United States to transition to an automated, interactive annual report of Building Energy Use.
			+  SF Environment internally uses the same report to shape targeted outreach and ongoing business community engagement
				+ #crit: Its so static, and scrolling and pagination are TERRIBLE. 
		+ Data:
			+ annual, according to building guidelines
	+ [City Performance Scorecards](https://datasf.org/showcase/powerbi/city-performance-scorecards/)
		+ **Background**: residents of San Francisco need to know how well City services are meeting their needs
	+ [SF Planning](https://sfplanninggis.org/PIM/)
		+ Background
		+ #crit: okay, its indicating based on city or regulation codes (Health Code Article 22A)
			+ **Flooding**: FEMA FIRM Floof Hazards
			+ **Maher Ordinance**: Health Code Article 22A
			+ **Cortese** List: Government Code Section 65962.5
			+ **Air Pollutant Exposure Zone**: Health Code Article 38
		+ #crit: has some interesting [[Indicator Decompostion]] 
			+ Zoning
				+ Business
				+ Coastal
				+ Port
				+ Cultural
				+ Planning Areas
			+ Environmental 
			+ Historical 
	+ [Greening the City](https://datasf.org/showcase/datascience/greening-the-city-with-better-lighting/)
		+ Result: **Building permits** can help identify new clients for installing new efficient bulbs under city's green policy
			+ #modeling: points to importance of modeling that correlates different sources, new hypotheses
		+ Based on the findings, DataScienceSF created a long list of potential leads. We combined data on property use, permitting activity, and energy consumption to help prioritize targets. The new list relied heavily on data already published through the open data portal. We then matched it with properties in SFE’s existing database to easily identify properties that already existed in the database.
		+ ![[Screenshot 2022-04-03 at 5.31.20 PM.png]]
			+ Leads list increases ... but for a specific clientele. Ie works when consulting. 
				+ Ie Combine this data with building energy consumption data from PG&E to further refine and prioritize SFE’s outreach strategy
					+ SFE has a refined strategy, but the person affecting is not the citizen.

2. [Open Data Network](http://www.opendatanetwork.com/)
3. [Bartholomew County Dashboard](https://static1.squarespace.com/static/590a013d17bffc01e661e5c1/t/5ab148136d2a73ff3ac0e8f5/1521567765686/Bartholomew+County+Community+Dashboard+PDF.pdf)
	+ Education
		+ Passing Rate of English and Math at 3rd Grade
		+ Passing Rate of English and Math at 8th Grade
		+ High School Dropout Rate
		+ High School Graduate Rate
		+ Postsecondary Attainment
			+ Previous Year
			+ Target
	+ Financial Stability
		+ Poverty
			+ % BPL
		+ Renter Occupied Units with High Housing Costs
		+ Free and Reduced Lunch
	+ Health
		+ Teen Births / 1,000
		+ Suicide Rate / 100,000
		+ Population under 65 without Health Insurance
		+ Adult Obesity Rate
		+ Drug Overdose Deaths

4. [SFGov Scorecards](https://sfgov.org/scorecards/)
	+ Areas
		+ **Livability**
			+ **Public Works**
				+ **Street and Sidewalk Cleaning Response**
					+ Public Works receives most cleaning requests through San Francisco 311, the City's customer service center. Public Works and has a goal of responding to 95 percent of street and sidewalk cleaning requests within 48 hours. Street and sidewalk cleanliness affects the aesthetics, health, and safety of San Francisco. Excessive litter and or debris can also block storm drains and cause flooding.
					+ Public Works dispatches litter patrols for small items and steamer services 24 hours a day, 7 days a week. Recology - the City's waste management vendor - is primarily responsible for removing large items since July 2013. Public Works dispatches additional packer trucks to remove large items in some cases.
					+ **HOW** **PERFORMANCE IS MEASURED**
						+ Street and sidewalk cleaning requests are generated internally and through calls received by the City’s 311 customer service center. Requests received by 311 are sent to the Public Works’ dispatch system. Public Works’ Radio Room triages the request to the appropriate crew, and crews respond to the request.
						+ The monthly response percentage is the number of requests responded to within 48 hours divided by the total number of requests received in that month.
						+ The number displayed on the [scorecard page](https://sfgov.org/scorecards/index.aspx?page=5370) represents a fiscal year average of the response chart above.
					+ **ADDITIONAL INFORMATION**
						-   Submit a street cleaning request through [San Francisco 311](http://www.sf311.org/index.aspx?page=109).
						-   Read about [PublicWorksStat (formerly known as DPWStat).](http://openbook.sfgov.org/webreports/details3.aspx?id=1884)
					+ **DATA**
						Access Scorecard data through [DataSF](https://data.sfgov.org/City-Management-and-Ethics/Scorecard-Measures/kc49-udxn), San Francisco's open data portal.
						
						Public Works dispatches litter patrols for small items and steamer services 24 hours a day, 7 days a week. Recology - the City's waste mana
						
						
						
						gement vendor - is primarily responsible for removing large items since July 2013. Public Works dispatches additional packer trucks to remove large items in some cases.
			+ Public Library
			+ Recration and Parks
			+ 2019 City Survey
				+ Overall Library System: A- 
		+ Public Health
		+ Safety Net
		+ Public Safety
		+ Transportation
		+ Environment
		+ Economy
		+ Finance
	+ Metrics
		+ Uses Meeting Target / Needs Improvement / Not Meeting Target / No Target
	+ #crit: **extremely slow**, but sparklines are nice as is consistent colors. 
		+ Another hosted PowerBI app. 