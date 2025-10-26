# Contributing

Everyone is invited to contributing to this ebook. It is written in Markdown and
the Markdown source are the `.i.md` files in this folder. The `docs/` folder is output
and should not be manually edited. All the SPARQL queries are found in the `sparql/`
folder. 

## Markdown syntax + extensions

The set up of this repository uses Markdown, but starts with files written
in Markdown but with some sugar. These extra command will be preprocessed
to create Markdown that is compatible with GitHub pages.

The extra commands are included in an `.i.md` file. The following subsections
give some information about the possible commands.

### SPARQL and their output

SPARQL examples can be included with the following instruction (on an otherwise empty line):

```xml
<sparql>someQuery</sparql>
```

The build script will look for the file `someQuery.rq` in the `sparql/` folder.

The output is added with a similar command. If you want a table with results, use:

```xml
<out>someQuery</out>
```

## Citing articles

If you want to cite an article, make sure the article is found in Wikidata and
include the following code in the `.i.md` file: `<cite>Qxxxx</cite>`.

Make sure to add the following content at the end of the `.i.md` file:

```markdown
## References

<references/>
```

## Crossreferences

Crossreferences from one section to another can be made with a combination
of `<section>` (target) and `<xref>` (where you refer). For example,
`<section label="intro" level="#">Introduction</section>` is used
to make a chapter referencable, and `<xref>intro</xref>` is used to refer
to that chapter.

### Adding a new query

Additional content can be contributed with a pull request. The Markdown content
is assumed to have a CC-BY-SA license, while the SPARQL query (-ies) must have
the CCZero license/waiver.

 * step 1: write the SPARQL query and create a `.rq` file in the `sparql/` folder
 * step 2: edit the `.i.md` file where the query should be added and add some written explanation
 * step 3: (Linux) run `cd sparql/; make`
 * step 4: (Linux) run `make` (so, in the root folder)

If that works, add the files like this:

 * step 5: (Linux) run `git add -f sparql/someQuery.rq` (the `-f` is important)
 * step 6: (Linux) run `git add docs/sparql/someQuery.code.md`
 * step 7: (Linux) run `git add -u`
 * step 7: (Linux) run `git commit -m "Added a query to do some lookup"`

## Requirements

- Groovy
- nodejs
- citation-js (see doi:[10.7717/peerj-cs.214](https://doi.org/10.7717/peerj-cs.214))
- make
- curl (optional, but handy)

## Install

The requirements can be installed on Debian GNU/Linux with:

```shell
sudo apt install groovy make nodejs curl
npm install citation-js
```

