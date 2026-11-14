# Notes 
> Notes file with cleaning remarks

## 10/11/2026 Import
- Imported Drama, checked only the main Drama sheet to be imported to avoid doubles.
- Imported Music, checked only the main Music sheet to be imported to avoid doubles.

# Drama

## 10/11/2026 Exploration
- *Language (008)*: Might be useful to create Lang 1, Lang 2 columns to document the multiple languages. Often "Und" seems to be English.
- Cfr. findings Omar: Country code is not readable => infer from imprint
- *Titles* often enclosed in square brackets, not clear whether this has a meaning or is just an artefact from the metadata export.
- *Author* names in all sorts of formats => last name capitalised, sometimes dates added. Dates need to be split from name, name normalised into format last name, first name.
- Column DDC (Dewey?) is empty
- There are 6 corprate authors, yet these contain personal author information in the title field. One even has two personal authors named in the corporate author field
- 7 records hold information in the Series field
- There are 16 subject allocations, could be considered to be left out, depending on richness of other data sets.
- 2 records have "Other corporate authors" yet these can be either attributed to a personal author or be labeled as Coprorate author.
- All records have Genre "Drama", 527 have Type "comedy", 636 "play", 32 "recitation", and 452 "tragedy".

## 10/11/2026 Step 1 Whitespace
- All trailing whitespaces and double whitespaces were deleted in all columns. This operation affected 0 cells, the data was clean on this part.

## 10/11/2026 Step 2 Title "Electronic Resource"
- Remove "[electronic resource]" using `value.replace(/\s*\[electronic resource\]/, "")`. 1646 cells out of 1647 were affected, all mentions were removed.

## 10/11/2026 Step 3 Remove DDC column
- Because of the lack of data in all three sets, we decided to remove the DDC column.

## 10/11/2026 Step 4 Author name standardisation
- Split `Personal author` column on","-separator => this splits the last name, first name, date information, person title and other possible information
- Normalise last name => Titlecase, 909 cells impacted
    - Manual check on nobility names where "de" has been capitalised => manually changed 10 cells.
- Place all date information in `Personal author 3` column
- Rename column with date information to `Personal author date`

## 10/11/2026 Step 5 Language (041)
- Remove MARC format and convert to comma separated lang codes. 3 records were edited manually.

## 10/11/2026 Step 6 Title bracket removal
- Removing square brackets around title by creating new column with rule `value.replace(/^\[(.*)\]$/, "$1")`
- Check difference and manually change 5 records.
- Remove old Title column and change name TEST title to Title.

## 12/11/2026 Step 7 Split Imprint
- Split the imprint column into three separate columns: `Place of imprint`, `Printer/publisher`, and `year published`
- First create a new column based on the `Imprint` column using `value.substring(-7)`to isolate the date.
    - Remove all "." and "," that were left.
    - correct 16 lines manually.
- Create new column trying to split off everything before the ":" delimiter to extract the place of imprint.
    - manual clean and correct 73 rows.
- Create new column to split of the charachters in between the ":" and the "," to extract the publisher/printer.
    - manual clean and correct 38 rows.
- Delete original `Imprint`column.


## 14/11/2026 Step 8 Clean author titles
- use text facet to look for titles (eg sir, bart. count, baron, ...)
    - Use replace to remove titles, 135 records changed.

## 14/11/2026 Step 9 Refine place of publishing
- remove square brackets
- remove extra information
- do some manual cleaning

## 14/11/2026 Step 10 




# Music
## 14/11/2026 Exploration
- *Language (008)*: Might be useful to create Lang 1, Lang 2 columns to document the multiple languages. Often "Und" seems to be English.
- Cfr. findings Omar: Country code is not readable => infer from imprint
- *Titles* often enclosed in square brackets, not clear whether this has a meaning or is just an artefact from the metadata export.
- *Author* names in all sorts of formats => last name capitalised, sometimes dates added. Dates need to be split from name, name normalised into format last name, first name.
- Column DDC (Dewey?) is empty
- There are 6 corprate authors, yet these contain personal author information in the title field. One even has two personal authors named in the corporate author field
- 7 records hold information in the Series field
- There are 16 subject allocations, could be considered to be left out, depending on richness of other data sets.
- All records have Genre "Music", 527 have Type "comedy", 636 "play", 32 "recitation", and 452 "tragedy".

## 14/11/2026 Step 1 delete DDC

## 14/11/2026 Step 2 Title "Electronic Resource"
- Remove "[electronic resource]" using `value.replace(/\s*\[electronic resource\]/, "")`. 980 cells out of 1647 were affected, all mentions were removed.

## 14/11/2026 Step 3 Personal author clean up
- Split dates from main column: create new column based on `Personal author`, removing all except the numbers, manually touch up where needed.
- Create column based on `Personal author` and remove all digits.
- Split the new column on "," separator
- Check columns 3, 4, and 5 for relevant information
- Titlecase the first column which contains the last name
- recombine column 1 (last name) and column 2 (first name)
- manual cleaning of only "," values.
- deleting irrelevant columns.

