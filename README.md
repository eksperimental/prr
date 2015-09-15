## prr – P(erl) R(eplace) R(ecursively)
**Search and Replace Recursively the Contents of any File**

Search recursively strings or regular expressions in the contents of
all the files in a folder, or any sub-sub-sub-folder, and replace it.


## Description

Shell script to let you search strings or regular expressions, 
and replace them with string or regular expressions, recursively
in multiple folders, be able to ignore some, global replacement or
just only one match, case sensitive or insensitive, ignore files listed
in popular ignore files such as `.gitignore` or `.hgignore`.

`prr` is a shell script that combines both of the fastest tools
for the job:
* `ag` (the silver searcher) – for searching the files
* `perl` for actually doing the string substitutions them.

`ag` will find the files that match your `SEARCH PATTERN`,
and `perl` will do the replacing.


### Requirements

* bash
* [ag – The silver searcher](https://github.com/ggreer/the_silver_searcher/)
* perl


## Usage

Basic usage will be:

```sh
prr [-cCdDghimuvV] [-o SEARCH_OPTIONS] SEARCH_PATTERN REPLACE_PATTERN [PATH]
```

## Default Options

By default, `prr` searches will be case sensitive, they will bot be
global, they won't be multi-line, it will ignore files listed in
ignore-files, it won't follow symlinks.


## Disclaimer

Please, understand before running this command, the nature of this project.
It is a command that given a string or a regular expression, it will search recursively in the folders
and replace inside the files.
It can be very destructive if not used with care, but due to it's early stage,
and since there are no unit tests that can assure that it will avoid
dangerous situations.

Eventhough I have designed this tool with dangers in mind, like trying to let the user know
what are the commands going to be executed, and so on, what I can recommend to have a backup copy of
use it in a directory that that you have under a SCM (Software Control Management) such as Git
or Subversion or CVS, in case things go wrong you can revert the changes, until v1.0 is reached.

Before version 1.0, `prr` will set the **confirm** option (`-c`) on, by default.

If you want to override this option, set the flag `-C`. 

Alternatively you can combine the following options:
* __debug__ (`-D`): to see how the options are interpreted, the commands being run.
* __dry-run__ (`-d`): which will only execute the search command and give you a list of files that
  will be modified.
* __verbose__ (`v`): to give more details about the action taking place. 


## Examples

```sh
# replace the first occurence of apple with banana for every file found
# recusively under the current dir.
prr 'Windoze' 'Linux'

# only files in currect dir (no subdirs)
prr 'apple' 'banana' *.*

# canse insensitive and global:  will replace with REPLICANT all
# matches of android, no matter the case, under lib/ and test/
prr -ig 'anDRoid' 'REPLICANT' lib/ test/

# Replace all occurences of "Mrs.Something" with "<Miss Something>" for
# all txt files under test/ dir, with the exception of test/drafts/ folder.
prr -g '\b(Mrs.)\s*(\w+)\b'  -o '--ignore-dir test/drafts/' '<Miss $2>' test/*.txt
```


## Installation Instructions

Put `[prr](prr)` in your `~/bin/` dir, or source it from the files that
bash will load automatically when launched, such as `~/.bashrc` or `~/.bash_profile`.


## Contributing

There is always room for error when trying to integrate two different tools into one.
If you think something is not working as expected, please
[create a ticket](https://github.com/eksperimental/prr/issues/new).


[Pull requests](https://github.com/eksperimental/prr/pulls) are always welcomed.


### Links

* [Github project](https://github.com/eksperimental/prr)
* [ag – The silver searcher](https://github.com/ggreer/the_silver_searcher/)


# TODO
* Escape quotes in SEARCH_PATTERN and REPLACE_PATTERN
* Once tested thoroughly I will enable the "follow symlinks" options.
  Which I decide to to disable momentarily just to rest on the safe side.


### Future plans

* Test it thoroughly with [shunit2](https://github.com/kward/shunit2).
* Test it with Travis CI.
* Right now it works with Bash, I will try to make it POSIX compliant,
  if I see it's doable.
* Port the "ag" command, to use "find", in case the former is not installed.


## Credits

Created by **[Eksperimental](https://github.com/eksperimental)**.


### License

This project is released under the Public Domain,
see [LICENSE](LICENSE.md) for the full text.
