# Applied-Data-Science-Capstone-Project


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
* **SpaceX API:** Data was programmatically collected using a GET request to the SpaceX API. The JSON response was then decoded and converted into a pandas DataFrame using the `.json()` and `.json_normalize()` methods, respectively.
* **Web Scraping:** Historical Falcon 9 launch records were scraped from a Wikipedia HTML table using the BeautifulSoup library .The objective was to parse this table and convert it into a pandas DataFrame for analysis.

#### **2. Data Wrangling and Preprocessing**
* The collected data was cleaned, and missing values were identified and filled where necessary.
* Categorical features were transformed using one-hot encoding to prepare them for machine learning models.
*]A binary classification label for landing outcomes (`Class` 0 for failure, 1 for success) was created from the 'Outcome' column.

#### **3. Exploratory Data Analysis (EDA)**
EDA was conducted using both SQL and data visualization techniques.
* **SQL Analysis:** The dataset was loaded into a PostgreSQL database .SQL queries were executed to extract insights, such as identifying unique launch sites, calculating total payload mass for NASA (CRS) missions, and finding the average payload for specific booster versions.
* **Data Visualization:** Various plots were created to visualize relationships between key features, including launch success trends over the years and the success rates for different orbit types.

#### **4. Interactive Visual Analytics**
* **Folium:** Interactive maps were built to visualize all launch sites. Color-coded markers were used to distinguish between successful (green) and failed (red) launches at each site, helping to identify sites with higher success rates .The maps were also used to analyze the proximity of launch sites to landmarks like coastlines, highways, railways, and cities.
* **Plotly Dash:** An interactive dashboard was created featuring pie charts to show the total successful launches by site and scatter plots to explore the relationship between payload mass and launch outcome

#### **5. Predictive Analysis**
* A classification pipeline was built to predict landing success.
* The data was split into training and testing sets.
* Several machine learning models were built, and their hyperparameters were tuned using `GridSearchCV`.
* Model performance was evaluated based on classification accuracy to identify the best-performing algorithm.

### **Results and Findings**

#### **Exploratory Data Analysis Insights**
* **Launch Site vs. Success:** A higher number of flights at a specific launch site correlates with a greater success rate . For the CCAFS SLC 40 site, a greater payload mass was also associated with a higher success rate.
* **Orbit vs. Success:** The orbits ES-L1, GEO, HEO, SSO, and VLEO demonstrated the highest success rates. With heavy payloads, successful landings were more frequent for PO, LEO, and ISS orbits.
* **Yearly Trend:** The launch success rate showed a consistent increasing trend from 2013 through 2020.
* **SQL Findings:**
    * The total payload mass carried by boosters for NASA (CRS) was 45,596 kg.
    * The average payload mass for the F9 v1.1 booster version was 2,928.4 kg.
    * The first successful ground pad landing occurred on December 22, 2015.

#### **Interactive Analytics Insights**
* **Launch Site Locations:** All SpaceX launch sites are located on the coasts of the United States in Florida and California.
* **Proximity Analysis:** Launch sites are situated close to coastlines but are intentionally kept at a distance from major cities, highways, and railways.
* **Dashboard Insights:**
    * The KSC LC-39A launch site has the highest number of successful launches. It has a success rate of 76.9%.
    * Launches with low-weighted payloads (0 kg - 4000 kg) have a higher success rate compared to those with heavy-weighted payloads (4000 kg - 10,000 kg).

#### **Predictive Analysis Results**
* **Best Model:** The Decision Tree classifier was identified as the best-performing model, achieving an accuracy score of **0.873**.
* **Confusion Matrix:** The model was generally effective at distinguishing between classes .However, its primary weakness was a tendency for false positives, meaning it sometimes classified an unsuccessful landing as successful.

### **Conclusion**

The project successfully built a data science pipeline to analyze and predict SpaceX's first-stage landing success. The key conclusions drawn from the analysis are:
* Launch success rate improves with a higher flight count at a given site and has been increasing yearly since 2013.
* The KSC LC-39A site is the most successful launch location.
* Certain orbits (ES-L1, GEO, HEO, SSO, VLEO) have higher success rates.
* The Decision Tree classifier is the most effective machine learning model for this prediction task.
