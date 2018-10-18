# Data Set Analysis with IBM Watson Studio

In this part of the workshop we'll be using the IBM Watson Studio tools in order to import, refine and visualize the same accident data that was done in the previous lab with Jupyter Notebooks.  We will compare the techniques used and how similar results can be achieved within IBM Watson Studio.  These techniques might be more interesting to those users who don't have a technical background.

## Log in to IBM Watson Studio

- Launch a new browser window and navigate to [IBM Watson Studio](https://dataplatform.cloud.ibm.com).
- Click Log in and specify your IBM ID and password for use on IBM Cloud (formerly Bluemix).

## Importing Data Assets in IBM Watson Studio

The first thing we are going to do is to import our data sources.  Much of the time this data will come in a tabular format such as a CSV file.

- Navigate to the existing IBM Watson Studio project used in the previous lab and click on the Assets tab.

- On the right hand side of the screen there is a section called Find and Add Data which allows you to load and view files that are imported into the project.

- Click on the Load tab and click Browse. Browse to <download_directory>/cascon-2018-watson-studio-master/data and select the following files:  
dftRoadSafety_Accidents_2016.csv (raw data regarding accidents)  
MakeModel2016.csv (raw data on makes/models of the vehicles involved in accidents)  
DayOfWeekLookup.csv (lookup data relating Day of Week to integer code)  
AgeBandLookup.csv (lookup data relating Age Band to integer code)  

- The files should now show under the Data Assets section

## Joining and Relating Data in IBM Watson Studio

Much like in the first lab, we have two data sets that share a common key, namely Accident Index.  The first thing we want to do is to join the two data sets together using that common key.

- In the Assets section, click on the bubbles next to dftRoadSafety_Accidents_2016.csv and choose Refine.  This opens the Data Refinery view in IBM Watson Studio.  A default view of sample data is shown.
![Default View][data-refinery-1]

- In the top left, choose +Operation.  Notice all the various options that are available for refining data such as Sorting, Removing and Replacing rows.  Under the Organize section, choose Join.
![Operations][data-refinery-2]

- A new panel is displayed which shows the join options.  

- First, choose <strong>Inner join</strong> for the join type.  Now you must choose another Data Set to join with.  In the first lab this was done by joining two data frames.  Here, choose the second Data Set, namely MakeModel2016.csv.  Click Apply.

- Now choose a Join Key.  The only common key in both data sets is Accident Index.  Choose this for both Data Sets and click Next.
![Join Key][data-refinery-3]

- Next we can select which columns we want to preserve in the resulting Data Set.  Just like in the first lab, we'll just keep some key fields that are interesting.  Uncheck all the fields except for these:  
Accident_Index  
Accident_Severity  
Number_of_Casualties  
Day_of_Week  
Speed_limit  
Age_Band_of_Driver  
make  
model  

- Click Apply.  IBM Watson Studio now shows a sample of what the new Data Set will look like.  However, it is not created just yet.  IBM Watson Studio uses Data Flows to actually run the data refinery.  Look at the details for the Data Flow and then when you're ready click on the Play button at the top right.
![Play Data Flow][data-refinery-4]

- On the next page, click the edit icon to change the name of the output file to something a little more manageable like "df_accidents_joined".  Finally, click Save and Run to run the Data Flow.
![Run Data Flow][data-refinery-5]

- You can watch the Data Flow run or come back to it later.  Choose to view the flow.  It will take a minute or two to complete.
![Complete Data Flow][data-refinery-6]

- Going back to the base project view, under Assets you'll see the new Data Set called df_accidents_joined.  Click it to explore the data.  You'll see that only your chosen columns are in this data set and that the make/model information is now joined.

## Refining and Cleaning Data in IBM Watson Studio

You might have noticed that the newly created Data Set still has some inconsistencies.  The make and model of the vehicles is still sometimes null or missing.  The Age Band of the driver is sometimes -1 for undefined.  These are things which can be further cleaned in the Data Set using the tooling provided by IBM Watson Studio.

- Click on the df_accidents_joined Data Set and view the sample contents.

- Click on the Refine link near the top right of the main content pane.  This launches the Data Refinery tool.

- Click the +Operation button.  Under the Cleanse section, choose Convert Column value to Missing.  NULL values in the Data Set can be flagged as Missing which is a type that IBM Watson Studio can more easily recognize.  In the next few steps you'll see what is done with these columns.

- Choose make as the column to convert.  Click Next and then specify NULL values should be converted to Missing values.  Click Apply and you'll see the Data Flow has added a step.
![Data Flow One Step][data-refinery-7]

- Click the +Operation button again and repeat the Convert Column value to Missing steps for the model column.  

- Repeat the Convert Column value to Missing steps again in order to convert any NULL values in the Speed_limit column as well.

- Next, try the Filter operation.  Use this to filter the Data Set and keep any rows where where Age_Band_of_Driver is not equal to -1.  You can combine many different steps together in a Data Flow in order to clean and shape the data as you like.  The resulting Data Flow should look like this.
![Data Flow Four Step][data-refinery-8]

- Click the Play button to launch the data flow and change the output Data Set name to df_accidents_cleaned_1.  Click Save and Run and watch the flow complete.

- View the df_accidents_cleaned_1 Data Set.  You'll see that there are no longer any rows with NULL make or model values - the column values are shown as blanks.  These are now marked as missing or blank rows and can be more easily removed.

- Click the Refine link to do some more cleansing of the data.  Click the +Operations button.  Under the Cleanse section choose Remove empty rows.  Add the column make and click Apply to add it to the Data Flow.  Repeat for the model and Speed_limit columns.  Click the play button for the Data Flow to execute it.  Give the resulting Data Set the name df_accidents_cleaned_2. This will remove any rows in the Data Set which have no data for these columns.  Run the data flow.

Up until now you've seen how to join multiple Data Sets and how to use the Refinery tools to cleanse Data Sets.  Now we're going to use some lookup data to replace integer values with proper text in preparation for visualization.

- Open up the asset df_accidents_cleaned_2.  Click the refine button, click +Operations and choose a Join operation with a <strong>Left Join</strong>.  As the second data set, choose DayOfWeekLookup.csv and click Apply.  Choose Day_Of_Week as the join key for df_accidents_cleaned_2 and code as the join key for DayOfWeekLookup.csv.  Click Next.

- On the next screen, uncheck Day_Of_Week as a result column and ensure that Weekday is chosen.  The lookup Data Set relates the day of week code to a readable week day name.  We're joining the data sets here - we want to include the readable week day name and exclude the actual code.  Click Apply to add the join to the Data Flow.

- Add a second lookup join to the data set called AgeBandLookup.csv with a Left Join.  Choose Age_Band_Of_Driver for the join key on df_accidents_cleaned_2 and code for the AgeBandLookup data set.  Click Next.  Deselect the Age_Band_Of_Driver column and ensure that Age is selected.  Click Apply to add the join to the Data Flow.

- IBM Watson Studio dynamically models the data so that you can see the results of the modifications before actually creating the output data set.  

- Run the data flow to complete the two join operations.  Use the name df_accidents_final.csv for the resulting Data Set.

- Now our data is finally cleaned and refined!  View the data set df_accidents_final.csv to see the results and the newly joined lookup columns.  In the next section we're going to use the Dashboard features of IBM Watson Studio to view the data set.

## Visualizing Data in IBM Watson Studio

- In this section we'll use the embedded Cognos Dashboards in IBM Watson Studio in order to build some visualizations of the data we've imported and refined.  We'll use similar visualizations as in the first lab in order to compare the techniques.

- first, open your IBM Watson Studio project and navigate to the Assets page.  Scroll down to Dashboards and click New Dashboard.

- In the likely event that you don't have an Cognos Embedded Dashboard service already associated with your project, click the link to associate one.  On the subsequent page, choose the Lite plan, Create and then give it a service name and region.  Once created and returned to the Create Dashboard page, click reload to select the service from the list.  Fill in the Dashboard name (example Cascon Dashboard) and optional description and then click Save to save the Dashboard.
![Create Dashboard][data-visualize-1]

- On the next page you can choose a layout for what your Dashboard will look like.  It can have multiple sections per page, multiple tabs, etc.  Choose Freeform since we'll just be creating a basic Dashboard.  Click OK.

- Now you see the default Dasboard building view.  On the top left, click the plus sign next to Selected Sources.  Choose df_accidents_final.csv as the data source.  Then you'll be able to expand that Data Set in the left pane to see the columns which are contained in it.
![Select Source][data-visualize-2]

- Dashboard has a drag and drop interface.  It's quite powerful but can take some getting used to.  You're encouraged to play around to see what kind of visualizations can be built.  We'll perform a few in the lab.  

- First, drag the Weekday column onto the canvas.  Since there is only one column, the data will just be displayed in a table  pane called a List View.  Click the Expand button on the top right of the pane to expand the pane.  Now there will be more options available.

- On the right, change the visualization type from List to Column.  The Weekday column that was dragged first defaults to the x-axis of the graph.  Drag the column Number of Casualties onto the Length area.  The bar graph dynamically forms on the canvas.  You may notice that the Number of Casualties column is large, in the 10's of thousands.  This is because the data is being totalled across the entire Data Set.  This is showing the raw number of casualties per day.  It shows that the least number of total fatalities occurred on Sunday.

- However, we may want to take an average per day instead.  To do this, click on the bubbles next to Number of Casualties, click Summarize and then choose Average.  Now the data has refreshed and the highest casualty days on average are Saturday and Sunday.  This shows how data tells a different story depending on how it's viewed or interpreted.  In this case, there are less overall casualties on a Sunday, but in fact the number of casualties per accident is at it's highest.  
![Graph 1][data-visualize-3]

- Next, let's add a second visualization to the Dashboard.  First, click the right corner of the open chart to collapse it to the canvas.  Move and resize the chart to the left side of the canvas.  Now multi select Number of Casualties and Speed Limit and drag them both together to the canvas, to the right of the existing graph.  Then click on the top right corner of the box to Expand and configure the chart.

- Choose Line for the visualization type.  Then click on the Bubbles to the right of Number of Casualties, choose Summarize and then Average.  The chart changes to show the new line chart.  As you might expect, as the road speed limit increases, so does the average number of casualties.  Collapse this visualization.

- See what happens when you just drag one numeric column over to the canvas.  Drag the Number of Casualties column to the canvas underneath the two graphs.  It displays a numeric value representing the total casualties in the entire Data Set.  This is interesting data to see alongside the other two charts.

- On the left hand side, click the tab for Widgets.  Here you can add titles to the charts as well as add images, videos or other shapes to the Dashboard page.  Using text boxes, give the charts a title like "Average Number of Casualties by Weekday" and "Average Number of Casualties by Speed limit".  You can also change the title of the tab to something like "Casualty Statistics" by double clicking Tab 1 and changing the text.
![Graph 2][data-visualize-4]

- Another feature of the Dashboard is dynamic filtering.  Click on one of the Weekday bars on your Average Number of Casualties by Weekday graph.  Notice that the other chart changes as well as the Number_of_Casualties statistic.  You have dynamically filtered the data to only include the data from that Weekday.  Users of the Dashboard can dynamically filter data as they view it, which is valuable to obtain insights and filter data on the fly.

- Changes to the Dashboard are automatically saved often but you can also save the Dashboard with a specific Save icon on the top row.

- Lastly let's Share this Dashboard.  Click the Share icon on the top row of the Dashboard editor.  On the overlay, choose Share this Dashboard with anyone who has the link.  Copy the link and close the overlay.  Then open a new browser tab and paste the link here.  This link could be embedded in a web application in order to show the users a dynamic visualization.  The same filtering is available here too.
![Shared Dashboard][data-visualize-5]

- The Dashboard features are extensive and include more things than we have time for in this lab.  You are encouraged to explore the Dashboard features using the accident data set or by importing your own.


[comment]: # "------------------------------------------------------------------------------"
[comment]: # "                              Links / Reference                               "
[comment]: # "------------------------------------------------------------------------------"

[data-refinery-1]: images/data-refinery-1.png "Default View"
[data-refinery-2]: images/data-refinery-2.png "Operations"
[data-refinery-3]: images/data-refinery-3.png "Join Key"
[data-refinery-4]: images/data-refinery-4.png "Play Data Flow"
[data-refinery-5]: images/data-refinery-5.png "Run Data Flow"
[data-refinery-6]: images/data-refinery-6.png "Complete Data Flow"

[data-refinery-7]: images/data-refinery-7.png "Data Flow One Step"
[data-refinery-8]: images/data-refinery-8.png "Data Flow Four Step"

[data-visualize-1]: images/data-visualize-1.png "Create Dashboard"
[data-visualize-2]: images/data-visualize-2.png "Select Source"
[data-visualize-3]: images/data-visualize-3.png "Graph 1"
[data-visualize-4]: images/data-visualize-4.png "Graph 2"
[data-visualize-5]: images/data-visualize-5.png "Shared Dashboard"


