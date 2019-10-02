1. Download and install Python 3.6 from https://www.python.org/downloads/
2. Download and install Pycharm community 2017.1.2 from https://www.jetbrains.com/pycharm/download/#section=windows
3. Set the Python interpreter to Python 3.6
4. Open Command Prompt in Admistrator mode. Install libraries - urllib.request, bs4, os, __future__, nltk, docx, rake_nltk, operator, pymongo, pprint, re, html2text, traceback, tkinter, csv, numpy
   using pip install <package-name> command.
5. Follow the steps mentioned in https://docs.mongodb.com/manual/installation/ to download and install MongoDB Community version.
6. Download the RoboMongo IDE from https://robomongo.org/download 
7. Double click to run download_edgar_data.py file and provide specifications to download the data.
	1.1. Select Range of the Years for which you want to download the data. 
	     If you want to download for only one year, then simply enter same year in both the fields.
	1.2. Check Form Types to be downloaded.
	1.3. Give the local folder path where the data to be downloaded.
   The downloaded data can be seen at the provided path which will contain nested folder structure like Year -> Quarter -> Form Type -> Downloaded file   
8. Provide absolute path and year to sectionalize_10_k.py, sectionalize_8-k.py, sectionalize_riskfactors_424B3.py where data is present. Also, make sure MongoDb server is running.
9. Create MongoDB database named 'Capstone' and add collections - 'RawData', 'RawData_8K' and 'RawData424B' to store sectionalized data for 10-K, 8-K and 424B forms resepectively using RoboMongo IDE.
10. Open .py file to sectionalize the 10-K, 424B3, 424B4, 424B5 and 8-K forms. Sectionalized Data can be shown in RoboMongo IDE in above mentioned database and collections.
11. For analysis of 10-K forms, create a manual training set using Mongo_to_Excel.py script which will store all information from database to excel sheet.
   This excel sheet will be used to tag Risk Factors and Business sections manually.
	Categories to be used to tag the data is -  
	1. Financial circumstances - "1"
	2. FDA processes - "2"
	3. Other INDUSTRY-RELATED regulatory measures - "3"
	4. Measures outside of the US jurisdiction/market - "4"
	5. GENERAL BUSINESS – "5"
	6. PRODUCTS – "6"
	7. GENERIC PUBLIC COMPANY LANGUAGE – ALMOST ALWAYS APPEAR IN EVERY COMPANY’S FILING – AND SUCH STRUCTURE – "7"
	8. INTELLECTUAL PROPERTY - "8"
12. Store the tagged excel sheet at the location where the python files has been stored.
13. Download and install Anaconda 4.3.1 for Python 3.6 version from https://www.continuum.io/downloads. You can refer https://docs.continuum.io/anaconda/install to install Anaconda on your machine.
14. Set the Anaconda interpreter in Pycharm in settings tab.   
15. Add library sklearn into Anaconda to run Tagger.py script.  
16. Open Tagger.py file to create a classifier using Training set and Test it using Testing Set. The trainig and testing set will be automatically created using excel files. 
17. If new data comes in, then you can give this data manually in the script to test it.
18. The same procedure of Analysis 10-K will be used to analyze the 424B forms if the risk factors of these forms categorize into same categories.
19. The other scripts such as keyphrase_extraction.py is used to read the sectionalized data from MongoDb and extract the keyphrases for each paragraph. These keyphrases are stored back to MongoDB.
20. The script fact_risk_separation.py is used to find negative and positive polarity of the each paragraph and then find facts and risks of the negative meaning of the paragraph. Stored everything into a word document.















