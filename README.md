# Control-Inventory
Various excel formulas to consolidate control data into custom controls along with team, control owners, frameworks and more. Refer to the 
- [Control Inventory Template](https://docs.google.com/spreadsheets/d/1kEB0t3QLhopN4Q5PdrbuDz3_0N6DURJE9FfT6C6eA0Q/edit?usp=sharing)
  - Unique filtered concatenation for framework type
    - =ARRAY_CONSTRAIN(ARRAYFORMULA(TEXTJOIN(";", TRUE, UNIQUE(IFERROR(FILTER(Data!B:B, REGEXMATCH(Data!F:F, CONCATENATE(".*", A3, ".*"))), "")))), 1, 1)
  - Dependency Check and Formatting =IF(F3<>"", 
  ARRAYFORMULA(TEXTJOIN("; ", TRUE, IF(TRIM(SPLIT(F3, ";"))<>"", 
    IF(VLOOKUP(TRIM(SPLIT(F3, ";")), Main!A:B, 2, FALSE) = "", 
      TRIM(SPLIT(F3, ";")), 
      TRIM(SPLIT(F3, ";")) & " - " & VLOOKUP(TRIM(SPLIT(F3, ";")), Main!A:B, 2, FALSE)), 
    ""))), 
  "")
  -


# Import Template
- [Import Template](https://docs.google.com/spreadsheets/d/1kEB0t3QLhopN4Q5PdrbuDz3_0N6DURJE9FfT6C6eA0Q/edit?usp=sharing)
  - **=IMPORTRANGE("spreadsheet key", "Tab Name!A:A") 

## Parse file
This Google Apps Script processes data in two sheets, 'Data' and 'Main,' by splitting and expanding information in specified columns, and then updates corresponding sheets, such as 'Data by ID,' 'ID by Owner,' 'ID by Framework,' 'ID by Team,' and 'ID by Assignee,' based on the segmented data.





