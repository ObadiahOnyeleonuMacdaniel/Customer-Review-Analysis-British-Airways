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

For collecting data from the site using Python and BeautifulSoup, I used the code below;
       
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
- Step 3 : Preprocessing the data
The content of the data set is given below:

![Head BA](https://github.com/ObadiahOnyeleonuMacdaniel/Customer-Review-Analysis-British-Airways/assets/156518788/a98d7d5b-22fa-4dbc-b6aa-93c1597f4ab3)




- Step 4 : Exploratory Data Analysis
- Step 5 : Data Visualization

        
A pie chart visual was used to represent review of the customers.
![PieChart BA](https://github.com/ObadiahOnyeleonuMacdaniel/Customer-Review-Analysis-British-Airways/assets/156518788/44ce9870-5ba1-4d4b-9603-aa09249223ed)



 
 A BarChart visual was used to represent this perecntage also.
![Barchart BA](https://github.com/ObadiahOnyeleonuMacdaniel/Customer-Review-Analysis-British-Airways/assets/156518788/d4377ad6-12e6-452c-934c-6cec5157e7ab)

 

### Following inferences can be drawn from the dashboard;
Out of 1000 reviews, almost 38.4% were positive, around 15.6%  were negative and approximately 46% were neutral. 
This means the majority of reviews were polarised as either positive or negative.
Although the number of Positive review customers (almost 38.4%) are more than dissatisfied customers with a negative review (around 15.6%). 
Howbeit, since number of neutral customers (almost 46%) are more than satisfied customers (around 38.4%), thus in all they must work on improving their service. 


## Insights & Recommendations
Based on the distribution of sentiment reviews for the airline company (38.4% positive, 46% neutral, and 17% negative), here are potential insights and recommendations:

### Insights:
1. **Neutral Dominance**: The majority of reviews (46%) are neutral. This suggests that customers may have mixed feelings or are indifferent about their experiences with the airline.
   
2. **Positive Reviews**: Positive reviews account for 38.4% of the total. While positive sentiment is significant, it indicates that there is room for improvement to increase customer satisfaction further.

3. **Negative Reviews**: Negative reviews constitute 17% of the total. Although relatively lower, negative feedback highlights areas where the airline is falling short and needs immediate attention.

### Recommendations:
1. **Enhance Customer Engagement**:
   - Actively solicit feedback from neutral customers to understand their concerns and preferences better.
   - Encourage more positive reviews by incentivizing satisfied customers to share their experiences.

2. **Address Negative Feedback Promptly**:
   - Identify recurring issues mentioned in negative reviews (e.g., flight delays, customer service issues) and prioritize corrective actions.
   - Implement a robust customer service strategy to resolve complaints efficiently and improve overall customer experience.

3. **Improve Communication and Transparency**:
   - Communicate updates and changes effectively to manage customer expectations.
   - Provide transparent information about policies, schedules, and services to reduce uncertainty and confusion among customers.

4. **Continuous Quality Improvement**:
   - Regularly analyze sentiment trends to detect emerging issues and proactively address them.
   - Invest in training programs for staff to ensure consistent and high-quality service delivery.

5. **Monitor Competitor Insights**:
   - Benchmark against competitors to identify best practices and areas for differentiation.
   - Incorporate successful strategies from competitors to enhance customer satisfaction and loyalty.

6. **Utilize Sentiment Analysis Tools**:
   - Implement advanced sentiment analysis tools to automate and streamline the analysis of customer feedback.
   - Leverage insights from sentiment analysis to make data-driven decisions and tailor strategies for improving customer sentiment.

By focusing on these recommendations based on the sentiment distribution, the airline company can strive towards improving overall customer satisfaction, loyalty, and operational efficiency. Regular monitoring and adaptation of strategies based on customer feedback will be crucial in maintaining competitive advantage and enhancing brand reputation.






        
