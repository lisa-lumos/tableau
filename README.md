# Tableau Summary
This file is a summary of Tableau features (`what it can do`). I have used Tableau for around a year (since Oct 2021), now I am summing it up. This file is mainly intended for Tableau Desktop. 

This file will be updated regularly until complete.

## 🏷 Connect to data
Tableau supports connecting to `hundreds of data sources`, including a number of different `flat file types` as well as a wide range of `server-based data sources`. E.g., to your computer in a spreadsheet or a text file, or in a database on a server. 

Two data connection options: use `live connection (default)`, or use an `extract`. 

A `live connection` is a direct connection to your data, best used when you want to `leverage a high performance database’s capabilities`, or get `real time changes` in viz (when you refresh it...). Sometimes, connecting live can result in a slow experience, depending on the database. You can `manually refresh` the live connection; Tableau will also `refresh the data automatically each time you open` the workbook.

An `extract` is a compressed snapshot of data stored locally. Useful when you `connect to a slow database` or when you want to `take query load off critical systems`. You can also choose to `import only some of the data` to the extract. 

### Metadata
Tableau assigns `metadata` to the data that you bring into it; you can edit the metadata to decide `how the fields to look and function` in a view. It includes the `names of fields`, `data types`, `aggregation information`, and `default display properties`, etc. 

### The Data Source page
In the `data grid` in the `Data Source page`, Tableau shows `some of the metadata` for the dataset, such as `data role` and `field name`. Tableau distinguishes numbers from strings and dates from dates with timestamps etc. Tableau represents these data role assignments with an icon near the field label. For example, Tableau recognizes City as a geographic entity, and therefore assigns it a `Geographic Role` (a common data role), connecting that field to Tableau's generated latitude and longitude coordinates. Note: `This does not change the data type`, which will remain as a string in this case. You can `make edits to the metadata` right `from the data grid`, such as `changing data role` for a field, `rename` a field. 

The `data grid view` and be switched to `metadata grid view`, which shows each field in a row, where you can `rename fields`, or `hide multiple fields at once`. Changes to the metadata in Tableau `don't impact the source data`.

### The Tableau workspace
In `the Tableau workspace`, the `Data pane` on the left lists the fields in the data source, organized into `dimensions`(blue icons) and `measures`(green icons). You can `drag` the fields from the `Data pane` to the `cards` and `shelves` to begin creating viz. You can also `rename fields` from the data pane. 

The `Pages shelf` lets you break a view into a series of pages to navigate your data like a flip-book animation. It can help analyze data changes and discover hidden insights. 

The `Filters shelf` lets you specify which data to include and exclude, to narrow your viz to the most useful information. 

The `Columns and Rows shelves` let you drop fields to create structure of viz.

The `Marks card` let you drop fields to add context and detail to the viz, such as setting mark type, color, size, shape, text, and detail. 

### Data Interpreter
Data Interpreter can automatically detect and bypass the titles, notes, footers, and empty cells in a data source. Use Data Interpreter to prepare data in files, including those in Microsoft Excel, CSV, PDF, and Google Sheets format. It does not change the underlying data source. Data Interpreter can detect additional tables and sub-tables so that you can work with a subset of the data independently. 

For detail on the field names and values Data Interpreter included or excluded, click Review the results. Then a copy of your data source opens in Microsoft Excel, showing the Key for the Data Interpreter tab.

When Data Interpreter is not available:
- The data source is already in a format that Tableau can interpret: If Tableau doesn't need extra help from Data Interpreter to handle unique formatting or extraneous information, the Data Interpreter option is not available.
- The Data Interpreter option is not available when the data set exceeds Data Interpeter’s maximum number of columns and rows.
- Data Interpreter is only available for supported file types, such as Microsoft Excel files (.xls or .xlsx format), text files(.csv format), PDF files, and Google Sheets.

Data Interpreter is an excellent shortcut, and works in many situations, but if the results aren't as expected, you may need to directly address the data file you bring into Tableau to ensure it's in the correct format.

After using Data Interpreter, you might still need to perform some additional restructuring steps like pivoting your data or splitting fields to get the data in the shape you want. 

### Pivot data in the data grid
Tableau works best when analyzing data in a “tall” or “narrow” table structure. If the data you’re working with has a “wide” structure (the information is captured with many columns, and the columns contain similar information), you can use a pivot to change the columns into rows. Changing the structure in Tableau does not change your underlying source data.

### Split data fields
Use the Split (automatically choose delimiter) or Custom split (manually choose delimiter, and which substrings to include) options in Tableau to separate the values based on a delimiter or a repeated pattern of values present in each row of the field. Split and Custom Split create calculated fields. Split and custom split options are available only for fields that are a String data type.

In Tableau Cloud and Tableau Server, Split and Custom Split are not available as menu options, but it’s possible to achieve the same result by creating a calculated field with a formula that uses the SPLIT function, similar to the one shown above. 

New fields generated from a split or custom split cannot be used in a pivot.

### Replace a data source for a view
If the original and new data sources have identical field names, after you replace the data source, the views in the workbook will work just as they did when they used the original data source, but will display the values in the new data source.

If there are differences between the original and new data sources, you can resolve issues after replacing a data source. However, it’s usually quicker to prepare the data sources first, replace the data source, and then fix remaining issues, if any. Ref: `https://tabsoft.co/repcovid19ds`. 

The goal of preparing the data sources is to make them as identical as you can, to make data source replacement smoother. Ideally, the new data source would have the same fields, with the same field names, data types, and so on, as the original data source. 

To resolve different field names, rename them in the data pane. Similar to data types. 

After you replace a data source, if there is an exclamation mark to the right of a field in the Data pane, as in the following animation, that field has errors to resolve. You could Replace References to solve it. 






## 🏷 Customize data source
Could do cleanup and organization as you work with the underlying source data, include customizations like `connection information`, `organizational or metadata changes`, `attributes`, or `aliases`. Tableau Desktop allows us to `save these data source customizations for reuse`. It preserves the customizations you make, but it does not change the underlying source data.

Common `changes to data attributes` fall into several categories, all of which are `saved in a Tableau data source (.tds) file`:
- Folder structure
- Measure and dimension conversions
- Field data types (e.g., strings, integers, dates)
- Field properties (e.g., how a field is displayed or aggregated)
- Attributes (e.g., field names)

### Organize fields into folders
Useful when you have `a large number of fields in the Data pane`. For example, you may want to organize all the customer fields, such as Customer Name and Customer ID, into a new folder called "Customer Info."

### Convert fields from measures to dimensions
Tableau automatically predicts and assigns fields to dimensions or measures, but you can `change it from one to the other`. 

