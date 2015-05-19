# Data Transformation with Talend: From .md to .ttl
This section describes, why and how the data integration tool [Talend](http://de.talend.com/products/talend-open-studio) is used to create a linked data representation of requirements.  
Recap: We are using gitbook to manage our requirements. Each requirement is located in a seperate .md file on github. We have english and german versions of the same requirement. In the linked data representation, there will only be one URI holding the requirements in both languages.
## Why Talend?
Talend is a data integration tool. It operates with schemata, which makes it a useful tool for all kinds of database management. Even though Talend is not specifically designed for file transformations, its ability to create and illustrate workflows has certain advantages, for example automatization and visual error indicators.
## Process Description
### Prequisites 
* clone github repository with requirements to transform to the local machine. We will extract the data using Talend in order to make it available on a server later on.
* download and install Talend
* Create a project and a job

### Ideas
Since Talend is not primarily meant for data transformation we need to work with the schemata. This works as follows:
* create schema with fields "subject", "predicate" and "object" representing the triple
* create output .ttl file for each requirement
  * for all triples
    * for all requirement files
      * load a requirement (input) file
      * extract the subject
      * choose a fitting predicate
      * extract the object
      * map those fields to the output .ttl of the specific requirement 
  * append the just created triple to the other triples of a specific requirement
* delete duplicate rows

### Example

The following requirement is available in english and in german:

{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/de/requirements/req0114.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0114.md" %}


One may want to create a .ttl represenation, that holds both the german and the english text, as well as information about properties that both requirements share, their id for example.
Thus, after the extraction, the information may be represented like this:

req0114	hasContent	"*  The system creates automatic link proposals"@en .  
req0114	hasContent	"*  Das System erstellt Verlinkungsvorschläge"@de .  
req0114	hasId		0114 .  

A Talend workflow can read a file, create *one* triple, save it into an output file and repeat the process. New triples can be appended to the output file then.

*TODO: Insert Image

We assume we have two directories EN and DE, each holding the requirements for one language. 
The the workflow could look like this: 


1. Loop through files in EN 
  1. Take file as Input 
  2. extract name (e.g."req0114") from the file name or the content 
  3. chose predicate "hasContent"
  4. extract the content from the file, add language tag "@en" manually
  5. map those strings to a schema
  6. write to output file (e.g. req0114.ttl) 
2. Do 1 with directory DE; writing to the output file means appending to the output file
3. Do 2 in directory EN, with the same subject, with predicate "hasId" and with the predicate "<id>"
4. Do 3 with directory DE
5. remove duplicates

### Talend Components

* Iterate through files in an directory: **tFileList**
* Take one of those file as an input: **tFileInputRaw** or **tFileInputDelimited** (depends on the data). The file name of this component must reference the CURRENT_FILE(PATH) variable of tFileList
* 1.ii-1.v are handled by **tMap**. Information can be extracted using methods of java.lang.String. 
* Write to output file: **tFileOutputDelimited**. Use the "Append" option, so that the next time, a triple is created, the file does not get overwritten.
* **tUniqRow** is useful to delete duplicate rows.
Why is this useful? Since it is possible, that some requirements are available in EN only, some are available in DE only and some are in available in both languages/directories, we iterate trough both directories. When a requirement is only available in one language, this works fine and creates outputs like this:  

req9999	hasContent	"*  I don't have a german brother"@en .  
req9999	hasId		9999 .  

However when both languages are available, the result looks as follows:  

req7777	hasContent	"*  I am available in two languages"@en .  
req7777	hasContent	"*  Ich bin in zwei Sprachen verfügbar "@de .  
req7777	hasId		7777 .  
req7777	hasId		7777 .  

Thus, duplicates need to be removed. 
If you can assure that - speaking of languages - one set of requirements is a subset of the other, you do not need to iterate over both directories when collecting the IDs but only over the superset.


