# `dotbad`

In pursuit of a Graphviz workflow that's...not bad.

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

## Ideas

Rather than try to build a whole editor around `dot`, perhaps we can extend the
`dot` language itself.

Most ofthe time I spend in Graphviz, I spend formatting for output presentation
or restructuring. One possible way around that would be to try applying the idea
of "classes" to Graphviz entities. Something simple like defining an attribute
that applies to any entity type, `dbclass`, which would take either a string
token or a comma-separated list of string tokens, and then we could identify
attributes to apply to that class, perhaps with a graph-scope attribute
`dbclassattrs` that could take an argument of the form
`class1:attr1=val1,attr2=val2,attr3=val3;class2:attrA=valA,attrB=valB,attrC=valC`.
(Obviously, some EBNF grammar would be preferable to this description...)

I'd also want to define a couple special class attributes. One would be
`dbgrouping`, and would identify one (and only one) way this class would get
grouped. The only valid values that comes to mind (for the moment) would be
`subgraph`, `cluster` or `rank`, which, if set, would mean that entities with
this class would be placed inside a subgraph, a cluster or a forced rank
grouping, respectively. Another special class attribute would be `dbgroupattr`,
which would provide a way to define attributes that would be applied to the
subgraph, cluster or rank grouping.

On a different note, I'd like to define a more simplified and stable canonical
form that preserves comments, to help with linting and beautifying Graphviz text
prior to committing to `git` or other version control tools.
