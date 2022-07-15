This is the frontend for LIMS - Laboratory Information Management System.
We have developed add-ons to Benchling that are specific for our center. 
For example to visualize the lineage of strains and cell lines or make sample registration easier when submitting samples to the Analytical Core, IPC or the NGS lab.
 
## RESPONSIBILITY
- Project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
- LIMS Administrator: Ester Milesi, esterm@biosustain.dtu.dk
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk
- Code: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk, Eren Yagdian, ereyag@biosustain.dtu.dk and Osilamah Solomon Imhomoh, ossoim@biosustain.dtu.dk
 
# Functions in LIMS
 
- Upload analytical chemistry metabolomics results.
Upload raw results to Benchling (data table "AC quantification Raw Run") from chromeleon, Xcalibur, SmartPeak or our generic report.
Optionally refine the raw data associated with a request by selecting the best values for each compound.
Upload final result to Benchling (data table "AC quantification Raw Run").
 
- Media
Search for medium recipes and mixtures that is located in Benchling and get the recipes that you need. **does this only search "medium" or does it search though all "mixtures" maybe it makes sense to specify exactly which entities it searches through**
View medium recipes and calculate quantities based on the desired final volume.
You can go to Benchling and view the recipes by clicking on search, seclet type and enitity, and then at the bottom, select Medium with Recipe.
 
- Lineage
Browse through the lineage of strains and cell lines that are registered in Benchling.
You can se the parents and children, you can also compare metadata to other strains and cell-lines. 
 
- Export Experiment Data
Documentation for this is being detailed and will be updated soon
 
- Register samples for a request
Create and register samples to add to a request in Benchling. Create a plate or box to store the samples and specify metadata related to the samples.
 
- IDE
An in-build IDE in the LIMS solution with code snippets and how to guide.
Here you can use the IDE to play around with different data from Benchling. 

- Data Browser
Access sequencing and proteomics data from Analytical Core and NGS lab with sample references to Benchling.
Here you can look through the data that you have accesse to in the data-lake. Access is granted based on your acces rights in Benchling. So, if you have access to view a submission sample in Benchling you will also have access to see the data generated for that sample.

- Import online data
Upload and store culture-based online data into Data Lake. (under developerment)

- Purchasing 
Adminster commercial material orders made in Benchling. 
Here you can view the orders of commercial materials that has been requested through Benchling.  
In purchasing you can filter the orders by staus, requested by, seller or order by and keep track of the orders that are "requested", "in progress" or "completed". As a purchasing team member you can also edit multiple orders at once. 
 
### TECHNOLOGY USED
- Angular
- Node.js

### ANGULAR 
Angular is a TypeScript-based free and open-source web application framework led by the Angular Team at Google and by a community of individuals and corporations. 

### NODE.JS
Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code outside a web browser, which was designed to build scalable network applications. 

## Nice to know 
You can also find guidelines and generally asked questions regarding LIMS and Benchling in the knowledge base: https://biosustain-dev.atlassian.net/wiki/spaces/LHG/overview
