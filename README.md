# Summary
To get the PM2.5 daily data from CPCB(India) for all stations located in Kolkata and Lucknow using code only, and provide an interactive 365-day running average chart for these two cities from 2020 onward, using stations average.

## Part 1b
- Refer to ScrapeCPCB.py and PlotCPCB.ipynb
- In order to collect the data from the CPCB website, I used Selenium with the Crhome webdriver. 
- First step was to fill the State and City info, in order to get the list of all the station names for each state (West Bengal & Kolkata).
- The solution then goes through filling the State, City, Station Name and more parameters like PM2.5 and setting the date as 01-01-2020 from the Calendar datepicker.
![Screenshot from 2022-06-27 18-44-55](https://user-images.githubusercontent.com/14858227/175950636-7b708477-6b7f-46bf-997f-4178b05647a5.png)




- It finds the 'Submit' button and then the web browser is prompted to a webpage where the data is visible and ready to be export to an Excel file which is saved in the data directory of the solution.



![Screenshot from 2022-06-27 18-47-01](https://user-images.githubusercontent.com/14858227/175950921-0c71ca17-3c96-4965-924a-9c6ed0d99fe8.png)


-There are a lot of 'None' values in the data collated from CPCB. For calculating the rolling averages, solution keeps a counter which gets reduced by 1 each time a 'None' is detected in the dataframes' PM2.5 value. It also resetting the 'None' PM2.5 value to be 0 afterwards. Finally adding the PM2.5 values and the counter to later find accurate averages.

- The PlotCPCB.ipynb has the relevant functions for the above logic as well as rolling average plots generated. Plotly was used for generating interactive plots and the same is saved as HTML(MovingAvgsLucknowKolkata.html).


## Part 2
- For the purposes of scraping and collecting data, I found Selenium to be more useful than BeautfulSoup for this particular problem statement.
- Currently the data is being stored in .xlsx files but can easily be migrated to SQL or NOSQL (MongoDB) databases. Cloud Storage platforms like Google Big Query and Amazon Redshift can also be used. We can also operate DB operations on the data (handle missing values,store counts) for reducing the preprocessing steps involved.
- Kafka Queues can be very helpful for serving a multitude of requests.
- For generating the plots, Plotly can generate decent looking interactive plots which can be saved or shared and embedded to a website using Django/Flask/FastAPI.
