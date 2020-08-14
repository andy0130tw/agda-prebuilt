# agda-prebuilt

![Linux (cabal)](https://github.com/andy0130tw/agda-prebuilt/workflows/Linux%20(cabal)/badge.svg)

Prebuilt, static-linked Agda binary for Linux.

## Usage

Extract the artifact in [action page](https://github.com/andy0130tw/agda-prebuilt/actions). The main executable is `./agda`. Execute it with some arbitary file as the first argument and observe its output.

```bash
$ ./agda /dev/null
#                          vvvvvvvv HERE vvvvvvvv
agda-gh: The lib directory /usr/local/bin/....../ does not exist
CallStack (from HasCallStack):
  error, called at src/full/Agda/Interaction/Options.hs:1173:8 in Agda-2.6.1-GBHAfzS8PHnCeWrfMQtOCD:Agda.Interaction.Options
```

You need to extract the `/lib` folder and copy it to the indicated location.

**Note**: Due to that the prefix is hardcoded in the program, the prefix is set to a system-wide directory `/usr/local`. You may need root permissions to copy the resources into it.

If you can't manage to do it, an environment variable `Agda_datadir` is required whenever you want to invoke `agda`. It should point to the library folder directory ([related issue](https://github.com/agda/agda/issues/4244)). Maybe I should write a simple script for this.

## Issues

- **In cabal v2+, prefix is actually ignored**: https://github.com/haskell/cabal/issues/5628#issuecomment-431596953
- (low priority) To enable cluster counting: https://github.com/4e6/text-icu-static-example

## References

- https://bazaar.launchpad.net/~ubuntu-branches/debian/sid/agda/sid/files/head:/debian
- https://ro-che.info/articles/2015-10-26-static-linking-ghc
- https://vaibhavsagar.com/blog/2018/01/03/static-haskell-nix/
