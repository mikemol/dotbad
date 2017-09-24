# `dotbad`

In pursuit of a Graphviz editor that's...not bad.

Really, Graphviz does not lend itself to easy editing.
Programmatically-generated charts based on existing data sets? Sure! It's great
for that! Because then you can write your templates as routines in your
language of choice. Because then you can quickly and dynamically regenrate your
graph with a different view in the overall dataset, to keep complexity down.
Because you can move the pain of tuning your charts out of the Dot language and
into some other language, some other engine.

Graphviz is not a great language for quick presentation. It is, howerver, an
excellent language for _relation_. Graphviz is a WYSIWYM language, along the
same vein as TeX. It's superb for writing out the content you have in mind, but
very difficult once you need control over _presentation_.

Enter `dotbad`. Intended to make controlling presentation easier while trying
to preserve a clean Graphviz file format and structure.
