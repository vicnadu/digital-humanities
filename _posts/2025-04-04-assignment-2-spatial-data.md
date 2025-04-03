---
title: "Assignment 2 - Spatial Data"
tags:
  - Assignments
  - Kepler
  - CSV
  - AI
---

# Introduction

The Zanzibar Gazette is a colonial-era newspaper that offers an invaluable record of the region’s imports and exports, legal notices, and administrative announcements. For this assignment, I chose a large table of imports into Zanzibar in January 1916, partly because I wanted a rich dataset that would demonstrate both the potential and the challenges of using generative AI tools for large-scale data extraction. The following essay details the rationale behind this choice, the difficulties encountered in transferring the data into CSV format with AI tools, the subsequent steps taken to visualize the data spatially on Kepler.gl, and my reflections regarding the process.

# Thick Mapping: Context and Relevance

One of the guiding concepts of this project is “thick mapping,” a method that combines multiple location-based datasets to highlight the geographical aspects of historical events. In the context of Zanzibar’s colonial history, thick mapping can help us see how trade routes, imported commodities, and cultural interactions were geographically dispersed or concentrated. If we imagine eventually adding layers for exports, shipping routes, or demographic data, we could start building a detailed picture of Zanzibar’s global connections during the British colonial period.

The 1916 Zanzibar Gazette data was a starting point for that bigger goal. Although I ended up focusing on a single month’s (January 1916) import table, the intention was to compare it with a September 1916 table and possibly others. This approach would have allowed an even richer comparative view of fluctuations in types of merchandise, prices, and geographic origins over time. However, due to AI data extraction limitations, it made more sense to focus on just one table for this assignment.

# The Source and Its Data

The source material for this assignment was the 1916 edition of the Zanzibar Gazette, specifically a tabular statement of imports in January of 1916. This table is extensive, listing over a 100 commodities, from arms and ammunition to everyday grocery items, along with their weight, quantities, values, and points of origin. Some of the key attributes in the table include:

- **Merchandise Name:** A wide variety, such as Ambergris, Ammunition, Arms fire, Beer, Coconuts, GRAIN-Millet, and many more.
- **Region and SubRegion:** Geographic origins like Europe (United Kingdom, Continent), Asia (India, Other Countries), Africa, America, etc.
- **Weight, Packages, Value:** Numerical data points indicating how much was imported, how it was packaged, and its monetary value.
- **Latitude and Longitude:** AI-generated coordinates to facilitate geospatial visualization in Kepler.gl.

In the Zanzibar Gazette, these data were presented in textual or tabular format without any geospatial metadata. Therefore, one of the tasks was to implement the dataset with latitude and longitude columns so that each import’s region of origin could be visualized on a world map.

# Part 1: Transferring the Data into a CSV File

## Initial Approach

Initially, my plan was to handle two large tables from the Zanzibar Gazette: one from January 1916 and another from September 1916. I intended to merge the two tables and to generate a single CSV file that would allow me to compare the types of imported goods, their values, and any price fluctuations between the two dates. This approach seemed promising for a more robust analysis, but it proved to be impractical as the AI models struggled to handle so much data.

