# ark2pan

## csv_tools

### csv2pan

Parses specifications in CSV format obtained from the AMD and Intel websites and generates Pan templates in `./output/` for use with [Quattor](www.quattor.org).

### scrape_amd

Creates the `./data/amd/` working directory for AMD specifications and prints instructions for how to obtain the CSV file.

### scrape_intel

Scrapes the Intel specifications web pages and generates a CSV file per processor in `./data/intel/` in a similar fashion to the method used by JavaScript on each of the pages.

## ark_xml_tools

Historical tools to parse XML data from Intel's ARK database and generate Pan templates for use with [Quattor](www.quattor.org).

ARK no longer makes this data available in XML format, so these tools are only kept for historical interest.

### arkparser

Implements a parser to read the pseudo-spreadsheet XML format generated by ARK which returns a list of dictionaries, each dictionary representing a single CPU.

Example:
```python
from json import dumps
from arkparser import ARKParser
arkparser = ARKParser()
cpus = arkparser.parse('Intel_ARK_AdvancedSearch_2016_05_11.xml')
print dumps(cpus[34], indent=4)
```


### ark2pan

Uses `ARKParser` to generate a single Pan template for each CPU.

Example:
```
./ark2pan Intel_ARK_AdvancedSearch_2016_05_11.xml
```


### ark2aq

Uses `ARKParser` to generate `add_cpu` commands for aquilon, should be used with templates from `ark2pan`.

Example:
```
./ark2aq Intel_ARK_AdvancedSearch_2016_05_11.xml
```
