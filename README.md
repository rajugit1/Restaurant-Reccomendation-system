# Restaurant-Reccomendation-system
Restaurant Recommendation system

Restaurant Recommender AI: Create a chatbot that helps users find the perfect restaurant for any occasion. It can consider factors like cuisine preferences, dietary restrictions, location, and user reviews to make tailored recommendations.


Data Source : https://www.kaggle.com/datasets/himanshupoddar/zomato-bangalore-restaurants



The provided code integrates various technologies and techniques to create a restaurant recommendation system using Python, pandas for data manipulation, regular expressions for text parsing, OpenAI's GPT-3.5 model for natural language understanding, and JSON for data format conversion. Below is a section-wise explanation for documentation purposes:

Data Loading and Preprocessing
Data Loading: The dataset is loaded from a CSV file containing restaurant data. It's crucial to ensure the path ('Downloads/zomato.csv') is correct and accessible.

Duplicate Removal: Duplicates are removed based on unique combinations of name, address, and cuisines to ensure each restaurant is listed only once.

Rate Conversion: The rate column, which may contain string values like '4.1/5', is converted to a numeric value for easier comparison and filtering. Missing or malformed rates are filled with the column's mean rate.
Cost Conversion: The approx_cost(for two people) column is cleaned by removing commas and converting the string values to numeric for straightforward cost analysis.

Reviews List Parsing
A custom parse_reviews function attempts to convert the reviews_list column from a string representation of lists to actual list objects, extracting and returning the first review text as a sample. If conversion fails, it returns "No reviews available".

OpenAI GPT-3.5 Integration
API Key Security: The OpenAI API key is set from an environment variable for security. However, the key is directly included in the provided code snippet, which is not recommended for public or shared code. Always use environment variables or secure means to handle sensitive keys.
Chat Model Completions: Utilizes OpenAI's GPT-3.5 turbo model to process user queries, interpreting the natural language to understand the user's intent regarding cuisine type, location, and desired rating.

Intent Parsing
Regular Expressions: The parse_intent function uses regular expressions to extract specific information (cuisine, location, and rating) from the user's query as interpreted by GPT-3.5, providing defaults if no matches are found.

Restaurant Recommendations
Filters the preprocessed dataset for restaurants matching the parsed criteria (cuisine type, location, minimum rating) and sorts the matches by rating to recommend the top 5.

Recommendations Formatting
Formatted Output: The format_recommendations function formats the filtered recommendations for presentation, including details like restaurant type, liked dishes, cost for two, and a sample review, enhancing the user's decision-making process.

Processing User Queries
Orchestrates the flow from receiving a natural language query, interpreting intent with GPT-3.5, filtering the dataset based on this intent, and formatting the recommendations for user presentation.
Example Usage

Demonstrates how to use the system with a sample query, showcasing the end-to-end process from query to recommendation.

Security Note
The direct inclusion of the OpenAI API key in the script is a significant security risk. Always use environment variables or secure vaults to handle such sensitive information. The provided key should be considered compromised and replaced immediately.

Improvement Suggestions
Error Handling: Improve error handling around OpenAI API interactions to gracefully manage failures or unexpected responses.

API Key Management: Remove the hardcoded API key from the script and ensure it's securely managed outside the codebase, ideally through environment variables or a configuration management system.
Data Validation: Add checks and validations around data conversions and parsing to handle edge cases or malformed data more robustly.
