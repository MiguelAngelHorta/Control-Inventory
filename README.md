# Control-Inventory
Various Excel formulas to consolidate control data into custom controls along with team, control owners, frameworks, and more. Refer to the 
- [Control Inventory Template](https://docs.google.com/spreadsheets/d/1kEB0t3QLhopN4Q5PdrbuDz3_0N6DURJE9FfT6C6eA0Q/edit?usp=sharing)
  - **Return unique filtered concatenation for framework types**
    - =ARRAY_CONSTRAIN(ARRAYFORMULA(TEXTJOIN(";", TRUE, UNIQUE(IFERROR(FILTER(Data!B:B, REGEXMATCH(Data!F:F, CONCATENATE(".*", A3, ".*"))), "")))), 1, 1)
  - **Return control mappings and concatenate control text based on array**
    - =IF(F3<>"", 
  ARRAYFORMULA(TEXTJOIN("; ", TRUE, IF(TRIM(SPLIT(F3, ";"))<>"", 
    IF(VLOOKUP(TRIM(SPLIT(F3, ";")), Main!A:B, 2, FALSE) = "", 
      TRIM(SPLIT(F3, ";")), 
      TRIM(SPLIT(F3, ";")) & " - " & VLOOKUP(TRIM(SPLIT(F3, ";")), Main!A:B, 2, FALSE)), 
    ""))), 
  "")
  - **Return concatenated matches for a single control string**
    - =TEXTJOIN(";", TRUE, IFERROR(UNIQUE(FLATTEN(SPLIT(TEXTJOIN(";", TRUE, ARRAYFORMULA(IFERROR(VLOOKUP(TRIM(SPLIT(F4, ";")), Main!A:E, 3, FALSE), ""))), ";"))), ""))


# Import Template
- [Import Template](https://docs.google.com/spreadsheets/d/1kEB0t3QLhopN4Q5PdrbuDz3_0N6DURJE9FfT6C6eA0Q/edit?usp=sharing)
  - Import control data from the control inventory
    - **=IMPORTRANGE("spreadsheet key", "Tab Name!A:A")
  - ![iScreen Shoter - Google Chrome - 240229211309](https://github.com/MiguelAngelHorta/Control-Inventory/assets/106134627/bd8c4d10-0e02-4430-b631-bd50cc52708d)
  - Once imported, run the controlDataSplit file attached to split strings with a ";" (semicolon) delimeter into new rows.


## controlDataSplit file
This Google Apps Script processes data in two sheets, 'Data' and 'Main,' by splitting and expanding information in specified columns, and then updates corresponding sheets, such as 'Data by ID,' 'ID by Owner,' 'ID by Framework,' 'ID by Team,' and 'ID by Assignee,' based on the segmented data.