### Edit attributes
Tableau allows you to `rename` any of the database fields. 

### Create aliases to rename members in the view
Tableau allows you to create `aliases` for values (labels) inside a field. 

### Edit a field’s default properties (Tableau Desktop only)
You can edit `a field’s default properties`, such as `color`, `number format`, or `aggregation`. This way, every time you add the field to the view, it will maintain its assigned properties.

### Tableau data source (.tds) file
Tableau Desktop can save your customizations (metadata changes) of your data source to a local file in the `Tableau data source (.tds) format`. You can `reuse` the .tds file in different workbooks and `share` the .tds file with other users.

Included in a .tds file:
- Measures converted to dimensions, and Dimensions converted to measures
- Edited field aliases
- Modified default field properties
- Calculated fields
- Groups
- Sets

Not included in a .tds file:
- Login info 
- Vizzes created with the data

### Refresh a viz to reflect new data
Tableau is flexible about `data source updates`. `Adding more columns or rows` to the data source won’t break the viz. 

However, `there are some updates that Tableau can’t accommodate`, like `changes to the structure of the dataset`, such as `rename or remove columns`. Viz will only be impacted by changes to fields that is uses. It can be fixed by replace references for that field. 

### Data extract
A `data extract` is a local subset of a data source: 
- You can create extracts that contain `billions of rows` of data.
- Can be `faster` than working with the original data, because they are usually `smaller` than the original data source. Generally experience `better performance` than the live connections to the original data.
- Allow you to take advantage of `additional functionality` that's not available or supported by the original data, such as the ability to compute a distinct count.
- Allow you to save and work with the data `locally` when the original data is not available. Provide `offline access`, `portable`. 
- An extract is a subset of the data, which `limits access to the remainder of the data`. This can aid in data security, administration, and load on workbooks.
- When the original data changes, you need to `manually refresh` the extract. Extracts can be configured to be `full refresh` (default, can take long time for large extracts), replacing all of the data with what’s in the original data source, or `incremental refresh`, adding just the new rows since the previous refresh. An incremental refresh is only possible when you are extracting `all rows` in the database. For `Tableau Desktop`, you can `automate extract refreshes` using the Tableau Data Extract Command Line Utility. For `web authoring`, you can `schedule refresh task`s for `published` extract data sources and published workbooks that connect to extracts. 
- Unfamiliar users `may not realize that some data has been filtered` from the original data source. A good design practice for extracts is to `inform the end user` about what is included and not included in the extract via notes or instructions in the views and dashboards.

**Best practices for incremental extract refreshes:**
- Use full refresh whenever possible. 
- Incremental refreshed extracts should be fully refreshed at regular intervals (e.g. every weekend or monthly) to maximize performance.

Beginning with Tableau version 10.5, when you create a new extract, it uses the `.hyper format`, which takes advantage of the improved data engine which supports faster analytical and query performance for larger data sets. When you perform an extract-related task on a (old) `.tde` format using Tableau version 10.5 or later, the extract is `upgraded to a .hyper` format. After a .tde extract is upgraded to a .hyper extract, it `can't be reverted back`. 

To create an extract, you can do it from the `Data Source page`, or from the `worksheet` so you can choose to only extract the part of data used in the view. Start the extract creation from the worksheet allows you to `configure the extract before Tableau creates it` - can save time for large data sources. You can edit a  extract after you have created it. 

In web authoring (requires Creator role), you can create extracts directly with default extract settings. Extract refreshes for web authors requires Tableau Bridge. 

**Best practices for creating a data extract:**
- `Aggregate` data: so it is much smaller than the transaction level data extract,  which improves query performance.
- `Hide` all unused fields: it can speed extract creation and to preserve storage space.
- `Filter` data:  remove data you do not need.

### Logical tables vs. physical tables in an extract
Two ways to store data in extract: `logical tables` or `physical tables`:
- `Recommended:  Logical tables`, which is the default.
- The `Physical tables` option should be used `sparingly` to help with specific situations such as when the `size of your extract is larger than expected`.

**Logical tables:**

If you use `Logical tables` when your extract contains `joins`, the `joins are applied` when the extract is created.

Use Logical tables when:

- you want to limit the amount of data in your extract with additional extract properties like `extract filters, aggregation, Top N`, or other features that require denormalized data.
- your data uses `pass-through functions (RAWSQL)`.

**Physical tables:**

Physical table uses one extract table for each physical table in the data source. If you use the physical tables, `joins are performed at query time`. Also, you `cannot append data` to it.

Use Physical tables when:
- your extract has `tables created with one or more equality joins` and meets all of these conditions: All joins between physical tables are equality (=) joins; Data types used for relationships or joins are identical; No pass-through functions (RAWSQL) used; No incremental refresh configured; No extract filters configured; No Top N or sampling configured
- the size of your extract is `larger than expected`.

## 🏷 Organize data and create filters
### Group
A group lets you combine several `members` (values) `inside a single dimension (field)` into `a single data point` or `category type`, `aka, combine into one member`, by `creating a new dimension` that didn’t originally exist in your data. The new group can be used repeatedly in vizzies. Existing groups can be edited. 

Groups in Tableau are represented by a `paper clip`: <img src="images/group.png" style="width: 2%">. In the `Data pane`, the paper clip to the left of the field indicates a grouped field. In the `tooltip` in the `view`, the paper clip is the `Group Members button` that creates a group.

Groups can be used in diverse ways to answer questions about your data:
- `Ad hoc analysis` - Grouping the destinations that loses the most airline packages that allows the company to discover what they have in common. Group sales of previous exhibits by audience to determine which brought the most visitors in the past. 
- `"What if" scenarios`: Determine what will bring the most profit for future investments by grouping long list of products into categories, to make informed decisions based upon overall profit. 
- `Correcting data errors`: Avoid data duplication (typos): Grouping CA, Calif., and California into one data point. Name changes: A product is renamed, but product itself didn't change - grouping allow to see sales before and after the name change.
- `Reuse`: After the groups are created, they can be used in other ways. 

Groups can be created using:
- `A field in the Data pane`: good for long lists, allows search (exact match, contains, starts with), can drag a member into an existing group in the window, can choose to create a "Other" group to group all the un-grouped members. 
- `Labels or marks in the view`: when you select multiple labels or marks, use the pop up tooltip window to group them. During this process, a group contains selected items is created, also a group called others is created. The newly created group field is instantly used in the view. 

### Hierarchy
A hierarchy is an arrangement of data fields in a hierarchical format with an "above" and "below" structure. A hierarchy preserves the ordering, creates drilling capabilities in the visualization,  and it can be used over and over. Its icon: <img src="images/hierarchy.png" style="width: 2%">. 

