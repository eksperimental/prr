## perl-replace-r
** Search and replace recursively**

It uses a combination both of the fastest tools for the job:
* `ag` (the silver searcher) – for searching the files
* `perl` for actually doing the string substitutions them.

`ag` will find the files that match your `SEARCH PATTERN`,
and `perl` will do the replacing.

## Installation instructions

Put `perl-replace-r` in your `~/bin/` dir, or source it from the files that
bash will load automatically when launched, such as `~/.bashrc` or `~/.bash_profile`.

### Requirements

* bash
* [ag – The silver searcher](https://github.com/ggreer/the_silver_searcher/)
* perl

## Contributing

If you think something is not working as expected, please [create a ticket](https://github.com/eksperimental/perl-replace-r/issues/new).

[Pull requests](https://github.com/eksperimental/perl-replace-r/pulls) are appreciated.

### Links

* [Github project](https://github.com/eksperimental/perl-replace-r)
* [ag – The silver searcher](https://github.com/ggreer/the_silver_searcher/)

### Future plans

* Test it thoroughly with [shunit2](https://github.com/kward/shunit2).
* Test it with Travis CI.
* Right now it works with Bash, I will try to make it POSIX compliant,
  if I see it's doable.

## Credits

Created by **Eksperimental**.

### License

This project is released under the Public Domain,
see [LICENSE](LICENSE) for the full text.
