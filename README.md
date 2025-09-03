# Applied-Data-Science-Capstone-Project

Of course. [cite_start]Here is a detailed summary of the data science project presentation titled "Winning Space Race with Data Science"[cite: 2].

### **Project Overview**

This presentation, outlines a data science project aimed at predicting the successful landing of a SpaceX Falcon 9 rocket's first stage. The project's business context is rooted in launch cost determination; SpaceX advertises Falcon 9 launches for $62 million, significantly lower than competitors' costs of over $165 million, largely due to the reusability of the first stage. By predicting if the first stage will land successfully, one can better estimate the actual cost of a launch, which is valuable information for companies bidding against SpaceX.

### **Project Goal and Key Questions**

* The primary goal is to build a machine learning pipeline to predict the success of a first-stage landing. The project seeks to answer the following questions:
* What are the key factors that determine if a rocket will land successfully? 
* How do various features interact to influence the success rate? 
* What operational conditions are necessary to ensure a successful landing program? 


### **Methodology**

The project followed a comprehensive data science methodology, from data collection to predictive modeling.

#### **1. Data Collection**
The dataset was compiled from two primary sources:
* **SpaceX API:** Data was programmatically collected using a GET request to the SpaceX API[cite: 46, 56]. [cite_start]The JSON response was then decoded and converted into a pandas DataFrame using the `.json()` and `.json_normalize()` methods, respectively[cite: 57].
* [cite_start]**Web Scraping:** Historical Falcon 9 launch records were scraped from a Wikipedia HTML table using the BeautifulSoup library[cite: 46, 59]. [cite_start]The objective was to parse this table and convert it into a pandas DataFrame for analysis[cite: 60].

#### **2. Data Wrangling and Preprocessing**
* [cite_start]The collected data was cleaned, and missing values were identified and filled where necessary[cite: 18, 58].
* [cite_start]Categorical features were transformed using one-hot encoding to prepare them for machine learning models[cite: 48].
* [cite_start]A binary classification label for landing outcomes (`Class` 0 for failure, 1 for success) was created from the 'Outcome' column[cite: 142, 200].

#### **3. Exploratory Data Analysis (EDA)**
[cite_start]EDA was conducted using both SQL and data visualization techniques[cite: 19, 20].
* [cite_start]**SQL Analysis:** The dataset was loaded into a PostgreSQL database[cite: 186]. [cite_start]SQL queries were executed to extract insights, such as identifying unique launch sites, calculating total payload mass for NASA (CRS) missions, and finding the average payload for specific booster versions[cite: 187, 189, 190, 191].
* [cite_start]**Data Visualization:** Various plots were created to visualize relationships between key features, including launch success trends over the years and the success rates for different orbit types[cite: 156, 173, 157].

#### **4. Interactive Visual Analytics**
* [cite_start]**Folium:** Interactive maps were built to visualize all launch sites[cite: 199]. [cite_start]Color-coded markers were used to distinguish between successful (green) and failed (red) launches at each site, helping to identify sites with higher success rates[cite: 201, 494]. [cite_start]The maps were also used to analyze the proximity of launch sites to landmarks like coastlines, highways, railways, and cities[cite: 202].
* [cite_start]**Plotly Dash:** An interactive dashboard was created featuring pie charts to show the total successful launches by site and scatter plots to explore the relationship between payload mass and launch outcome[cite: 207, 208, 209].

#### **5. Predictive Analysis**
* [cite_start]A classification pipeline was built to predict landing success[cite: 214].
* [cite_start]The data was split into training and testing sets[cite: 215].
* [cite_start]Several machine learning models were built, and their hyperparameters were tuned using `GridSearchCV`[cite: 216].
* [cite_start]Model performance was evaluated based on classification accuracy to identify the best-performing algorithm[cite: 217, 218].

### **Results and Findings**

#### **Exploratory Data Analysis Insights**
* [cite_start]**Launch Site vs. Success:** A higher number of flights at a specific launch site correlates with a greater success rate[cite: 230]. [cite_start]For the CCAFS SLC 40 site, a greater payload mass was also associated with a higher success rate[cite: 242].
* [cite_start]**Orbit vs. Success:** The orbits ES-L1, GEO, HEO, SSO, and VLEO demonstrated the highest success rates[cite: 247]. [cite_start]With heavy payloads, successful landings were more frequent for PO, LEO, and ISS orbits[cite: 285].
* [cite_start]**Yearly Trend:** The launch success rate showed a consistent increasing trend from 2013 through 2020[cite: 308, 310].
* **SQL Findings:**
    * [cite_start]The total payload mass carried by boosters for NASA (CRS) was 45,596 kg[cite: 350, 360].
    * [cite_start]The average payload mass for the F9 v1.1 booster version was 2,928.4 kg[cite: 363, 374].
    * [cite_start]The first successful ground pad landing occurred on December 22, 2015[cite: 377, 386].

#### **Interactive Analytics Insights**
* [cite_start]**Launch Site Locations:** All SpaceX launch sites are located on the coasts of the United States in Florida and California[cite: 485].
* [cite_start]**Proximity Analysis:** Launch sites are situated close to coastlines but are intentionally kept at a distance from major cities, highways, and railways[cite: 538, 539, 540, 541].
* **Dashboard Insights:**
    * [cite_start]The KSC LC-39A launch site has the highest number of successful launches[cite: 553]. [cite_start]It has a success rate of 76.9%[cite: 558].
    * [cite_start]Launches with low-weighted payloads (0 kg - 4000 kg) have a higher success rate compared to those with heavy-weighted payloads (4000 kg - 10,000 kg)[cite: 593].

#### **Predictive Analysis Results**
* [cite_start]**Best Model:** The Decision Tree classifier was identified as the best-performing model, achieving an accuracy score of **0.873**[cite: 598, 613].
* [cite_start]**Confusion Matrix:** The model was generally effective at distinguishing between classes[cite: 617]. [cite_start]However, its primary weakness was a tendency for false positives, meaning it sometimes classified an unsuccessful landing as successful[cite: 618].

### **Conclusion**

[cite_start]The project successfully built a data science pipeline to analyze and predict SpaceX's first-stage landing success[cite: 34]. The key conclusions drawn from the analysis are:
* [cite_start]Launch success rate improves with a higher flight count at a given site and has been increasing yearly since 2013[cite: 641, 642].
* [cite_start]The KSC LC-39A site is the most successful launch location[cite: 644].
* [cite_start]Certain orbits (ES-L1, GEO, HEO, SSO, VLEO) have higher success rates[cite: 643].
* [cite_start]The Decision Tree classifier is the most effective machine learning model for this prediction task[cite: 645].
