# E-commerce Funnel Analysis

![Funnel Chart Example](funnel-chart-example.png) <!-- Replace with an actual screenshot of the Plotly funnel chart from the notebook -->

## Description
This project analyzes user event data from an e-commerce platform (likely sourced from Google Analytics or BigQuery) to visualize and understand the user journey through a conversion funnel. It uses Python libraries like Pandas, NumPy, Matplotlib, Seaborn, and Plotly to process the data, perform exploratory analysis, and generate interactive visualizations. The focus is on key events such as page views, engagements, item views, add-to-cart actions, checkouts, and purchases. The goal is to identify drop-off points, calculate conversion rates, and provide insights to optimize user experience, retention, and conversions.

## About the Project
### Project Summary
This Jupyter notebook (`funnel_analysis.ipynb`) conducts an exploratory data analysis (EDA) and funnel visualization on a sample JSON dataset (`bq-results-sample.json`) containing 26,489 user events from a single day (January 31, 2021). The analysis reveals user behavior patterns, funnel progression, and potential bottlenecks in the e-commerce journey.

Key steps in the notebook:
- Import necessary libraries (Pandas, NumPy, Matplotlib, Seaborn, Plotly).
- Load and explore the dataset (display head, info, describe, shape).
- Calculate event frequencies.
- Define a multi-stage funnel and visualize it with a bar chart (Matplotlib) and an interactive funnel chart (Plotly).
- Note: The notebook includes a comment about converting `event_date` to datetime for time-based analysis, but it's not implemented.

### Technologies Used
- **Python Version**: 3.13.5 (per notebook metadata).
- **Libraries**: 
  - Data Manipulation: Pandas, NumPy.
  - Visualization: Matplotlib, Seaborn (static plots), Plotly (interactive funnel).
- **Data Source**: Sample JSON file from BigQuery export, simulating e-commerce event logs.
- **Environment**: Jupyter Notebook.

Below is the complete README content formatted in Markdown for GitHub, incorporating a detailed analysis and report based on the funnel_analysis.ipynb notebook. The content includes the project description, installation and usage instructions, a comprehensive analysis with insights, recommendations, limitations, and all relevant details, structured for clarity and compatibility with GitHub's Markdown rendering.
markdown# E-commerce Funnel Analysis

![Funnel Chart Example](funnel-chart-example.png) <!-- Replace with an actual screenshot of the Plotly funnel chart from the notebook -->

## Description
This project analyzes user event data from an e-commerce platform (likely sourced from Google Analytics or BigQuery) to visualize and understand the user journey through a conversion funnel. It uses Python libraries like Pandas, NumPy, Matplotlib, Seaborn, and Plotly to process the data, perform exploratory analysis, and generate interactive visualizations. The focus is on key events such as page views, engagements, item views, add-to-cart actions, checkouts, and purchases. The goal is to identify drop-off points, calculate conversion rates, and provide insights to optimize user experience, retention, and conversions.

## About the Project
### Project Summary
This Jupyter notebook (`funnel_analysis.ipynb`) conducts an exploratory data analysis (EDA) and funnel visualization on a sample JSON dataset (`bq-results-sample.json`) containing 26,489 user events from a single day (January 31, 2021). The analysis reveals user behavior patterns, funnel progression, and potential bottlenecks in the e-commerce journey.

Key steps in the notebook:
- Import necessary libraries (Pandas, NumPy, Matplotlib, Seaborn, Plotly).
- Load and explore the dataset (display head, info, describe, shape).
- Calculate event frequencies.
- Define a multi-stage funnel and visualize it with a bar chart (Matplotlib) and an interactive funnel chart (Plotly).
- Note: The notebook includes a comment about converting `event_date` to datetime for time-based analysis, but it's not implemented.

### Technologies Used
- **Python Version**: 3.13.5 (per notebook metadata).
- **Libraries**:
  - **Data Manipulation**: Pandas, NumPy.
  - **Visualization**: Matplotlib, Seaborn (static plots), Plotly (interactive funnel).
- **Data Source**: Sample JSON file from BigQuery export, simulating e-commerce event logs.
- **Environment**: Jupyter Notebook.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/ecommerce-funnel-analysis.git
   cd ecommerce-funnel-analysis

Install dependencies (create a requirements.txt with the following):
textpandas
numpy
matplotlib
seaborn
plotly
Then run:
bashpip install -r requirements.txt

Download or provide the sample data file bq-results-sample.json in the project root (as referenced in the notebook).

Usage

Launch Jupyter Notebook:
bashjupyter notebook

Open funnel_analysis.ipynb and run cells sequentially:

Cells 1-2: Import libraries and load/display data.
Cell 4: Data exploration (head, info, describe, shape).
Cell null (event_counts): Calculate and display event frequencies.
Cell 6: Comment on date conversion (not implemented).
Cell null (bar chart): Visualize a subset funnel with Matplotlib.
Cell 10-11: Prepare data and create interactive Plotly funnel chart.


Customize: Modify funnel_events or funnel_data for different funnel stages.

Analysis and Report
Dataset Overview

Size: 26,489 rows (events), 17 columns.
Columns and Types:

Numerical: event_date (int64), event_timestamp (int64), event_bundle_sequence_id (int64), user_pseudo_id (float64), user_first_touch_timestamp (float64), stream_id (int64).
Categorical/Object: event_name, event_params, privacy_info, user_properties, user_ltv, device, geo, traffic_source, platform, ecommerce, items.


Statistics (from df.describe()):

