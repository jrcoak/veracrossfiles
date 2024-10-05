# veracrossfiles
How to download Files from Veracross in bulk

How to Batch Export Files from Veracross
(example use case: exporting Health files for third party)

1. Start on a student’s record >> Files tab (or start from a Find Files query on the System
homepage and go straight to 2a).
2. Open the embedded query by clicking on the grey icon with a square and an arrow on
it.

      a. Build a query containing all of the files needing to be exported (sort by
      Classification if necessary).
     
      b. Include all fields necessary for identifying the files in the third-party system (VC
      student ID, any other student ID, names, etc.)
  
      c. Hide from display any superfluous fields, such as Classification, Name, Size,
      Notes, Input Date, etc.
  
     d. Query must at least include Download field and Description, but most likely also
      the VC Student ID field.

4. Once the query is built, click on the Action menu (lightning bolt) and Export to Excel.

5. Once in Excel, delete the first row (headers will cause the script to error out).

6. In a blank column, concatenate the desired fields that will be used as identifying the
exported files.

      a. Enter the formula “=CONCAT(text1,text2...)”
      
      b. If the desired end result is to use both VC Student IDs and the File Descriptions
      as the final naming convention of the files, click on a cell with the Student ID in
      it, then enter a comma, then click on the cell with the corresponding File
      Description in it, then close the parentheses.
      
      c. Ex: =CONCAT(B2,C2)

6. In a blank column, copy the ***values only*** (right click and select Paste Specials >>
Values) from the concatenated column.

7. Find & Replace all hyphens (-) and spaces ( ) with underscores (_) in the new column.

8. Remove all other columns, leaving only:

      a. Download field in Column A.
      
      b. File Name (concatenated) in Column B (must be value, cannot be formula).

9. Create a new folder on your desktop and do not include any spaces in the title (ex:
HealthFiles). This will be the final destination for the files once they are exported from
VC.

10. Open zip file (sent separately than this Word document) >> Automator workflow (must
be run on a Mac).

11. Within workflow, replace “test” with the name of the new file destination:
do shell script "curl -L " & item 1 of theItem & " -o $HOME/Desktop/test/" & item
2 of theItem

12. Click from Automator back into the Excel spreadsheet then back into Automator and
click Run (triangle icon).

13. All of the files listed in the Excel spreadsheet should now be viewable in the new
desktop folder.
