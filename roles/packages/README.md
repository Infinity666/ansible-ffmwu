This role installs apt and python packages on the target host. Necessary
apt repos can be defined.
It expects the arguments pkg_repo_list, pkg_pkg_list and pkg_pip_list
to be filled. If any argument is undefined, the repectibe action will
be skipped. See below for examples.

```
pkg_repo_list: # example
  repo_keys:
  - cool_guy:
    id: "67678686"
    server: keyserver.ubuntu.com
  - smart_guy:
    id: "2f2f2f2f2"
    server: keyserver.ubuntu.com
  repos:
  - cool_game:
    repo: 'deb http://ppa.launchpad.net/cool/game/ubuntu trusty main'
    update_cache: no
  - smart_tool:
    repo: 'deb http://ppa.launchpad.net/samrt/tool/ubuntu trusty main'
    update_cache: yes   # smart to have yes on last and only last entry

pkg_pkg_list: # example
- cool-game
- smart-tool
- python3-pip   # remember this one when wanting to use pkg_pip_list

pkg_pip_list: # example
- smart-tool-py-interface

# this flag controls the execution of the role; used to subdue if needed
really_do: True
```