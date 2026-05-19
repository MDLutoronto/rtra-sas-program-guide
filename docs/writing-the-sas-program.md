---
title: Writing the SAS Program
parent: RTRA SAS Program Guide
layout: default
created_date: 2020-06-02
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 3
---
## WRITING THE SAS PROGRAM

You have three options to write the SAS program. (1) You can write a SAS program from scratch. (2) You can modify the survey specific sample SAS code provided on the EFT (usually called *SampleProgramEng.sas* found under the *Example Program* folder of the survey directory). Not all surveys provide a sample SAS code. (3) Or use the Statistics Canada [RTRA SAS assistant](https://www.statcan.gc.ca/rtra-adtr/eng/sas).

### OVERALL STEPS

1. Library step to define a short term to represent the data directory (libname)
	* If you have a libname line in your SAS code delete it. If you don’t, ignore this step.
2. Data step to process the master dataset
	* The survey master dataset is called from the *RTRAData* library/directory
	* The name of this master dataset can be found on the RTRA Parameters [webpage](https://www.statcan.gc.ca/en/microdata/rtra/data)
3. Macro step to compute statistics
4. Name the SAS program file starting with the TAG name specific to the survey followed by an underscore
	* The TAG name can be found on the RTRA Parameters [webpage](https://www.statcan.gc.ca/en/microdata/rtra/data)
	* Eg. CCHS2015_myname

Note: The data step is necessary even if you are not modifying the original dataset because you cannot refer to the *RTRAData* library in the macro step.

 

### BASIC CODE STRUCTURE

The RTRA SAS code consists of 1) the data step and 2) the procedure macro step. The data step is used to process data by keeping/dropping observations and/or variables, creating new variables etc. The procedure macro step are used to compute means, frequencies, percentiles, percent distributions, proportions, ratios and shares.

The list of procedure macro steps are:

* %RTRAFreq
* %RTRAMean
* %RTRAPercentile
* %RTRAPercentDist
* %RTRAProportion
* %RTRARatio
* %RTRAShare

 

### DATA STEP

The SAS code for the data step has the following structure below. Each line (statement) ends with a semi-colon. The final statement run is used to execute previous lines of SAS statements. The asterisks are meant to be replaced with the appropriate parameter names.

```
data ******;
set RTRAData.***;
****** ******;
run;
```
 

Below are the definitions of the parameters to be replaced.

```
data ******;       -> name of the processed data set. Use one term with no spaces.
set RTRAData.***;  -> add the survey master dataset name found in the Parameters webpage (eg. RTRAData.CCHS2015)
****** ******;     -> add statements to process data
run;
```
 

DATA STEP - ADDITIONAL STATEMENTS

Additional statements in the data step are optional and only to be included if you want to process the master dataset before running a procedure. These statements are included between the set line and the run line. The lines to be added depend on how you want to modify the original survey dataset. A few examples of additional statements that can be included in the data step can be found below.

To drop observations (i.e., subset) use the if statement:

> Eg. Drop all values of gender with a value of 1

```
     if gender=1 then delete;
```

> Eg 2. To delete cases where the variable education has missing values [dot=missing for numeric]

```
     if education = . then delete;
```
To create a new variable which results in a new column:

> Eg. Create a new variable days that converts the variable year from the original data set

```
     days = 365.25*year;
```

> Eg 2. To convert a character variable age with a length of 3 digits into a numeric variable age2

```
     age2 = input(age, 3);
```
To recode a variable:

> Eg. Say a variable maritalstatus has values 5 that we want to recode (regroup) as 4

```
     if maritalstatus = 5 then maritalstatus = 4 ;
```
 

Additional documentation on SAS statements used in the data step can be found [here](https://documentation.sas.com/?docsetId=lestmtsref&docsetTarget=p10bvg3wauedhan1qly0hiokirlv.htm&docsetVersion=9.4&locale=en) and [here](https://documentation.sas.com/api/docsets/lestmtsref/9.4/content/lestmtsref.pdf?locale=en).

Some numeric measures are stored as character variables. To run procedures such as the mean procedure on variables stored as character, you have to convert them to numeric first. If you are not sure if the variable is stored as numeric or character, you can either assume it is numeric and run the procedure and to see if you get an error message or you can check the survey documentation found on the EFT.

 

### MACRO STEP - FREQUENCY & MEAN PROCEDURE

The SAS code for the frequency and mean macro procedures hav the following structure below. Again, the asterisks are meant to be replaced with the appropriate names. The definiton of arguments follows after the SAS code for each procedure. The SAS code/list of arguments for other procedures can be found here. Note that not all arguments are always necessary when running a procedure. For example, the ClassVarList variable may not be necessary depending on the output desired and the procedure used. When this is the case, simply omit the ClassListVar argument (the entire line) from the SAS code.

```
%RTRAFreq(
InputDataset =******,
OutputName=******,
ClassVarlist=******,
UserWeight=****** );
```
 

*Definition of arguments (Freq)*

**InputDataset**: Add the data set used to run procedure (the processed data set)  
**OutputName**: Name the output data table (the results of the procedure in a data table)  
**ClassVarlist**: Add variable(s) used to make the frequency table  
**UserWeight**: Add survey weight variable found in the Parameters document

 

```
%RTRAMean(
InputDataset =******,
OutputName=******,
ClassVarlist=******,
AnalysisVarList=******,
UserWeight=****** );
```
 

*Definition of arguments (Mean)*

**InputDataset**: Add the data set used to run procedure (the processed data set)  
**OutputName**: Name the output data table (the results of the procedure in a data table)  
**ClassVarlist**: Add variable(s) used to group mean calculation  
**AnalysisVarList**: Add variable(s) used to calculate mean  
**UserWeight**: Add survey weight variable found in the Parameters document

 

### EXAMPLE OF FINAL SAS CODE

Below is an example of an RTRA SAS code.

```
data ******;
set RTRAData.***;
****** ******;
run;
```

```
%RTRAFreq(
InputDataset =******,
OutputName=******,
ClassVarlist=******,
UserWeight=****** );
```

```
%RTRAMean(
InputDataset =******,
OutputName=******,
ClassVarlist=******,
AnalysisVarList=******,
UserWeight=****** );
```

**Technique:** [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [SAS](https://mdlutoronto.github.io/tutorials-search/?tool=SAS) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)