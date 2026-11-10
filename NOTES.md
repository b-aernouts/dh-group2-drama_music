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

## 10/11/2026 Step 2 Title
- Remove "[electronic resource]" using `value.replace(/\s*\[electronic resource\]/, "")`. 1646 cells out of 1647 were affected, all mentions were removed.
- 
