# Specification of bots.yml for software bots

Authors: Martin Monperrus et al.
Created on July 2019, [last modifications](https://github.com/monperrus/bots.yml/commits/master).
  
Software development platforms such as Github are slowly becoming a playground for software bots. For instance, the [Dependabot](https://dependabot.com/) makes pull-requests to fix insecure dependencies and [Repairnator](https://github.com/Spirals-Team/repairnator/) makes pull-request to fix build failures. Some bots are commercial, other come from research and academia. 

**Problem:** The problem with software bots is that they can be disruptive, they can be perceived as unwelcomed by developers, if not Github spammers.

**Solution:** Developers have a way to tell the authors and operators of software bots whether and to what extent the bot contribution are welcome.

## The bots.yml configuration file

Developers can add a `bots.yml` at  the root of their repository. This file specifies:
* which bots are allowed or disallowed
* which kinds of contributions are welcomed

In essence this file is equivalent to the `robots.txt` file put at the root of web servers to tell web crawlers about important crawling directives.

The file is written in the [YAML format](https://en.wikipedia.org/wiki/YAML).

### The `allow-bots` directive

The `allow-bots` directive specifies which bots are allowed.

```yml
allow-bots: yes
```

```yml
allow-bots: no
```

One can list bots by type, in this case, only the bots of the listed types are allowed to operate on this repo:
```yml
allow-bots:
  type: [research]
```

```yml
allow-bots:
  type: [research, commercial]
```

One can list bots by name, in this case, only the listed bots are allowed to operate on this repo:
```yml
allow-bots:
  name: [repairnator]
```

When bots are listed by name, new bots are allowed to make a single pull-request adding their identifier to the list. If this pull-request is rejected, it means that the new bot is not welcome.


### The `contribution-kinds` directive

The `contribution-kinds` directive specifies which kinds of contributions are welcome. The accepted values are
`new-issue`, `new-pr`, `issue-comment`, `pr-comment`. If it is not present in `bots.yml`, it is assumed that all kinds of contributions are welcomed.


```yml
# new issue and pr forbidden
contribution-kinds: [issue-comment, pr-comment]
```

### The `source-folders` directives

Sometimes, the source code directory or the repo owner wants only a subset of source folders to be analyzed. The `source-folders` directive targets this usage. If a `source-folders` directive is present, it means that contributions are only welcome for files in those folders.

```yml
source-folders: ['src/experimental']
```

Credits: Ivan Beschastnikh

## Known bots complying with `bots.yml`

Make a pull-request to add a new bot:

* TODO

## Credits

This comes from great discussion at the [1st International Workshop on Bots in Software Engineering in Montreal, Canada](http://botse.org/).








