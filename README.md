# Customer-Review-Analysis (British-Airways)
### A simulation job focusing on how data science is a critical component of British Airways Success


### Dataset Link : [https://www.airlinequality.com/airline-reviews/british-airways]
If you navigate to this link: [https://www.airlinequality.com/airline-reviews/british-airways] you will see the data used for this analysis. 

Now, we can use Python and BeautifulSoup to collect all the links to the reviews and then to collect the text data on each of the individual review links
## Problem Statement

This review analysis helps the airlines understand their customers better. It helps the airlines know if their customers are satisfied with their services. 

Through different ratings, they get to know their improvement area, & thus they can improve their services by identifying these area. It also lets them know the average delay & departure time, thus since by using this dashboard they have identified this problem, they can further work on factors responsible for these unwanted delays.

Since, number of neutral/dissatisfied customers (almost 57 %) are more than satisfied customers (around 43 %), thus in all they must work on improving their services. 

Also since average delay in arrival & departure both is 15 minutes, thus they must try to reduce it.


### Steps followed 

- Step 1 : Web scraping and analysis. I used a package called BeautifulSoup to collect the data from the web. Once I've collected the data and saved it into a local .csv file, I started with my analysis.

For collecting data from the site using Python and BeautifulSoup,the expression was written as;
       
        import requests
        from bs4 import BeautifulSoup
        import pandas as pd"

        base_url = "https://www.airlinequality.com/airline-reviews/british-airways"
        pages = 10
        page_size = 100

        reviews = []

        # for i in range(1, pages + 1):
        for i in range(1, pages + 1):
            print(f"Scraping page {i}")
            # Create URL to collect links from paginated data
            url = f"{base_url}/page/{i}/?sortby=post_date%3ADesc&pagesize={page_size}"
            # Collect HTML data from this page
            response = requests.get(url)
            
            # Parse content
            content = response.content
            parsed_content = BeautifulSoup(content, 'html.parser')
            for para in parsed_content.find_all("div", {"class": "text_content"}):
                reviews.append(para.get_text())
            print(f"   ---> {len(reviews)} total reviews")
            
- Step 2 : Load the csv dataset into my notebook as a pandas Dataframe

The content of the data set is given below:

![Head BA](https://github.com/ObadiahOnyeleonuMacdaniel/Customer-Review-Analysis-British-Airways/assets/156518788/a98d7d5b-22fa-4dbc-b6aa-93c1597f4ab3)


- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present except column named "Arrival Delay".
- Step 5 : For calculating average delay time, null values were not taken into account as only less than 1% values are null in this column(i.e column named "Arrival Delay") 

  

        
A pie chart visual was used to represent review of the customers.

![PieChart BA](https://github.com/ObadiahOnyeleonuMacdaniel/Customer-Review-Analysis-British-Airways/assets/156518788/44ce9870-5ba1-4d4b-9603-aa09249223ed)



 
 A card visual was used to represent this perecntage.
 
 Snap of % of customers who preferred business class
 
 ![Snap_Percentage](https://user-images.githubusercontent.com/102996550/174090653-da02feb4-4775-4a95-affb-a211ca985d07.jpg)

 
 - Step 17 : New measure was created to calculate total distance travelled by flights & a card visual was used to represent total distance.
 
 Following DAX expression was written to find total distance,
 
         Total Distance Travelled = SUM(airline_passenger_satisfaction[Flight Distance])
    
 A card visual was used to represent this total distance.
 
 
 ![Snap_3](https://user-images.githubusercontent.com/102996550/174091618-bf770d6c-34c6-44d4-9f5e-49583a6d5f68.jpg)
 
 - Step 18 : The report was then published to Power BI Service.
 
 
![Publish_Message](https://user-images.githubusercontent.com/102996550/174094520-3a845196-97e6-4d44-8760-34a64abc3e77.jpg)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://user-images.githubusercontent.com/102996550/174096257-11f1aae5-203d-44fc-bfca-25d37faf3237.jpg)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload](https://user-images.githubusercontent.com/102996550/174074051-4f08287a-0568-4fdf-8ac9-6762e0d8fa94.jpg)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Customers = 129880

   Number of satisfied Customers (Male) = 28159 (21.68 %)

   Number of satisfied Customers (Female) = 28269 (21.76 %)

   Number of neutral/unsatisfied customers (Male) = 35822 (27.58 %)

   Number of neutral/unsatisfied customers (Female) = 37630 (28.97 %)


           thus, higher number of customers are neutral/unsatisfied.
           
### [2] Average Ratings

    a) Baggage Handling - 3.63/5
    b) Check-in Service - 3.31/5
    c) Cleanliness - 3.29/5
    d) Ease of online booking - 2.88/5
    e) Food & Drink - 3.21/5
    f) In-flight Entertainment - 3.36/5
    g) In-flight service - 3.64/5
    h) In-flight Wifi service - 2.81/5
    i) Leg room service - 3.37/5
    j) On-board service - 3.38/5
    k) Online boarding - 3.33/5
    l) Seat comfort - 3.44/5
    m) Departure & arrival convenience - 3.22/5
  
  while calculating average rating, null values have been ignored as they were not relevant for some customers. 
  
  These ratings will change if different visual filters will be applied.  
  
  ### [3] Average Delay 
  
      a) Average delay in arrival(minutes) - 15.09
      b) Average delay in departure(minutes) - 14.71
Average delay will change if different visual filters will be applied.

 ### [4] Some other insights
 
 ### Class
 
 1.1) 47.87 % customers travelled by Business class.
 
 1.2) 44.89 % customers travelled by Economy class.
 
 1.3) 7.25 % customers travelled by Economy plus class.
 
         thus, maximum customers travelled by Business class.
 
 ### Age Group
 
 2.1)  21.69 % customers belong to '0-25' age group.
 
 2.2)  52.44 % customers belong to '25-50' age group.
 
 2.3)  25.57 % customers belong to '50-75' age group.
 
 2.4)  0.31 % customers belong to '75-100' age group.
 
         thus, maximum customers belong to '25-50' age group.
         
### Customer Type

3.1) 18.31 % customers have customer type 'First time'.

3.2) 81.69 % customers have customer type 'returning'.
       
       thus, more customers have customer type 'returning'.

### Type of travel

4.1) 69.06 % customers have travel type 'Business'.

4.2) 30.94 % customers have travel type 'Personal'.

        thus, more customers have travel type 'Business'.

