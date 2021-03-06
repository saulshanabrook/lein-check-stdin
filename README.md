# `lein-check-stdin`

A Leiningen plugin that prints erros when parsing some clojure code.

It's output is in the form `<line number> <error message>` if it encounters
an error.

## Usage

Put `[lein-check-stdin "0.2.0"]` into the `:plugins` vector of your `:user`
profile. For example, to do this for all projects, you can set  `~/.lein/profiles.clj` to:

```clojure
{:user {:plugins [[lein-check-stdin "0.2.0"]]}}
```

Then you can use it to manually check any Clojure code, or use it to [lint Atom](https://github.com/saulshanabrook/linter-lein).

```bash
$ echo '(+ 1 1)' | lein check-stdin
# no output on good file
$ echo '(+ 1 1)\n(+ true false)' | lein check-stdin
{"file":"","line":1,"message":"java.lang.Boolean cannot be cast to java.lang.Number"}
```


## Releaseing

```bash
env LEIN_USERNAME=saul LEIN_PASSWORD=<pw> lein release :minor
```
