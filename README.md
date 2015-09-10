# PKGBUILDs for [Arch User Repository](https://aur.archlinux.org) maintained by [ethail](https://aur.archlinux.org/packages/?SeB=m&K=ethail)
Includes control scripts for managing AUR packages. Huge thanks to [eli-schwartz](https://github.com/eli-schwartz/pkgbuilds)
Requires @falconindy's [pkgbuild-introspection](https://aur.archlinux.org/packages/pkgbuild-introspection-git) tools to auto-generate .SRCINFO

## How it works
Commit PKGBUILDs in named subdirectories. Export them to the AUR with the included `aurpublish` script, using the subtree push stratagem.
This preserves an independent history for third-party hosting, pull requests... ;)


## Commands
* `./setup.sh ssh`
> Append ssh-config rules for accessing the AUR.

* `./setup.sh hooks`
> Install githooks.

* `./aurpublish PACKAGE`
> Push PACKAGE to the AUR. With "--new", registers the package.

## Hooks
* pre-commit
> Reject whitespace errors, and auto-generate .SRCINFO for all changed PKGBUILDs.

* prepare-commit-msg
> Prefill the commit message with a list of updated packages + versions (if any).

* post-commit
> Clear aurballs and generate a new, up-to-date aurball for all changed PKGBUILDs.

#What I Maintain for now:

...

Any trouble or problem with iany of my packages, you can post a comment at the AUR package's page or send me an e-mail. 
