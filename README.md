# Hello Plasmidsaurus!
Thank you for your consideration for the Product Engineer role.  
The projects below highlight my experience building interactive data visualizations using React, D3.js, and Python-based tools. While some projects were collaborative or part of larger systems, I’ve consistently taken initiative on the design and implementation of key components, often building from scratch or working independently on distinct features. These examples show my ability to translate complex biological data into clear, usable interfaces, with a focus on usability, performance, and scientific accuracy.

### Mammoth Biosciences
My most relevant work was done at Mammoth. Unfortunately, it involves internal IP that I cannot share directly, but I’ve included a summary below and would be happy to discuss details further.

At Mammoth, I was the primary developer of a full-stack data platform to analyze the off-target effects and binding patterns of novel Cas proteins. My work enabled scientists to transform raw CRISPResso2 output into intuitive, real-time visual insights across thousands of experiments.

#### Visualization tool
I developed a multi-page Streamlit application for internal scientific users. Visualizations were connected to internal APIs or live Athena queries over S3 data. Tools included:

- Editing efficiency dashboard: An interactive Plotly visualization showing per-position editing rates (inserts, deletions, substitutions), aggregated across levels such as experiment or amplicon. Scientists could drill down to individual experiments or analyze trends across effectors and assay types.
- Gene coverage tool: A customizable bar chart (Plotly) displaying read or mutation density across targeted gene regions. Used for quality control and exploratory insights. 
- Dynamic Weblogos: An on-the-fly motif discovery tool. Scientists could search and select effectors, choose associated analysis jobs, filter by assay type, mode, or library, and apply thresholds (e.g., top 5% by mean fold change). The filtered PAM sequences were then used to generate sequence logos in real time, helping identify consensus motifs tied to Cas protein performance. 
- Contig viewer: A genome browser implemented using Gosling.js, allowing scientists to navigate from base-pair level up to chromosome scale and visualize mutation distributions across contigs.

#### Data engineering & pipeline architecture 
To supply these tools, I built a robust, automated ETL pipeline that processed raw text-based outputs from CRISPResso2, extracting insertion, deletion, and substitution events by genomic position. The data flowed from AWS S3 into structured Glue tables, making it queryable via Athena or Python scripts. I joined this with contextual metadata (e.g., amplicon structure, effector identity) to enrich downstream analysis.

The pipeline ran nightly and was deployed using Terraform and GitHub Actions for scalable, hands-off operation. This infrastructure served as the foundation for all visualization and analysis tools.

#### Sample tagging chart
In a separate project at Mammoth, I built a standalone visualization tool to help scientists identify unannotated samples lacking experimental metadata. The chart dynamically showed the number of untagged samples per user, with interactive features like hover highlights to help users quickly spot gaps in annotation. This helped improve data integrity and guided scientists toward cleaner downstream analysis. I made this chart using D3.js running in a React component.

### NYC Health Violations Map

[Link](https://jpcaltabiano.github.io/final//)

As part of a graduate data visualization course, I collaborated with a teammate to create an interactive website using D3.js that visualizes restaurant inspection data across New York City. The goal was to highlight the surprisingly high frequency of critical health violations, especially among major fast food chains like McDonald's, Subway, and Dunkin.

The site includes:
- An interactive map showing inspection violations across the city with pan, zoom, and hoverable data
- A grouped bar chart comparing the top six critical violations across five major fast food chains
- Linked interactivity between map and charts, with dynamic filtering based on user clicks
- Custom UI elements including dropdowns, tooltips, and info markers, all built with vanilla D3

While this was an academic project, it served as a valuable end-to-end exercise in using D3 for data-driven storytelling and browser-based interface design. We focused on getting interactivity and data integration working across views, despite limited time and experience.

### CO2 Emissions Map

[Link](https://jpcaltabiano.github.io/04-Remix/)

Built independently for the same data viz course. This project visualizes global CO₂ emissions per country, both in total and per capita, with a focus on clarity, interactivity, and exploratory control. I reimagined an existing visualization by designing a custom globe projection, building UI toggles for total vs per capita views, and linking the map to a supplemental line chart that updates based on user interaction.

The site includes:
- A map and chart that are fully interactive - clicking a country shows its emissions over time and clicking the ocean returns to a global view
- A timeline slider that lets users scrub through decades and compare specific years
- A bespoke color scale with designed with custom bins to highlight both subtle differences and extreme values
- A flexible UI with toggles for total vs per capita modes, along with tooltips and annotations for clarity

Under the hood, I optimized performance by pre-rendering elements and toggling visibility instead of redrawing. I also refined the layout and responsiveness using CSS and SVG sizing, which was a rewarding learning experience.

This project demonstrates my ability to take an existing concept, identify its design flaws, and rebuild it into a usable, data-rich interface using D3.js and standard web tools.


### NYDEC Swallow Toxicology Visualization
This project supported a toxicology study conducted by Yu Chen at the New York State Department of Environmental Conservation, examining effects of PFAS exposure in tree swallows. Working with raw field data, I used R to preprocess morphological measurements and apply principal component analysis to derive a body condition index, a standardized metric based on the structural size and weight.
The analysis included:
- Visualizations using ggpolt2 and boxplots to compare body condition across contaminated and control sites 
- Data cleaning and reshaping for statistical modeling
- PCA to reduce multi-dimensional measurements into a single metric
- Fitting a quadratic regression model (weight vs. size) and extracting residuals as indicators of body condition
- A linear mixed-effects model to assess the effects of site and age on body condition, accounting for individual variability