The full CSV file is the following:
[View the CSV file on GitHub](https://github.com/vicnadu/digital-humanities/blob/master/assets/data/Perplexity_January_1916_Imports.csv)

## Challenges with Large-Scale AI Extraction

The main issue was the sheer volume of data from the import tables. Each table had over 100 rows, making it difficult for most AI models to accurately process and output a complete, properly formatted CSV. My initial attempts involved:

- **Uploading Screenshots:** I tried uploading screenshots of the PDF pages to various AI models as it was recommended in class.
- **Uploading PDF:** After some failed attempts with the screenshots, I realized that I could take advantage of the OCR (Optical character recognition) already present in the file and directly upload the specific page of the table from the PDF.

However, as I tried to process a large quantity of data from the tables, I encountered significant limitations with the following AI tools:

- **ChatGPT (Free Version):** Tended to produce tables with inaccurate data or broken formatting.
- **Gemini:** Generated decent formatting but omitted large chunks of data, rendering the CSV incomplete.
- **DeepSeek (Free Version):** Could not handle the full tables at all, only providing small snippets.
- **Perplexity Pro:** Did the best job in terms of generating efficient formatting and populating the data correctly in one table, but it severely struggled to populate accurate data when working with more than one table.

Given the consistent errors and omissions, I realized that I would need to spend a disproportionate amount of time cleaning and verifying any AI-generated CSV if I continued with the plan to merge January and September data. This would be counterproductive to the assignment’s intention, which was to leverage AI to automate most of the process, not to create more excessive manual labor. Ultimately, I decided to focus exclusively on the January table, which still provided a large amount of data, with more than 100 rows of merchandise and 6 columns of regions to work with.

## Final CSV Creation

After deciding to use only the January 1916 table, I was able to simplify my prompts and feed a more manageable dataset to Perplexity Pro. By reducing the scope to one table, the AI-generated CSV was near perfectly accurate, though it still required some manual corrections. Additionally, Perplexity also modified the structure of the table without any explicit prompts from my end, fitting the table into a better format for Kepler. The final CSV included:

- **Merchandise:** The name of the product.
- **Region:** Broad geographical categorization (e.g., Europe, Asia, Africa, America).
- **SubRegion:** More specific geographic detail (e.g., United Kingdom, Continent, India, Other Countries).
- **Weight, Packages, Value:** Numeric columns reflecting the quantity and cost.
- **Latitude, Longitude:** Coordinates for each region.

The incorporation of latitude and longitude was completely automated with Perplexity, which was easily verified for its accuracy on Kepler. For example, London (United Kingdom) was assigned approximately (51.5074, -0.1278), Paris (Continent, Europe) around (48.8566, 2.3522), India around (20.5937, 78.9629), and so forth.

# Part 2: Creating an Interactive Map in Kepler.gl

With the CSV file in hand, I moved on to Kepler.gl to visualize the data. Kepler.gl is a robust, browser-based geospatial analysis tool that can generate interactive maps with different layers and filters. Below are some key steps and findings:

- **Data Upload:** I uploaded the CSV directly into Kepler.gl. Immediately, the tool recognized the Latitude and Longitude columns and plotted the data points on the world map.
- **Layer Configuration:** I experimented with point layers and color scales. One interesting approach was to color-code each merchandise category by Value, which yielded a quick visual impression of which regions had higher-value imports. Another approach was to color-code by Packages to see where bulk items (like grain or groceries) originated.
- **Tooltips and Pop-ups:** By configuring the tooltips, I made it possible to see each data row’s details when hovering over a point on the map. This is crucial for a “thick mapping” approach, as it allows for immediate contextualization of each data point.
- **Clustering and Patterns:** The visualization showed clear concentrations of imports from India and Europe (particularly the United Kingdom and continental Europe). High-value items like Coins-Gold or Arms fire originated in Asia or Europe, whereas bulky, agricultural products such as Coconuts and Grain were predominantly from Africa and parts of Asia.

![Kepler.gl Data Visualization](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/zanzibar_kepler.gl.png)

An example of the Kepler.gl visualization (as shown above) revealed the distribution of imported goods, with color gradations to represent monetary value.

# Findings and Observations

Even with a single month’s data, several patterns could be noted:

- **Europe’s Dominance in High-Value Goods:** Items like Carriages and Ammunition were predominantly from the United Kingdom, suggesting strong colonial ties and a reliance on European industrial goods.
- **Asia’s Contribution in Agricultural and Household Goods:** India and “Other Countries” in Asia contributed a significant portion of groceries (e.g., Sugar, Tea, Ghee), as well as bulk commodities like Coconuts and Grain.
- **Africa’s Local and Regional Imports:** Some items, such as Charcoal, Bottles, and Live Stock (Cattle, Goats, Sheep), were traded regionally within Africa, indicating internal supply chains.
- **Geographical Dispersal of Imports:** The map highlights that, although a small island territory, Zanzibar had an extensive network of trade routes spanning four continents.

If we were to scale up and incorporate data from the September 1916 table (and potentially other months or years), we could look for seasonal patterns or shifts in trade alliances, possibly revealing how global events (such as World War I) impacted the flow of goods to and from Zanzibar.

# Reflection on the Automation Process

This assignment highlighted both the benefits and challenges of using AI for large-scale data extraction: Below are some reflections on that process:

- **Data Format Sensitivity:** AI tools often struggle with tabular data that exceed a certain size or complexity (100+ rows).
- **Prompt Engineering:** Iterative prompt engineering is essential. Asking for a “perfectly formatted CSV” does not guarantee that the AI will retain every row and column in the correct position. Adding step-by-step instructions, such as “Process the table in segments” or “Generate partial CSV outputs, then merge them” could possibly yield better results, though it requires testing.
- **Manual Verification:** Even when an AI-generated CSV appears correct, manual spot checks are crucial. Even the last version generated by Perplexity had some minor value errors.
- **Tool Limitations:** Each tool has its own constraints. While Perplexity Pro performed best overall, it still introduced errors when dealing with large amounts of data. This made me wonder how archivists and digital humanists are able to handle large datasets more efficiently with AI.

Below are examples of some prompts that I used in the mentioned AI models:

- **Prompt 1:**  
  "Here are images of one table from a historical newspaper in Zanzibar containing imports in 1916. Make me a perfectly formatted CSV file that corresponds to the table. This data will be used in services such as Kepler to create interactive maps/data visualization based on the table."

- **Prompt 2:**  
  "I need help doing a spatial data assignment. Below I will write the assignment description, which is divided into three parts. The first is transferring the data of the tables that I will give to you into two different perfectly formatted CSV files. The second is transferring that data into Kepler.gl, creating an interactive map/data visualization. The third is writing a 1500-word essay analyzing the process. I need your help with the first step (creating the CSV files). Before doing anything, wait for me to confirm that everything is uploaded first. I will upload one PDF file for table 1 (January), and one PDF file for table 2 (September). Therefore, you should create one formatted CSV file for table 1, and another formatted CSV file for table 2."

- **Prompt 3:**  
  "Use the following CSV code and implement latitude and longitude data for all regions in the table (for example, Europe, Asia, Africa). This will be used to visualize the data of the origin of imported goods in Zanzibar using Kepler.gl. Here is the CSV code:"

- **Prompt 4:**  
  "I need help doing a spatial data assignment. Below I will write the assignment description, which is divided into three parts. The first is transferring the data of one table into a CSV file. The second is transferring that data into Kepler.gl, creating an interactive map/data visualization. The third is writing a 1500-word essay analyzing the process. I need your help specifically with the first step (creating the CSV file). I will upload a PDF file for the table of imports to Zanzibar in January, as well as two screenshots of the same table in case that is better to use. Therefore, you should use the CSV text that I already have for the January table. However, you will include the latitude and longitude of all of the regions in the table (Europe, Asia, etc) while maintaining the same structure of the original table. Implement the latitude and longitude data in the most efficient way (for example, as additional columns). Remember that the purpose of this data will be to create a visualization of the origin of imports into Zanzibar in January 1916. Here is the CSV text that you need to modify:"

# Generative AI Research Reflections

As *Provocations from the Humanities for Generative AI Research* argues, AI-generated content is shaped by the biases of its training data and the assumptions embedded in its algorithms. This is particularly relevant when working with colonial-era documents like the 1910 Zanzibar Gazette, where the structure of the data itself reflects historical power dynamics. The way imports were recorded (what was categorized, emphasized, or left out) was possibly influenced by the British colonial administration’s economic priorities rather than the perspectives of Zanzibari traders or consumers.

By extracting and visualizing the Statement of Imports into Zanzibar in January 1916, we confront both the possibilities and the limitations of AI-driven research in digital humanities. The process of structuring the data (cleaning it, deciding how to represent it spatially) was not a neutral act. Instead, it required critical engagement with the Gazette’s colonial framework and an awareness of how AI processes might reinforce its biases. For example, while AI tools helped extract numerical and textual data efficiently, they struggled with inconsistencies in the original document’s formatting. These errors, if left unchecked, could distort the historical narrative, much like the British colonial records themselves often presented a one-sided view of Zanzibar’s economy.

Zanzibar’s position in the early 20th century as a key trading hub in the Indian Ocean world adds another layer of complexity to this analysis. The island was deeply embedded in global trade networks, with imports reflecting its economic entanglements with Britain, India, and the broader imperial economy. The visualization of this data, mapping trade routes and commodity flows, helps reveal these global connections. However, AI alone cannot capture the full significance of these relationships, it also requires human interpretation to contextualize any economic or political context.

Ultimately, this assignment demonstrates that while generative AI can be a powerful tool for digital humanities research, it should not be used uncritically. The extraction and visualization of historical data must be guided by an awareness of both the limitations of AI and the underlying structures of the historical records themselves. By applying these principles to the 1916 Zanzibar Gazette, it is possible to not only uncover patterns in colonial trade, but also to engage in a broader discussion about how digital tools shape our understanding of the past.

# If Expanded Further

Had I been able to successfully merge the January and September 1916 tables, a more detailed analysis would have been possible:

- **Price Comparisons:** Observing whether the value of certain goods increased or decreased over the span of several months, potentially correlating with historical events in 1916.
- **Seasonal or War-Related Trends:** Considering World War I’s impact on shipping routes, supply chains, and commodity availability.
- **Thick Mapping with Multiple Layers:** Integrating more data layers such as export figures, shipping news, or demographic data could yield a richer map.

Nonetheless, the single-month focus still provided a comprehensive view of Zanzibar’s import economy and the global connections that shaped it.

# Conclusion and Future Directions

This whole process was both interesting and, at times, frustrating. On one hand, it showcased the immense potential of generative AI tools to automate data extraction from historical newspapers like the Zanzibar Gazette. On the other hand, it revealed the technology’s current limitations when confronted with large tables. However, even with all the difficulties, visualizing the final table in Kepler.gl provided valuable insights into Zanzibar’s trade networks and the colonial power dynamics of the early 20th century.

# Bibliography

- Zanzibar Protectorate. *Index to the Official Gazette of the Zanzibar Government*. 1916. Print.
- Provocations from the Humanities for Generative AI Research. (2025). [arXiv:2502.19190](https://arxiv.org/abs/2502.19190)