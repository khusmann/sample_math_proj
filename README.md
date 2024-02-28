This repo contains example data and syntax used for demonstration purposes in
this [blogpost](https://cghlewis.com/blog/data_clean_03/) series on creating a
data cleaning workflow.

---

## Note for Crystal:

Here's an example of how data cleaning would look like with my library! Here's a
quick overview:

All of project's codebook information would go into `codebook.yaml`. It would
act as the single source of truth for all of the project's variables, metadata,
and general validation. It would also have the ability to define different
"releases" of the data (e.g. public / restricted versions).

The `cleaning-syntax.Rmd` file shows how the codebook would be used to import,
clean, and export a raw data file, found in
`data/input/w1_mathproj_stu_svy_raw.csv`. Instead of loading the data file
directly, the file is loaded through another yaml definition:
`w1_mathproj_stu_svy.yaml`. This file serves as a bridge between the raw data
and the codebook definitions. It would do two main things: rename columns (to
match the codebook) and remap values (to match the codebook). More complex
processing would still be done in the cleaning syntax (as shown in the Rmd file
for the example of fixing unique ids).

I hope this illustrates what I'm trying to do! The advantage of this approach is
that it enables a majority of our pipeline to be defined in these `yaml` files
that allow us to effectively describe the structure of the results we want, and
reuse definitions across multiple files. This is an example of how we can make
metadata work FOR us, instead of having it be an extra burden or afterthought on
a project. The more metadata you produce, the more validation you get on your
data, and the richer data dictionaries you can produce for your users.

With a standard format for describing pipelines (the yaml files) data cleaning
audits are much easier compared to a bunch of R scripts. It also helps us
scaffold decisions in people's data cleaning pipelines, because the library
could scan the configuration files and give the user warnings when they were
configuring things in weird ways (compared to a raw script, where decisions are
no-holds-barred)

Future versions would have the capacity for all kinds of hand features, like the
ability to rename a variable in your codebook, and have the change automatically
propogate to all of the data file yaml definitions. Wouldn't that be handy??

Maybe we could give this a fancy term, like "metadata-driven data cleaning" or
something?

Anyway, thanks for reading this far and listening to my crazy ideas!
