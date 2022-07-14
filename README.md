# Tally
5236 Android Development Project

Show:
<p float="left">
  <img src="https://user-images.githubusercontent.com/36163586/178882162-0aee0195-66ac-43ff-8999-432e186ef67a.jpg" width="100" />
  <img src="https://user-images.githubusercontent.com/36163586/178882167-4a0ccaf5-8ccc-4d56-ae06-ddc9cede048d.jpg" width="100" /> 
  <img src="https://user-images.githubusercontent.com/36163586/178882171-665d3bde-c4cf-47a4-b8b8-e465ec3ee485.jpg" width="100" />
</p>
![1](https://user-images.githubusercontent.com/36163586/178882162-0aee0195-66ac-43ff-8999-432e186ef67a.jpg "1")![2](https://user-images.githubusercontent.com/36163586/178882167-4a0ccaf5-8ccc-4d56-ae06-ddc9cede048d.jpg)![3](https://user-images.githubusercontent.com/36163586/178882171-665d3bde-c4cf-47a4-b8b8-e465ec3ee485.jpg "2")
![4](https://user-images.githubusercontent.com/36163586/178882174-2bbc28a6-42eb-408d-ad00-3bde46f00404.jpg)![5](https://user-images.githubusercontent.com/36163586/178882176-efb48658-7df7-4109-a899-e150dd6078bd.jpg)![6](https://user-images.githubusercontent.com/36163586/178882178-21e335a0-9e15-4a5d-b53c-f7190a4c91e3.jpg)![7](https://user-images.githubusercontent.com/36163586/178882179-e379892c-9f71-4d3f-95f9-a123d0a582e1.jpg)

# Tally final report
## Section 1 – Introduction
 At present, most college students have difficulty in planning their monthly expenses properly, which is the same as me. Therefore, our group decide to design an app to help users achieve the balance of payment records, which is named “Tally”. Through this app, users can see monthly payments, monthly expenses, budgets and records of each payment directly on the home screen. Besides, there are also search, budget, charts, records and selection categories to choose from, providing users with easier visual images.
When clicking on the search icon, user can see a frame to find any particular payment or receipt. If the user clicks on budget icon, he can see a new frame and enter his target budget. When the user selects the chart module, the app opens a new screen where the user can see a histogram of monthly payments and receipts. Scales for different categories will be displayed at the bottom, and a calendar icon in the upper right helps users change the month. After that, the user can click the back arrow to return to the home screen. Clicking the Record button takes the user to a new screen with a back icon in the upper left corner that helps the user return to the previous screen. In this interface, users can record payments or receipts for various purposes, and can add comments and adjust the recording time. After the user completes this operation, the application will automatically return to the main interface, and the record will appear on the main interface. If the user clicks the Select button, a new interface pops up at the bottom with about, Settings, Records and billing icons. In Settings, the user can reset all stored records, but he should do so carefully. In the record module, the user can see the specific record of each month, and can click the calendar icon to change the month.
While most of the above features are already available on the market, there is no application to put them together. Therefore, we believe our app can be useful for those who want to make a reasonable balance of payments.
One of the features of our app is convenience, which means a user can easily create his own bill and find out if it meets his target budget to help him adjust his spending habits. To help users determine where their income is coming from and where they are spending, we created histograms to visualize the data and show their proportions.

## Section 2 - Design Process
Once the idea was presented, we started thinking about how to turn it from an idea into a reality. First of all, we started thinking about what features our app should have. In the beginning, we envisioned some simple features, including editing our target budget, keeping track of every income and expense we made, and deleting error records. Later, in order to more conveniently check the time and detail of each record, we added the calendar function and search function, so that users can conveniently search the income and expense records with time or details. Of course, users can also see the history record list at the main page directly.
In addition, we found that there was a lack of statistical function to realize all the consumption amount and income amount, so we added a statistical function to facilitate users to intuitively see the total consumption and total expenditure of each month. In order to make it more convenient for users to see where they spend their money, we also provided categories for each purchase, such as travel, education, etc. In addition, we also provided histogram charts to make consumption and income records much clearer.
Finally, we also need an “About” page to show the information of the developers and a “Setting” page to reset user information.
At this point, we’ve come up with all the nouns and verbs associated with the function of our application. They are as follows:
Nouns: user, income, expense, budget, chart, payment, receipt, record, bill, calendar, setting.
Verbs: add record, delete record, display history records, view chart, search record, choose date, edit budget, see about, reset.
From these nouns and verbs, we started creating the corresponding classes [5], including income record, outcome record, search, budget, chart and setting. For the income record and outcome record classes, the most desirable functions are add, edit and delete operations. As for search classes, it relates to income record and outcome record classes, which is the same as chart classes. The budget class can independently set amount of budget, but it still needs to rely on outcome record class to give users the remain budget. For setting class, it can reset all records that users have created. Therefore, it also relates to income record and outcome record classes. You can see that the most important classes above all are income record and outcome record classes.
Next, we needed to set up database about these classes to store data for our users. The record class needs id(record id), typename(such as food, salary, traffic...), sImageId(images for different types), detail, money, time, year, month, day, kind(income as 1 and expense as 0). All of other classes are just surrounded by the record class. Just like setting class, it needs to have right to access record classes to erase all records. And for search class, it also needs to have right to access record class to find out what users want. The chart class needs sImageId, type, ratio and total money. The barChart class which helps us to draw chart needs year, month, day and sum_money.

## Section 3 - Translating Design to Implementation
After having completed the design process, our team started using android studio [1][3][4] tool to design our application to make it possible to implement it on android opening system. First of all, we design activities: MainActivity, RecordActivity, HistoryActivity, ChartActivity, SearchActivity, AboutActivity and SettingActivity. And we wrote the layout xml file and activity class for these activities.
Then, we wrote SQL [7] statements to test if we could insert data information. We wrote DBOpenHelper to create two tables: type_tb( record the types of different records) and account_tb( record each record). In order to make it simple to choose time, we wrote time selection dialog box. And at this time, we can do some simple records. And we use DBManager to manage database: read database and write it into storage; insert record into database; calculate the sum income and expense money of every day, month and year; search database record with keywords; calculate the sum income and expense money for every type.
In addition, we wrote the BaseRecord fragment [2]. And we wrote IncomeRecord fragment and OutcomeRecord fragment to extend the BaseRecord fragment. We also wrote the TypeBase adapter for adapt design.
In order to further improve it, we added history record function to our application and completed drawing and logic writing. Besides, we all added calendar dialog box to history record function, so that users could search monthly record easily and it was also convenient for the following monthly bill analysis. We also wrote the Detail dialog, SelectTime dialog, Budget dialog and More dialog.
We completed charts for monthly bill analysis by MPAndroidChart [6], where we used percentage calculation to show income and expenditure type. As the part of record fragment, we write the BaseChart fragment and then write IncomeChart fragment and OutcomeChart fragment to extend it.
Finally, we create the adapter file for adapt design. The adapter file includes
 
Account Adapter, Calendar Adapter, ChartItem Adapter, ChartItem Adapter and RecordPage Adapter.

## Section 4 - Suggested Changes and Improvements
Review of design and implementation process, we designed a lot of functions, without considering their practicability and maneuverability, which leaded to waste too much time on these useless designs. And because the design is not rigorous, we had to a lot of repeated work. As a result, the next time we need to make the relatively well-developed design and try to reduce the overlapping functions in the application.
During the design process, we should also evaluate the implementation of each piece of functionality and prioritize them. This would allow us to allocate our time and energy to different prioritized features so that our team would have a clear picture of progress and are able to complete tasks on time.
We wasted too much time doing separate database stores during execution, but sometimes these databases could be shared with each other. If we saved this time, we could focus more energy on the design process to make data sharing between different functions better, thus reducing code redundancy and reducing memory footprint.
During execution, we can also add some more detailed features. For example, set a minimum balance alert that automatically turns red when the monthly balance falls below this value to alert the users. We can also mark red to records of excessive spending. In addition, we only have a histogram chart for monthly consumption, and we will add the function of annual summary in the future.
In addition to adding new features, we can also enhance existing features. For example, for delete operations, users can only delete a single record once a time or reset all records he has stored. In the future, our team plan to enhance this operation so that users can delete all records over a certain period of time, such as all records in March.
## References
1. Android Open Source Project, Android, http://developers.android.com
2. Fragments, Android, https://developer.android.com/guide/components/fragments.html 3. Android Open Source Project, Android, http://developers.android.com
4. Android Tutorial: Implement A Shake Listener, http://jasonmcreynolds.com/?p=388 5. Java API, https://docs.oracle.com/javase/7/docs/api/
6. MPAndroidChart, https://github.com/PhilJay/MPAndroidChart
7. SQLite, https://www.sqlite.org/index.html
