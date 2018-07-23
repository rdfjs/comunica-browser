# Comunica Browser

This repository consists of ready-to-use browser builds of [Comunica engines](https://github.com/comunica/comunica/).

This repository is updated on every new Comunica build and release.
This means that these scripts can be used directly in any Webpage using GitHub pages.
The packages for which browser scripts are available can be explored in this repo
(also make sure to check their corresponding usage README over at the [Comunica repo](https://github.com/comunica/comunica/)).

Three categories of scripts are exposed:

#### Major release (_recommended_)

Each Comunica release is published the URL identified by its major version and will change on every [minor update and patch](https://semver.org/).
Use this if you want to stay up-to-date with the latest fixes, but do not want any problems due to breaking changes.

Source template: `http://rdf.js.org/comunica-browser/versions/[major-version]/packages/[package]/comunica-browser.js`

Source example (`actor-init-sparql-rdfjs` at version `1.x.x`): http://rdf.js.org/comunica-browser/versions/1/packages/actor-init-sparql-rdfjs/comunica-browser.js

#### Specific release

Each Comunica release is published to a specific URL and is immutable.
Use this if you want certainty that your script usage will not break.

Source template: `http://rdf.js.org/comunica-browser/versions/[version]/packages/[package]/comunica-browser.js`

Source example (`actor-init-sparql-rdfjs` at version `1.1.2`): http://rdf.js.org/comunica-browser/versions/1.1.2/packages/actor-init-sparql-rdfjs/comunica-browser.js

#### Latest build
The latest version of Comunica engines, updated with every commit to the [Comunica repo](https://github.com/comunica/comunica/pull/160#pullrequestreview-133152431).
Use this if you automatically want to stay up-to-date with the latest version, including breaking changes and potential bugs.

Source template: `http://rdf.js.org/comunica-browser/versions/latest/packages/[package]/comunica-browser.js`

Source example  (`actor-init-sparql-rdfjs` at latest version): http://rdf.js.org/comunica-browser/versions/latest/packages/actor-init-sparql-rdfjs/comunica-browser.js

## Example usage

The following example executes a simple SPARQL query using `actor-init-sparql` at version 1.x.x.

```html
<script src="http://rdf.js.org/comunica-browser/versions/1/packages/actor-init-sparql/comunica-browser.js"></script>
<script language="JavaScript">
  Comunica.newEngine().query('SELECT * { ?s ?p <http://dbpedia.org/resource/Belgium>. ?s ?p ?o } LIMIT 100',
    { sources: [ { type: 'hypermedia', value: 'http://fragments.dbpedia.org/2015/en' } ] })
    .then(function (result) {
      result.bindingsStream.on('data', function (data) {
        // Each variable binding is an RDFJS term
        console.log(data.get('?s').value + ' ' + data.get('?p').value + ' ' + data.get('?o').value);
      });
    });
</script>
```

## License
This code is copyrighted by [Ghent University – imec](http://idlab.ugent.be/)
and released under the [MIT license](http://opensource.org/licenses/MIT).
