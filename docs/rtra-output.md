---
title: RTRA Output
parent: RTRA SAS Program Guide
layout: default
created_date: 2020-06-02
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 6
---
## RTRA OUTPUT

It takes a few minutes to run the code. You will likely receive an email when the output is ready.

1. Login [here](https://eft-tef.statcan.gc.ca/#/)
2. Click on *From StatCan* folder
3. Download the output files

The output files will be available for 7 days before they are deleted. The files are ordered by RTRA code number. Use the time of submission to find the most recent output files.

List of output files:

* RTRA log file (.txt) indicates which stages of the RTRA processes have been successfully completed.
* SAS log file (.log)
* Output table as a SAS data set, CSV file and HTML file

The statistics reported in the output tables are rounded to the nearest rounding base. The rounding base for each survey can be found in the RTRA parameters [webpage](https://www.statcan.gc.ca/en/microdata/rtra/data).

You will find rows in the output tables with blank cell(s). The statsitics in a row with a blank cell is not broken down by the variable in the blank cell column. In other words, the statistics in that specific row is reported as if that variable was not included in the analysis.

 

### ERROR

It is not uncommon to get errors when you first submit your program. Use the checklist below to check and debug your SAS program.

Tips/Checklist:

* Check the RTRA log file if the RTRA process was unsuccesful at any stage
* Check the SAS log file for error messages
* Use the survey tag name at the beginning of the SAS program file name (eg. CCHS2015_zzzz)
* The library name is always *RTRAData*
* Do not include a libname line
* Use the dataset name in the data step following the *RTRAData* library name
* Don’t forget the semi-colon after every line in the data step!
* Don’t forget the semi-colon at the end of the macro!
* Don’t forget *run;* at the end of the data step
* Check the spelling of variables, procedure(s), data set name
* Check the RTRA [system limitations](https://www.statcan.gc.ca/en/microdata/rtra/training/limitation)

**Technique:** [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [SAS](https://mdlutoronto.github.io/tutorials-search/?tool=SAS) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)