zip2fips
========

At work, we keep certain location information indexed by
zipcode. Recently, I wanted to feed that data into something that
worked with 5-digit FIPS county codes, and was unable to find an
easily-parsed table that mapped, however roughly, from one to the
other. The best I could find was the CDC's [County Cross
Reference](http://wonder.cdc.gov/wonder/sci_data/codes/fips/type_txt/cntyxref.asp)
files, but I realized I needed to do quite a bit of parsing before
they were really useful to me. I figured it might be of use to someone
else, so here it is.

The fetch_source script downloads the zip files and makes the one
"cleanup" change required, to line 1794315 of zipcty4, which
originally was missing GA as the state abbreviation.

makejson.py constructs the json dictionary from zip code to county
code from the zipcty files. The output is in zip2fips.json.

The state_fips.json file was made by hand, where "by hand" means I
copy-and-pasted [this
table](https://en.wikipedia.org/wiki/Federal_Information_Processing_Standard_state_code#FIPS_state_codes) and
manipulated it in Emacs.
