LIMS - Laboratory Information Management System.
We have developed add-ons to Benchling that are specific for our center. 
For example to visualize the lineage of strains and cell lines or make sample registration easier when submitting samples to the Analytical Core, IPC or the NGS lab.
 
## RESPONSIBILITY
- Project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
- LIMS Administrator: Ester Milesi, esterm@biosustain.dtu.dk
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk
- code: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk, Eren Yagdian, ereyag@biosustain.dtu.dk and Osilamah Solomon Imhomoh, ossoim@biosustain.dtu.dk
 
# Functions in LIMS
 
- Upload analytical chemistry metabolomics results
upload raw results to Benchling (data table "AC quantification Raw Run") from chromeleon, Xcalibur, SmartPeak or our generic report.
optionally refine the raw data associated with a request by selecting the best values for each compound.
Upload final result to Benchling (data table "AC quantification Raw Run")
 
- Media
Search for medium recipes that is lowcade in Benchling and get the recipes that you need must farster
view medium recipes and calculate quantities based on the desired final volume.
You can go to Benchling click on search seclet type and then seclet enitity and then at the bottom selcet Medium with Recipe to what you have accesse to.
 
- Lineage
Browse through the lineage of strains and cell lines that are registered on Benchling.
you can se the parents and children, you can also compare metadata other strain and cell 
 
- Export Experiment Data
Download experiment related data from Benchling in different formats.
- .xlsx
- .csv
you cab add filter columns in the order that you want the file to be sort by, before you download.   
 
- Register samples for a request
Create and register samples to add to a request on Benchling. create a plate or box to store the sample and specify metadata related to the samples.
 
- IDE
An in-build IDE in the LIMS solution with code snippets and how to guide.
Here you can use the IDE to get 

- Data Browser
Access sequencing and proteomics data registered on Benchling.
 
- AC Booking
here you can book time with laboratory instrument
 
- Purchasing: view and edit material orders
 
### TECHNOLOGY USED
- Angular
- Node.js
- Docker