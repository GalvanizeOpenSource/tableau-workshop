* Google slides
* Connecting to a file
    * Several different file types
        * JSON
        * PDF tables
        * Google sheets
        * Dropbox
        * With the paid version - mySQL, PostgreSQL, salesforce
    * Click Excel file - navigate to FBI file
* Cleaning up the data
    * Load in excel sheet of FBI crime data
    * Use Data Interpreter - Review the results
    * 2nd tab - point out new headers, merged cell handling
    * Merge sexual assault columns
    * Other neat features - pivoting (spreadsheet where each year was a column and the value is a population), splitting text into multiple columns
* Tour of sheet 1 tab
    * Dimensions - categorical
    * Measures - numerical / anything it makes sense to sum or take an average of
    * Marks card - Altering the appearance of the graph
    * Show me - basic graph types to choose from
* Demonstration #1
* First graph - sum of robberies by state
    * Note that you can change the sum to a median or an average
    * Sort results
    * Show mark labels
    * Color - can change it manually OR command drag Robbery to color
        * Change the color scale to a different scale
    * Click the plus sign to see cities makeup
    * Let’s add to hierarchy
    * Right click on population - create - bins
    * Drag population (bin) to between state & city in hiearchy
    * Call the sheet - Robberies
* Save the workbook
    * Create a Tableau Public account if you haven’t yet
    * Log into account
    * Check in about pacing
* Violent crimes by cities map
    * Start with counts of violent crimes
    * Filter on state Colorado
    * Violent crime rate = violent crime/population * 100000
        * A crime rate describes the number of crimes reported to law enforcement agencies per 100,000 total population.
    * Replace violent crime
    * Examine data under Lakeside, then exclude
    * Drag the size up
    * Label unknowns
        * 39.6011 -105.0322
        * 38.9122 -106.9624
    * Call the sheet - Violent Crime Rates
* Arson by burglary
    * Rename arson variable
    * Right click trend lines - show trend lines
    * Hover over line - see p value is very small
    * Drag state onto color to add more detail - drag it off, since too many measures
    * Name the sheet - Arson vs Burglary
* Making a dashboard
    * Change size to automatic
    * Drag in all graphs
    * Use Robberies by state as a filter
    * Add to tooltip - population for map
    * Name sheet - Analyzing 2013 FBI Crime Data
* Breakout #1
    * Average arson by state
    * Sum population on color
* Demonstration #2
* Titanic data
    * Text file import
* Cabin group survivors
    * Move survived & pclass to dimensions
    * Make aliases for survival & class
        * Just for my reference: port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton)
    * Cabin group = LEFT([Cabin], 1)
    * Cabin group & survived as the left side of the graph
    * Make a group from Unknown & T
    * Table calculation -> Percent of total -> specific dimensions -> check Survived
    * Survived onto color
    * Percent onto label
    * Number onto label
    * Drag to see graph better
* With family
    * With family calc
        * IF [Parch] = 0 THEN 'No Family'
        * ELSEIF [SibSp] = 0 THEN 'No Family'
        * ELSE 'With Family'
        * END
    * Bubble graph
    * Change color palette just for fun
    * Add number for label
* Ages and Classes - Box & Whisker
    * Age by sex & class
        * Sex on top, class on bottom — age as the DV
    * Colored by class
    * Change age default to no decimals
    * Average Fare in _
        * Drag fare to tooltip
            * Look at the underlying data - is just giving us individual fares for each datapoint
        * {FIXED  [Pclass]: AVG([Fare])}
    * Change fare format to currency
    * Make dynamic tooltip
* Titanic dashboard
    * Resize traveling with family graph to fit automatically
    * Add filter for traveling with family dropdown - apply to all
    * Add filter for age - apply to all
    * Add little image of titanic
* Breakout 2
    * {FIXED [Ticket]: COUNT(Name)}
    * Age vs number of people on ticket
    * Trend line
    * Add to dashboard
    * Add filter
* Demonstration #3
* Billionaire dataset
    * Add currency as default
* Gender statistics
    * Parameter - Gender Graphs
        * Average Age
        * Count of Billionaires
    * Dynamic Measure
        * IF [Gender Graphs] = 'Average Age' THEN AVG([Age])
        * ELSEIF  [Gender Graphs] = 'Count of Billionaires' THEN SUM([Number of Records])
        * END
* Top Billionaires
    * First show top 10 fixed billionaires, then show adding parameter functionality
    * Top Billionaires parameter - range 1-50
    * Filter name by worth in billions and top billionaires parameter
    * Circle graph
* Tabby
    * Need to install
    * Activate from the command line
    * mdfind kind:folder "tabpy_server"
        * sh /Users/applemacbook/anaconda/envs/Tableau-Python-Server/lib/python2.7/site-packages/tabpy_server/startup.sh
        * Recommend making an alias in your bash profile if interested
    * Help -> Settings -> Manage External Service Connection
        * Port 9004 by default
        * Local host
    * SCRIPT_BOOL
    * SCRIPT_INT
    * SCRIPT_REAL (like float)
    * SCRIPT_STR
    * Use _arg# to reference Tableau measures or dimensions
* Countries by worth
    * Country Name
        * SCRIPT_STR("
        * return [x.title() for x in _arg1]
        * ",
        * MIN([Country of Citizenship]))
    * Average Worth
        * SCRIPT_INT("
        * return [x*1000000000 for x in _arg1]
        * ",
        * AVG([Num Worth in Billions]))
* Billionaire Analysis - Story
    * Make a story - guided dashboard/findings
    * Resize graphs at source
    * Billionaire couples tend to be older than single billionaires.
    * Most of the billionaires, however, were men.
    * In fact, in the top 10 billionaires, none of them were women.
    * Interestingly, billionaires in Mexico, Nigeria, and Saudi Arabia had the highest average wealth.
    * Here's my next steps.
        * For my next project, I'm going to focus on successful women and what made them successful!
* Breakout 3 - choose your own adventure!
* Feedback survey!