One of the most useful ways to navigate hierarchies is to drill down using the [+] or drill up using the [-] to hide or display the related fields. The symbol appears on the left of the field when it's on a shelf, on the Marks card, or in the view. 

Date hierarchies: For relational data sources, dates and times are automatically placed in the dimensions area of the Data pane and are identified by the date icon <img src="images/date.png" style="width: 2%">, or date-time icon <img src="images/datetime.png" style="width: 2%">, and can be drilled up and down as a hierarchy. Date fields can consist of Year, Quarter, Month, Day, Time. Notice that the list order must be preserved for the hierarchy to make sense.

Common examples of subjects with hierarchical categories: Biological classification, Family tree, Geographical locations. 

### Filters
Filtering does not remove or modify data, it just changes the data that appears in your view. 

Filter types
- **Extract filters**
When creating an extract, filter out irrelevant data. 

- **Data source filters**
Reduce the amount of data being fed into Tableau. Can be used to filter out sensitive data from data source. For systems that rely heavily on partitions or indexing, data source filters may yield tremendous control over the performance of queries issued by Tableau. 

- **Context filters**
All filters in Tableau are computed independently. Context filter is processed first. If you have two dimension filters, one on Region and another top 3 on products, both filters will apply to the entire data set, e.g: product A, D, F are globally top 3, but only A lives through the region filter, so the final result will show only product A. If you want to see the top 3 products in each region, need to set Region as the context filter, in this way, product A, B, C might be the top 3 and all will show up. Context filters are greyed out in the filter pane.You may also create a context filter to improve performance. You can further improve performance of context filters on large data sources by: Use a single context filter; Complete all of your data modeling before creating a context (Changes in the data model, such as converting dimensions to measures, require recomputing the context); Set up context filters before adding fields to shelves.

- **Dimension filters**
Dimensions contain discrete categorical data, so filtering it involves selecting the values to include or exclude. For example, use a dimension filter to show sales in specific regions.

- **Measure filters**
Measures contain quantitative data, so filtering it involves selecting a range of values that you want to include. For example, show only products that have sales greater than 10,000.

- **Date filters**
Date filters allow you to filter data by a range of dates, relative dates, or exact dates. For example, show products that have been ordered starting January 2017. 

- **Table Calculation filters**
Applied after the view has been produced. Suitable if you want to filter the view without filtering the underlying data.

Order of Filters:

<img src="images/filter-order.png" style="width: 60%">

Dimension filter: The easiest way is to include or exclude data points (marks) from your view. Another way is to drag the dimension field from the Data pane to the Filters shelf.

Filters can be created on fields that are not in the view. On Tableau Desktop, you can right click fields in data pane and select show filter. Filters can be reused across worksheets (not default). In filter window, 'Use all' is dynamic and adapts to changes, 'Select from' is static and ignores changes. 

You can customize the look and interaction of a filter. The Remove Filter option removes the filter from the Filters shelf. Hide Card/Filter only removes the filter card from the view. 

Tableau can create filters on continuous date values or discrete date parts. For continuous data filter, you can filter by relative dates, range of dates, starting date, ending date, and special (null). 

### Sorting
Computed sort (dynamic) and manual sort. As an author, you can disable the sort icons in published content.

When the values to be sorted occur in multiple panes in a view, there are two ways to sort: nested sort (considers each pane independently and sorts the rows per pane) and non-nested sort (default, considers the value across panes and will have the same order of values per pane).

### Set
Sets are custom binary fields that define a subset of data - for viewing and highlighting data that meet specific criteria. For instance, sets can help you identify customers with sales exceeding a certain threshold. Set can be dynamic (members change with data, can be based on single or multiple dimensions), or fixed (members do not change with data, based on a single dimension only). Sets can be reused throughout the workbook, and it is part of the metadata and saved in .tds file. Sets can be used like any other field in a view (to encode marks, use in calculated fields, use as dimensions (in/out a set), use as filters). 

Use cases for sets:
- View or highlight data that meets a specific computed condition, for example, a set  contains customers with sales exceeding a certain amount.
- Monitor key data points, for example, high- or low-performing sales regions.
- Show members in a field that meets a few conditions, e.g., items that are top sellers but are also highly discounted.
- part-to-whole comparison
- part-to-part comparison (set to set)

You can create a fixed set by selecting marks in a view or using the Create Set option for a dimension from the Data pane. 

In Tableau Desktop, you can combine two sets - you create a new set containing either the combination of all members, just the members that exist in both, or members that exist in one set but not the other. To combine two sets, they must be members of the same field.

To give your audience the ability to quickly modify members of a dynamic set, you can also display a set control. A set control is a worksheet card that is very similar to a parameter control or filter card.

Based on the filter order, Tableau applies set filters before dimension and measure filters. 

## 🏷 Build views
### Visualize time-based data
Tableau provides two ways to visualize date fields: as continuous date values or discrete date parts (default); they are interchangeable in the data pane. Continuous date values, also called date values, represent the chronological progression of time. Date values appear as green fields when placed on a shelf. Discrete date parts are distinct units of time contained in your data. 

Use continuous date values to visualize how your data changes over a range of time. Use discrete date parts when you want to compare a measure for specific units of time

When you add a date field to a view, Tableau automatically selects the highest discrete date part (default) in your data to display. You can change it. 

Note that selecting "Discrete" or "Continuous" from the date field drop-down menu will not change whether a date field is used as a discrete date part or a continuous date value in the view, it will only change how the data is displayed (as headers or axis). You need to select explicitly the lod of the continuous date or discrete date in this dropdown menu. 

If your organization uses a week-based calendar, with Monday as the first day of the week, you can specify the ISO-8601 calendar as your preference for your data source. This change will apply to all worksheets using the data source, affecting date fields, context menus, filters, and so on. 

You can create `custom date fields` in Tableau Desktop, using discrete dates part or continuous date values, and use them in views so they provide users the exact experience you want. Custom date field has a plus sign in its icon. 

You can create a custom date hierarchy from discrete date parts. 

The Data pane always contains several fields that do not exist in your original data source, two of these are Measure Values and Measure Names - they serve as containers for the measures in the Data pane. Tableau automatically creates these two fields for each data source when you connect it to a workbook. 

The Measure Values field is a measure that contains the values of the measures. The Measure Names field is a dimension that contains the names of the measures. Note that it does not include measures such as Latitude, which do not aggregate the same way as other measures.

Text tables can contain up to fifty measures on Rows and sixteen on Columns. Measures in a text table use the text mark.

You can build dual-axis charts in Tableau - you need two measures and one/more dimensions. 

You can add annotation to data points in a view. 

