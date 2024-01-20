# odin-xdg

This package provides a basic interface for the [XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html)

## Provided Procedures

* `config_home() -> (string, Error)`
* `cache_home() -> (string, Error)`
* `data_home() -> (string, Error)`
* `state_home() -> (string, Error)`
*	`runtime_dir() -> (string, Error)`
* `data_dirs() -> ([]string, Error)`
* `config_dirs() -> ([]string, Error)`

All procedures will return the directories as configured by their relevant environment variables, if set, or the defaults prescribed in the spec otherwise.

## Considerations

The `runtime_dir` procedure requires retrieving the UID in order to calculate the return value (default: `/run/user/$UID`). To my knowledge (and I did hunt) there is no good *documented* way to do this in Odin yet. Consequently, odin-xdg relies on some of the deeper parts of `core` that you won't find in the [package docs](https://pkg.odin-lang.org/).

I don't know how likely those parts are to change, though I know gingerBill has some packages in there that are dummy packages for future work. As such, I cannot guarantee that a future update to the language won't unexpectedly break this package. Buyer beware.

## License

[0BSD](https://opensource.org/license/0bsd/)