event_date: All 20210131 (single-day snapshot).
event_timestamp: Mean ~1.612095e+15 (Unix microseconds), range from 1.612051e+15 to 1.612138e+15.
user_pseudo_id: Mean ~3.071288e+08, up to 9.100857e+09 (anonymized user IDs).
Missing Values: 958 (~3.6%) in user_first_touch_timestamp.


Other Observations:

Platform: Exclusively "WEB".
Traffic: Primarily organic (traffic_source.medium = 'organic').
Geo: Mostly Americas/Northern America (sample shows US-like data).
Device: Mobile category dominant (e.g., Android brands).
No time-series trends due to single-date data.



Event Frequency Analysis
Event counts (from df['event_name'].value_counts()):


























































































Event NameCountPercentagepage_view949835.9%user_engagement500518.9%scroll287010.8%session_start276010.4%first_visit21278.0%view_item18296.9%view_promotion11904.5%add_to_cart2951.1%select_item2370.9%begin_checkout2340.9%view_search_results1980.7%add_shipping_info1000.4%select_promotion710.3%add_payment_info530.2%purchase190.07%click30.01%

Interpretation: High early-stage events (e.g., page_view, user_engagement) indicate strong initial traffic. Low conversion events (e.g., purchase) suggest significant drop-offs.

Funnel Analysis
Defined funnel stages: page_view → user_engagement → scroll → session_start → first_visit → view_item → view_promotion → add_to_cart → select_item → begin_checkout → view_search_results → add_shipping_info → select_promotion → add_payment_info → purchase.

Funnel Counts and Drop-off Percentages (relative to page_view = 100%):





































































































StageCount% of InitialDrop-off from Previouspage_view9498100.0%-user_engagement500552.7%47.3%scroll287030.2%42.7%session_start276029.1%3.8%first_visit212722.4%22.9%view_item182919.3%14.0%view_promotion119012.5%34.9%add_to_cart2953.1%75.2%select_item2372.5%19.7%begin_checkout2342.5%1.3%view_search_results1982.1%15.4%add_shipping_info1001.1%49.5%select_promotion710.7%29.0%add_payment_info530.6%25.4%purchase190.2%64.2%

Visualizations:

Matplotlib Bar Chart: Displays counts for a subset of events (page_view, view_item, add_to_cart, begin_checkout, purchase) to highlight conversion drop-offs.
Plotly Interactive Funnel: Shows all stages with counts, percentages, and text labels (e.g., "9498 (100.0%)" for page_view). Labels are blank for lower stages (select_promotion, add_payment_info, purchase) in the code, but percentages are calculated.


Overall Conversion Rate: 0.2% (19 purchases / 9,498 page views), indicating a low end-to-end conversion rate.

Key Insights

Strong Top-of-Funnel:

High volumes in awareness and engagement stages (page_view at 100%, user_engagement at 52.7%) suggest effective traffic acquisition, likely driven by organic sources.


Major Drop-offs:

Browsing to Cart (view_item 19.3% → add_to_cart 3.1%): 84% drop-off; users view items but rarely add them to the cart, possibly due to unappealing product details, pricing, or UI friction.
Cart to Checkout (add_to_cart 3.1% → begin_checkout 2.5%): Minor 19.4% drop-off, but indicates cart abandonment issues.
Checkout to Purchase (begin_checkout 2.5% → purchase 0.2%): ~92% drop-off across checkout stages, with significant losses at add_shipping_info (49.5%) and purchase (64.2%). Potential causes include complex forms, payment failures, or lack of trust.


Promotion and Search Impact:

view_promotion (12.5%) and view_search_results (2.1%) show moderate engagement, but low follow-through to cart, suggesting ineffective promotions or search functionality.


User Acquisition:

first_visit (22.4%) indicates a significant portion of new users, but low conversion suggests retention challenges.


Event Patterns:

scroll (30.2%) and user_engagement (52.7%) indicate moderate session depth, but this doesn't translate to conversion actions.



Recommendations

Optimize Product Pages:

A/B test product descriptions, images, pricing, and add-to-cart button placement to reduce the 84% drop-off from view_item to add_to_cart.


Streamline Checkout Process:

Simplify shipping and payment forms, offer guest checkout, and integrate trusted payment gateways to address the ~92% drop-off in checkout stages.


Enhance Promotions and Search:

Improve visibility of promotions and relevance of search results to boost mid-funnel engagement (view_promotion, view_search_results).


Segmentation Analysis:

Extend the notebook to segment data by device.category, geo, or traffic_source for targeted insights (e.g., mobile vs. desktop conversion rates).


Time-Series Analysis:

Implement event_date conversion to datetime and analyze multi-day data for trends, cohort retention, or seasonal patterns.


User-Level Funnel Tracking:

Use user_pseudo_id to compute per-user funnels, ensuring accurate conversion paths without overcounting events.


A/B Testing:

Test UI/UX changes at identified drop-off points (e.g., cart, checkout) to measure impact on conversions.


Data Enrichment:

Extract nested fields (e.g., event_params for page locations, items for product IDs) to analyze specific pages or products driving conversions.



Limitations

Single-Day Snapshot:

Data is limited to January 31, 2021, preventing analysis of temporal trends or retention.


Event-Based Analysis:

Funnel is based on aggregate event counts, not individual user journeys, which may overestimate or misrepresent conversions.


No Segmentation:

Lacks breakdowns by user attributes (e.g., device, location), limiting granular insights.


Missing Data:

958 nulls in user_first_touch_timestamp; nested columns like event_params and items are not fully unpacked.