Text tables can be used for drilling down from summary visualizations to more detailed information, such as when a text table is used as a filter in part of a dashboard. You can create a text table from an existing view or from scratch. You can use the Analysis menu to add these aggregations (such as totals, subtotals, or averages of columns and rows to provide users with high-level information) to a text table.

A highlight table enables you to apply color to a text table when you need to show every value but also want to show patterns or extreme values.

Pie charts are built solely on the Marks card (Angle); no fields are placed on rows or columns.

Tree maps display data in nested rectangles. Dimensions define the structure of the tree map, and measures define the size and color of the individual rectangles. Tree maps and pie charts are good choices for showing part-to-whole comparisons. But, unlike pie charts, tree maps are good for displaying data sets with long tails, those that have many small values that contribute to the whole dataset. The basic building blocks for a tree map are the Automatic or Square mark type, one measure on Color and Size, and one dimension on Detail. By default, when building a tree map, negative values are hidden from the view. In Tableau Desktop you can click the button on the right bottom of the view, and choose to Use Absolute Values. 

You can build word clouds and packed bubble charts from tree maps by changing the mark type to text. 

Bar-in-bar charts and bullet graphs have a similar goal: to compare two values in a bar chart-style view. In a bar-in-bar chart, you're usually comparing two measures against one another. In a bullet graph, you're usually comparing a measure against a goal or threshold which is a reference line, and can have reference bands. Both the bar-in-bar chart and the bullet graph are derived from the side-by-side bar chart, but the former two are visually less crowded and more direct—making the information easier to see and understand.

### Custom Color and Shape Palettes
You might create a custom color palette so marks in your views use the colors adopted by your organization or occupation. There are three types of color palettes: categorical, sequential, and diverging. 

Tableau Desktop: For workbooks with Excel and text file-based data sources that are saved as Tableau packaged workbooks, meaning .twbx files, the custom color palette information is embedded in the workbook, so you can share the workbooks with other people in Tableau Desktop, and the custom colors on the marks will display as they did for you. The palettes are also available to other users, in the Edit Colors dialog box, to assign to views they create in the workbook.

Tableau Cloud/Tableau Server: After you publish a workbook that uses custom color palettes, when other people create workbooks in Tableau Cloud or Tableau Server, the palettes won’t be available to them in the Edit Colors dialog box, and they therefore can’t use the colors in the custom palettes or assign the custom palettes to views in workbooks.

You can create a custom shape palette in Tableau Desktop so marks in your views use more intuitive shapes, such as the shape of traffic signs for data related to traffic planning.

## 🏷 Map geographic data
### Symbol and Filled maps
Two map types in Tableau: `symbol maps` (uses symbols to represent a central point of a geographic region, effective for showing quantitative data for individual locations,  work best with data containing large variations of values) and `filled maps` (shows boundaries of a geographic region, filled with color, ideal for showing ratio data). 

When building map views, Tableau supports any latitude and longitude coordinates, as long as they are in decimal degrees. Tableau can also recognize and geocode the following geographic information types: Worldwide airport codes, Cities, Countries , Regions , Territories, States , Provinces, Some postcodes and second-level administrative districts (county-equivalents) , Core Based Statistical Areas (CBSA), U.S. area codes, Metropolitan Statistical Areas (MSA) , Congressional districts , Zip codes. 

For a symbol map, use the following building blocks in the Tableau workspace:
| Place | Content |
| ----------- | ----------- |
| Columns shelf | Longitude (continuous measure, longitude geographic role assigned) |
| Rows shelf | Latitude (continuous measure, latitude geographic role assigned) |
| Detail | One or more dimensions |
| Size | Measure (aggregated) |
| Mark type | Automatic |

For a filled map, use the following building blocks in the Tableau workspace:
| Place | Content |
| ----------- | ----------- |
| Columns shelf | Longitude (continuous measure, longitude geographic role assigned) |
| Rows shelf | Latitude (continuous measure, latitude geographic role assigned) |
| Detail | One or more geographic units (dimensions with geographic roles assigned) |
| Size | Measure or dimension |
| Mark type | Automatic or Map |
	
You can resolve ambiguous geocoded location data by: Specifying the Country/Region and/or State/Province for your data.

