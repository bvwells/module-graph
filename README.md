# Go Module Graph Behaviour

The documentation [here](https://golang.org/ref/mod#go-mod-graph) states:

```markdown
The go mod graph command prints the module requirement graph (with replacements
applied) in text form.
```

The go module file contains a single dependency on github.com/go-openapi/swag.
The replace command is used to replace the github.com/go-openapi/swag dependency
gopkg.in/yaml.v3 to a later version.

After performing ```go mod tidy``` the go.sum file only contains the replaced
version of the gopkg.in/yaml.v3 dependency.

However, when running

```bash
go mod graph > graph.txt
```

The output graph contains the original dependencies for gopkg.in/yaml.v3, i.e.
the version has not been replaced.
