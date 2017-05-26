# goloader

A fork of golang.org/x/tools/go/loader but with support for choosing the [`types.Importer`](https://golang.org/pkg/go/types/#Importer) that is used.

## Why?

By default, go/loader uses it's own internal implementation of `types.Importer` which loads *all* information by reading Go source files from disk and then performing type-checking. This can be quite slow, because it includes transitive dependencies. For writing things such as editor plugins, [this isn't suitable](https://github.com/sourcegraph/go-langserver/issues/178).