A filled map shows ratio or aggregated data in shapes known as polygons. The polygons can be countries, regions, states, or almost any area that can be geocoded in Tableau. (An exception is cities, which won't allow for a filled area.) The distribution you specify for the color of the polygons (gradients vs. stepped, and the number of steps) highly affects how people interpret your data. To make the variation more apparent, reduce the number of visible color shades on the map. The level of detail you specify in a filled map determines the patterns you want to see in the data. To simplify the pattern, aggregate up to a higher level of detail. To make smaller trends more visible, aggregate down to a lower level of detail. 

You could customize Tableau's Geocoding. You could also plot data on a custom background. 
	
### Density Maps
A density map shows the frequency of marks in an area. By grouping overlapping marks, and color-coding them based on the amount of overlap, you can create a density map to reveal trends.

Density maps are most effective when the location data is very precise, such as location coordinates in a limited space. For example, events associated with specific street-level addresses. Additionally, density maps work best where the specific locations change continuously and smoothly across space, rather than values constrained to discrete locations such as district, borough, or neighborhood. The density mark can be useful with scatter plots, too, especially if you’re more interested in the patterns than the outliers.

For a density map, use the following building blocks in the Tableau workspace:
| Place | Content |
| ----------- | ----------- |
| Columns shelf | Longitude (continuous measure, longitude geographic role assigned) |
| Rows shelf | Latitude (continuous measure, latitude geographic role assigned) |
| Detail | One or more fields with many underlying data points |
| Mark type | Density |

## 🏷 Create calculated fields
Calculated fields allow you to create new fields from data that already exists in your data source. You can create calculated fields to compute a ratio, manipulate string and date fields, convert the data type of a field, and combine and aggregate data. A calculation, also known as a formula, includes some or all of these components: Fields, Functions, Operators, Parameters, Comments. After you build a calculated field, use it in your view just as you would any other field. 

You can also create ad-hoc calculations using existing fields or on an empty shelf in the view. To save an ad-hoc calculation for use in other workbook sheets, CTRL + drag it from the view to copy it to the Data pane, and you can rename it.

String functions allow you to manipulate data made of text, or string data. Common string functions: LEFT (string, number), RIGHT (string, number), SPLIT (string, delimiter, idx of substring start from 1), CONTAINS (string, substring), REPLACE (string, substring, replacement), UPPER (string), LOWER (string), TRIM (string). 

Type conversion functions allow you to convert fields from one data type to another. 

Tableau date parts include: 'year', 'quarter', 'month', 'dayofyear', 'day', 'weekday', 'week', 'hour', 'minute', 'second'.  Note that they must be singular, all lowercase, and wrapped in single quotation marks. Date functions include: DATEPART (returns a number), DATENAME (returns a string), DATEADD, DATEDIFF, DATETRUNC, MIN and MAX. 

If you are using a .hyper extract, date functions can also be calculated using the ISO 8601 Standard format, which differs from the Gregorian calendar because of how it calculates the starting week of a year. 

When Tableau automatically aggregates measure fields, SUM is the default aggregation. Aggregate functions allow you to summarize data by performing a calculation on a set of values at the level of detail in a view, and return a single value. For example, you might want to know the distinct count of attendees at your company’s annual conference over time. You can use the COUNTD function to calculate the distinct number of conference attendees and then break the visualization down by year. Aggregate functions: SUM, AVG, MEDIAN, COUNT, COUNTD, MIN, MAX.  

Use cases for aggregate dimensions: 
- When dimensions are used in calculations that contain aggregated measures
- the questions you need to answer with your data require an aggregation
- if your data contains multiple values for a dimension, and you want to show only one value, you can aggregate them into a single value.
- When you’re blending multiple data sources in which the dimensions don’t have a consistent level of detail, Tableau will aggregate the linked dimensions to the same level of detail.

## 🏷 Apply Table calculations & Secondary table calculations
Table calculations are calculated fields that you apply to the values of a measure in a visualization. They compute the local data based on what is currently in the view. You can use table calculations to transform values to show rankings, running totals, percent of total, etc. You can use a quick table calculation using builtin calculations and preset configs, can manually configure calculations, and can build complex custom table calculations. 

List of quick table calculations:, Running Total, Difference, Percent Difference, Percent of Total, Rank, Percentile, Moving Average, YTD Total, YTD Growth, Compound Growth Rate, Year Over Year Growth. 

For difference calculation, you can hide or filter the null value, or show null data at default position. 

Scope refers to the segment of the data to which the calculation is applied. We can apply a table calculation to the values within a table, a pane (such as Category and Sub-Category), or a cell. Direction refers to whether the calculation is applied and computed across or down the defined scope. You can opt to show Row and/or Column Grand Totals. 

Table calculations are continuous measures by default, and continuous measures always display to the right of dimensions on a shelf, so we needed to convert the field from continuous to discrete before we could place it between dimensions on the shelf.

In the table calculation window, when selected, Show calculation assistance uses highlighting and numbering to demonstrate how the calculation is being computed. 

Table calculations are not automatically added to the Data pane, but you can save it manually by dragging it into the data pane and give it a name. Note that, when you use this field, it’s dependent on the other fields in the view, so it may need modification.

To add a customized table calculation, click the drop-down arrow on a measure field in the view and select Add Table Calculation to open the Table Calculation dialog box.

When you add a table calculation, Tableau automatically selects which dimensions define the scope and which define the direction. However, if you want to control which dimensions define the scope and which define the direction, use the Specific Dimensions option. This option will lock in the scope and direction regardless of the table structure.

## 🏷 Create Level of Detail (LOD) expressions
Level of detail (LOD) refers to the aggregation or granularity of the data. LOD expressions allow you to determine the levels of detail used in a calculation without actually dropping those dimensions into the visualization. LOD uses keywords to perform calculations at a more granular level (INCLUDE), a less granular level (EXCLUDE), or an entirely independent level (FIXED).

For example, to see sales percentage of one country in global sales, [sales] / sum([sales]), but if only want to see sales percentage of this country in north america (regional), then use [sales] / {FIXED [Region]:sum([sales])}. 

FIXED LOD expressions compute a value using the specified dimensions, without reference to the dimensions in the view. Example: Compute the sum of sales per region: {FIXED [Region] : SUM([Sales])}

INCLUDE LOD expressions compute values using the specified dimensions in addition to dimensions in the view. Use it when you want to calculate at a fine LOD in the database and then re-aggregate and show at a coarser LOD in your view. Fields based on INCLUDE LOD calculations will change as you add or remove dimensions from the view. Example: The following INCLUDE LOD expression computes total sales per customer: { INCLUDE [Customer Name] : SUM([Sales])}

EXCLUDE LOD expressions declare dimensions to omit from the view LOD. Use it for ‘percent of total’ or ‘difference from overall average’ scenarios. It cannot be used in row-level calculations (where there are no dimensions to omit), but can be used to modify either a view level calculation. You can use an EXCLUDE calculation to remove a dimension from some other LOD expression. Example: Compute the average sales total per month and then excludes the month component: { EXCLUDE [Order Date (Month / Year] : AVG ({ FIXED [Order Date (Month / Year] :  SUM([Sales])})}

In Tableau, cohort analysis is a common use of FIXED LOD expressions. A cohort refers to a group that shares common characteristics over a period of time: for example, customers who purchased their first items on the same date; students who graduated college in the same year; or patients in a pharmaceutical trial who received the same dosage of a drug at the same time. So, instead of looking at the entire data set, it is broken into related groups. Cohorts help data analysts detect changes in trends and determine the outcomes that are associated with the cohort. e.g.:
- {FIXED [CustomerID] : MIN([Order Date])} Creates a calculated field to show the first time a customer made a purchase.
- {FIXED [Country] : SUM([Confirmed Cases])} Creates a calculated field to show each country’s total confirmed cases.





## 🏷 Apply analytics
### Reference Lines and Bands
You can add reference lines, reference bands, distribution bands, and box plots to identify specific values or ranges on a continuous axis. You are able to create an unlimited number of reference lines, reference bands, distributions, and box plots.

### Parameters
A parameter is like a variable in an equation, where the value can be controlled by the end user. It could be anything, such as a number, date, or string that can replace a constant value in a calculation, filter, set, or reference line. 

For example, you may create a calculated field that returns True if Sales are greater than $2000 and otherwise returns False. You can replace the constant value of “2000” in the formula with a parameter. Then, using the parameter control, users can dynamically change the threshold in your view.

Parameters let you 
- Dynamically modify values in a calculation. 
- Customize filters (for top N filter, N can be a parameter). 
- Dynamically modify a reference line, band, or box. 

Parameters vs filters:

| Parameters | Filters |
| ----------- | ----------- |
| Able to select from a set of variables | Show a subset of the data |
| Unable to select multiple values | Able to select multiple values |
| Faster | Slower |
| Can be used in a calculated field | Cannot be used in a calculation |
| Support multiple datatypes | Do not support multiple datatypes |

Dynamic parameters updates automatically, and you can
- Link a data source field to the parameter’s list of values, so Tableau will pull the most up-to-date field values every time a user opens the workbook.
- Specify what the parameter’s current value should be when the workbook opens. 

Note that for dynamic parameters:
- The order in which dynamic parameters are populated is based on the default sort of the field. Default is the data source order. If you want new values to fill in at the bottom rather than alphabetically, set the default sort to manual.
- When setting the value to a calculated field, the calculation should be viz-independent. Also if using a Fixed LOD calculation, it cannot be a nested LOD calculation.

You can use parameters to swap measures in a view. If you're working with a data source that's got a lot of data, you may find yourself in a situation where the audience for the data would benefit from having it presented in one interactive view, rather than spread between multiple views. 

### Histograms (show distribution)
A histogram groups values together into buckets/bins that you define.

### Box & Whisker Plots (show distribution)
histograms show only one distribution of data along an axis; box & whisker plots are useful to compare multiple distributions of the data - they group values into four quartiles, with:
- the middle two quartiles constituting the "box" 
- the upper and lower quartiles located near the top and bottom as "whiskers".

Note that the IQR (InterQuartile Range) captures data that's 1.5 times the middle 50% of data, which sometimes results in values outside the whisker. Therefore it is a good plot for seeing outliers. 

### Trend lines and forecasts
You can use trend lines to make predictions about your data.

You can build forecasts in your views using Tableau Desktop. Tableau Desktop provides built-in statistical models to forecast your data, including models that account for seasonality and trends. 

### User parameters to swap measures


## 🏷 Multiple data sources
There are many ways to combine data in Tableau. Relationships are the default method. 
### Relationships between tables
Relationships are a dynamic, flexible way to combine data from multiple tables for analysis. They are the default way to work with data from multiple tables in Tableau and are created directly on the Data Source canvas. When drag tables out of the sheets pane, Tableau will automatically relate the tables if there is a common field name. You can hover over the relationship line for details. Relationships can be edited after creation. 

You can view fields and data of each table in the data source page, or in the data pane of a worksheet. 

In the data pane of a worksheet, tableau automatically generates a row count for each table. Other automatically generated fields include Latitude and Longitude (if applicable), and Measure Name and Measure Values. You can choose to group by Data Source Table (default), or by Folder (hides the table name). 

Relationships in Tableau Cloud and Tableau Server: 
- You can't edit relationships/joins/unions after publishing a data source.
- You can't define new relationships/joins/unions between published data sources.

Relationships use correct aggregations with no data duplication: Tableau uses relationships to generate correct aggregations and build a query that uses appropriate joins during analysis, based on the current context of the fields in use in a worksheet. The key is “current context.” Use relationships to avoid the data duplication that can sometimes occur when joins are used.

### Join tables
There are four types of joins we can do in Tableau: inner (default), left, right, and full outer. 

Joins are created in the physical layer of the Tableau data model.

When you drag a table to the canvas, you are creating a Tableau data model. The data model has two layers: 
- The default view that you first see in the Data Source page canvas is the logical layer of the data source. You combine data in the logical layer using relationships (or noodles). Think of this layer as the `relationships canvas` in the Data Source page. 
- The next layer is the physical layer. You combine data between tables at the physical layer using joins (and unions). Each logical table contains at least one physical table in this layer. Think of the physical layer as the `joins canvas` in the Data Source page.

To create, view, or edit joins in Tableau, you must open the physical layer. To open a logical table to see it in the physical layer, double-click it.

Joining data with different aggregations or levels of detail can cause data duplication. 

### Union tables
You can use a union to combine data that has a similar structure so that rows from one table are appended to the rows of another table. If there are fields that do not exist in one or more of the tables in a union, you may choose to keep the fields (resulting null values), or remove the fields. Some tables might contain fields that have the same data but have different field names, you can merge them to ensure all of the related values align to one common field. 

After you have created a union, you can edit it, and/or remove it. 

In Tableau, unions can be created manually (tables must come from the same connection) or by using a wildcard search (Tableau Desktop only). You cannot union tables from different databases.

You can create unions in the canvas of the logical or the physical layer of the Tableau data model. 

In the logical layer, if a logical table contains more than one physical table using a union/join, you will see an icon (stacked bars for a union or a Venn diagram for a join) that alert you to the union/join happening in the physical layer. In the physical layer, a union is represented by stacked sheets underneath the first table name in the union.

A unioned table can be used in a join with another table or another unioned table. The reference fields generated by a union to indicate the data source (Sheet and Table Name) can be used as the join key. 

Unions can be created manually or by using a wildcard search (need Tableau Desktop or Tableau Prep Builder). In a wildcard search, Tableau searches for tables or files and automatically adds them to the union based on wildcard search criteria (useful when you want to union multiple tables with similar name). A wildcard search also helps when you expect new, similarly-named tables or files to be added to the data source in the future (If you reload the data source, the wildcard search will automatically include new tables into the union). If you want Tableau to search for and include all available files in a chosen folder or tables in a selected file, regardless of name, leave the wildcard search criteria area blank. You can also expand search to subfolders/parent folder. Wildcard searches are also useful when new, similarly-named tables or files are added to the data source. 

You can rename/edit/remove a union. 

### Blend multiple data sources
Blends are most commonly used when combining data sources, including those with different levels of detail, when you want:
- The link fields to vary on different sheets.
- The primary data source to differ on different sheets.
- Use data sources (json files, cube data, etc) that cannot be combined with the default method (relationship).
- To combine published data sources, but not allowed to edit the structure of them. 

To blend data from two data sources, the data sources need a common dimension.

You can have different primary (blue) and secondary data sources (orange) in different worksheets of the same workbook. 

Data blends expand your flexibility to combine data: Blends, unlike relationships or joins, never truly combine the data. Instead, blends query each data source independently, the results are aggregated to the appropriate level, then the results are presented visually together in the view. Because of this, blends can handle data sources that have different LoD, work with data sources that don’t allow relationships/joins, and work with data sources that have already been published to Tableau Cloud or Tableau Server. 

Data blends cannot be published: Blends are established individually on every sheet. Because there is no true “blended data source,” only blended results from multiple data sources in a visualization, the blended data cannot be published to Tableau Cloud or Tableau Server.

Linking fields can be established manually: When a primary data source has been established by using a field in the view and the secondary data source is selected in the Data pane, any fields with the same name between the two data sources will display a link icon in the secondary data source. If the related field from the primary data source is used in the view, the link becomes active automatically. If the link appears “broken,” click on the icon to activate it.

If there are no link icons on the secondary data source, you can help Tableau establish the link manually.  

there are two methods available for manually establishing the linking fields:
- Add a custom blend relationship (Tableau Desktop only).
- Rename one of the fields to match the other (all environments).

When you use data blending to combine data, a query is sent to the database for each data source that is used on the sheet. The results of the queries are sent back to Tableau as aggregated data. Tableau takes all the data in the primary data source, and only the corresponding matches in the secondary data source(left join-like behavior). If a primary data source row does not have a corresponding row match in the secondary data source, a null value will show in the results. 

Dimension values are aggregated using the ATTR aggregate function, which means the aggregation returns a single value for all rows in the secondary data source. 

Like renaming fields to help Tableau identify linking fields, in some circumstances you can edit aliases for members in those fields. 

use the ZN function to replace null values with zeros. 

### Filtering across data sources
When working with multiple data sources in a workbook, you can filter on a common field to compare the data between them. To enable filtering across multiple data sources, you need to establish a relationship between them. 

## 🏷 Create dashboards
A dashboard is a collection of several views to explore relationships in data. When you modify a sheet, any dashboards containing it change, and vice versa.  This is because data in sheets and dashboards is connected. 

Considerations for planning a dashboard: 
- Knowing and understanding the audience for your dashboard will influence both the content you include and how you present it. Your intended audience will help you to determine which chart types to use, how you arrange the charts on the dashboard, the level of detail you provide, and the level of interaction you build in.
- Consider what the key takeaways are for your audience. Make sure that your dashboard is simple and only includes relevant information, leads with the most important data, provides interactivity so that users can find their own answers and insights, and uses consistent design, language, and color scheme.
- The best visualizations have a clear purpose and work for their intended audience. Are you presenting a conclusion or a key question? Is it to inform your users? Is it to explore the data? Understanding the purpose of a dashboard is crucial in knowing what information to include, and what to exclude.
- Are users going to view the dashboard on different size devices, such as a desktop, laptop, tablet, and phone? If the dashboard will be used on a small device, consider what device-specific composition and content changes will be needed. The more you customize the dashboard to the viewing device, the more you will enhance users’ experience. Will users want to print a dashboard, for example, as a pdf to take to a meeting or look at offline? Depending on the audience and purpose, consider which charts or elements need to be interactive and which could be static.

You can use the settings in the Dashboard and Layout panes to customize your dashboard.

You can hide and unhide sheets/all-sheets from the tab. Show/Hide button lets you toggle the visibility of floating containers. It's possible to reorder floating objects on a dashboard. You can evenly distribute a layout container's items.

Tableau provides many interactive features in dashboards that allow users to explore a dashboard and ask questions of the data (highlighting and filtering, etc.).

You can use highlights to call attention to marks of interest and enable users to explore your dashboard further.  

Filters can be applied to individual worksheets in a dashboard or to all sheets in a dashboard. 

### Actions
Actions are a feature of dashboards that allow users to interact directly with data in the view and access related web-based content. Actions require a source sheet, where the user interacts to run the action. Some actions also use a target sheet, where the results of the action are displayed.

Action types:
- Filter action: guide analysis by using the data from one view to filter data in another. Sends information from a selected mark to another sheet showing related information. (Behind the scenes, it act as filters to the target sheet). Is the most commonly-used action on a dashboard - gives added control to users, enabling drill-down capability between views. 
- Highlight action: call attention to marks of interest by retaining color for specific marks and dimming the rest. You can highlight marks by manually select them, using legend, using the highlighter, or create an advanced highlight action.
- Go to Sheet action: simplify navigation to other worksheets/dashboards/stories.
- Go to URL action: create hyperlinks to external resources, such as a web page, email link, or a file.
- Parameter and set actions: Parameter actions let your audience change a parameter value through direct interaction with a viz, such as clicking or selecting a mark. Set actions let users change the set by directly interacting with marks on a viz.

You can run an action using: Hover (good for highlight), Select (good for everything except URL) or Menu (good for URL actions). 

### Refine a Dashboard
Placement and layout: 
- Decide which worksheets you want to include in your dashboard and make sure that each worksheet you want to use has a title. 
- Layout containers allow you to set the orientation of the items in your dashboard. 
- You can use non-worksheet objects to further customize your dashboard. (Text, Image, Web Page, Navigation, Extension, Export)
- To save space or improve its proximity to another item, you can float a view, filter, legend, text, image, web page, or even a layout container. 
- Add white space by a blank container, or adjusting either the outer or inner padding of a view, container, or object.
- After you have built a dashboard, you can create layouts that are specific to particular devices. As the author, you only have to create a single dashboard and deliver a single URL.

Instructional clarity:
- For filters, change title from Region to Select a Region
- Add text boxes with instructions
- Use a common font color, size and style 
- Sparingly, use annotations to call attention to interesting data points.

Improve appearance and readability: 
- When using crosstabs, don't use Fit Entire View; use a combination of a scroll bar and either Fit Width or Fit Height.
- The quickest way to make a fast, large-scale change to all the titles in your dashboard is to change them at the workbook level. 
- Customize tooltips
- To to reveal more details without cluttering, consider using a view in the tooltip (can set the size, format tooltip text, ). The viz in the tooltip is a static image. 
- You can add smooth animations (to avoid sudden jumps) to highlight changing patterns. Two options: Simultaneous (default, faster), or Sequential (Slower). Can be configured for entire workbooks or to individual sheets. 

### Navigate between dashboards
We can have a Summary dashboard for the organization, which often generates questions that require more detailed information, we then can switch to the Details dashboard to answer them. 

We can add a dashboard filter action to the workbook, and use it to create a navigation link from the Summary dashboard to the Details dashboard, that also applies the filter from the former to the latter. We can also add a navigation button on the Details dashboard that goes back to the Summary dashboard. 

### Containers
Two main types of layout container are Horizontal and Vertical. A horizontal container keeps your objects arranged horizontally next to each other, whereas a vertical container keeps your objects stacked vertically on top of one another.

A container is either Tiled or Floating. Tiled items don't overlap. 

Layout containers can give dashboard viewers the ability to show or hide the container with the click of a button. 

By collecting filters and parameters in a container that has a Show/Hide button, you can enhance dashboard functionality without the filters taking up limited dashboard space.

What if you want to add supplementary instructions to a dashboard to enhance usability, but there isn’t enough room? Solution: Add instructions as a transparent overlay so viewers can toggle on or off as needed.

As a best practice, customize the Show/Hide button to best suit how you want the dashboard user to interact with the container. There are two options to choose from: a custom Text Button or a custom Image Button.

## 🏷 Create stories
### Story telling with data
A story is a sheet that contains a sequence of views and dashboards that work together to convey information. Each individual sheet in a story is called a story point. You can create stories to tell a data narrative, provide context, demonstrate how decisions relate to outcomes, or simply make a compelling business case. 

## 🏷 Share and publish content
### Publish workbooks
You can use Tableau Desktop or web authoring to publish new workbooks to Tableau Server or Tableau Cloud. You can choose which sheets or all sheets to include, decide whether the data is embedded in the workbook or published separately, show sheets as tabs, show selections, include external files. 

Dashboard extensions includes sandboxed and network enabled ones. You can use an extension to:
- Integrate with third-party APIs inside the dashboard.
- Use third-party charting libraries like D3 to add custom visualizations.
- Enable write-back functionality, so that users can modify data in a viz and have that change automatically update the source data.
- Provide custom viz and interactivity types, such as a filter replacement with a custom interface.

You can also create your own extensions using the Tableau Extensions API, a JavaScript library that you link to from your web application.

### Export and download content
At times, however, you may need to work with or share your data insights offline. Perhaps you want to save your findings in a local workbook that you can use while traveling, or you want to engage with the added functionality provided with Tableau Desktop. 

When a workbook is published, the version is same with source tableau version. But if it is modified, then it becomes the version of the modifier tableau version. 

Tableau Desktop version is backward compatible. 

You can generate a snapshot in one of the following formats: Image, PDF, or PowerPoint.

There are two types of snapshots that you can generate for your workbook data: 
- The underlying data for the workbook or a view
- A crosstab, which is a structured output format that generally retains the format of the view

### Publish and manage data sources and extracts
A published data source is one that has been published to Tableau Server/Cloud, and contains one or more reusable connections to data. With a published data source, a server or site administrator can control the permissions for use of the data source, which provides essential data security and oversight.

Other benefits of a published data source: 
- Establishes a central location for connecting to your data.
- Makes a data source reusable & shareable.
- Establishes a "centralized version of the truth" for the data.
- Makes widely available the changes and updates that authors make to the Data pane (such as calculations, sets, groups, hierarchies, and aliases).
- Frees each client from having to download and install database drivers—connecting to data occurs at the server level.
- Uses either live data or data extracts that can be refreshed on a schedule.
- Increases server efficiency by pooling data connections.
- Available for web authors to create a new workbook / add to an existing workbook for blending.

A `Tableau data source file`, saved in a .tds file format, is a published data source that stores `data connection information` and any `metadata changes` you've made to it. "Data connection information" is all the information required to make a live connection to an external—that is, external to Tableau Server—data source. Thus, a Tableau data source file `allows many users to connect to external data sources and have the same experience, with the same metadata settings`. 

An `extract file`, saved in a .hyper file format, is a published data source that contains a snapshot of the data from one or more external data sources. Tableau creates this snapshot by storing extracted data in columns instead of rows. This columnar data structure makes reading and writing data highly efficient, while also enabling compression for faster columnar operations (such as MIN or MAX). You can set up the extract to refresh on a set schedule. 

`Embedded data sources`: Unlike a published data source, which is either a connection to or extract from an external data source, an embedded data source is one that is `part of a workbook that has been published to Tableau Server or Tableau Cloud`. An embedded data source does not exist as a separate object that can be reused by others on the server; users can only access the workbook that contains the embedded data source. You need to specifically publish a data source to share it as a data source. Because an embedded data source exists only within the workbook, it does not have its own page on Tableau Server or Tableau Cloud. Only a published data source can have a separate and distinct page on the server. However, users can view a list of embedded data sources on the Data Sources page by filtering to show either all data sources or just those embedded in workbooks.

Best practices: When sharing data, you want the data to be as clear, clean, and efficient as possible for usability by others:
- Prepare the data: Anticipate the types of questions users will want to answer, and use this to inform your data preparation. Then perform all necessary cleaning, combining, and shaping operations on the data.
- Edit field settings: Assign default aggregations; Set up number formats; Geocode geographic fields; Create meaningful aliases for field values; Use comments to add field descriptions.
- Organize and identify fields appropriately: Set up logical hierarchies; Organize fields into folders; Add relevant calculated fields; Differentiate attributes; 
Avoid naming fields as values. 

Remember that after you publish a data source, you'll no longer be able to rename it directly. Instead, you must publish the renamed copy, and then update all workbook connections.

For your published data source, consider providing lineage information about it. Data lineage identifies where data has come from and the transformations it has gone through over time. This kind of history is particularly helpful for administrators as they monitor and maintain data sources on a site. Creator site roles might help in that effort by providing certain details about their published data sources—details that could also be helpful to other users of the data sources. 

`Tableau Catalog`, which is available in the Data Management Add-on to Tableau Server and Tableau Cloud, automatically discovers and indexes all of the content on the server, including workbooks, data sources, sheets, and flows. It uses indexing to gather information about the metadata, schemas, and lineage of the content. The lineage feature in Tableau Catalog indexes both internal and external content.

The process for publishing a data source varies depending on whether you use Tableau Desktop or web authoring, publish to Tableau Server or Tableau Cloud, and work with a live data source or an extracted, in-memory data source. 

When you are working with extract refreshes, there are two main areas to be concerned with: Scheduling extract refreshes and handling extract refresh failures. Sometimes, something goes wrong with an extract refresh, resulting in an extract refresh failure. If your scheduled refresh fails five consecutive times, Tableau suspends it. When a refresh is suspended, Tableau does not try to run it again until someone corrects the cause of the failure. After you make the correction, run the extract refresh again. 

An extract refresh failure results in two actions by Tableau:
- You'll see an alert icon appear in the Notifications menu at the top-right corner of the user interface (UI).
- As the owner of the data source, you'll receive an email indicating that an extract refresh failure occurred.


### Tableau Prep Builder
In Tableau Prep Builder, both the data preparation operations you’ve performed in the flow and the data you’ve prepared can be published. 

### Other stuff
In addition to creating, running, and publishing flows and flow outputs from Tableau Prep Builder, you can work with flows on the web.

Subscriptions: Subscribing to your favorite workbook or view helps you to keep current on the latest data updates.

Sometimes you want to be notified as soon as something very specific happens in the data. For example, maybe you want to be notified as soon as your team hits its sales quota, or when a stock price drops below a certain dollar amount. If you want to be notified when your data reaches important thresholds like these, set a data-driven alert. When the data reaches the specified threshold, you will receive a subscription email which has several components:
- The target threshold 
- An image of the view
- Links to manage the alert

On a Tableau site, the best way to save your specific analysis is to create a custom view of your work. A custom view is a saved version of a view with your selections and filters applied. You can then use that custom view for yourself, and can optionally share your insights by making your custom view available to others. Custom views can be accessed only from the view itself and are not saved as distinct views from the original. 

MWhat if you have important, individual numbers that you are trying to keep track of, such as total sales? Do you need to open the view each time you want to see the latest number? No, you can use a metric. Metrics provide a fast way to stay informed about your data. Metrics help you monitor changes to your data in a format that's easy to interpret at a glance. 




