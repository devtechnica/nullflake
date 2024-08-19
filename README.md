# The Null Flake

Sometimes, when running nixosConfiguration tests, I need to override some input flakes to a flake with just an empty attribute set as an output (secrets etc). This is that flake that I use to do the override. Feel free to use this flake in your own build process.

Here's of usage in a excerpt from a dockerfile used to check build of a nixosConfiguration Flake:

```bash
RUN nix --extra-experimental-features flakes --extra-experimental-features nix-command flake lock --override-input sec "github:devtechnica/nullflake?shallow=1"
CMD nix --extra-experimental-features flakes --extra-experimental-features nix-command build '.#nixosConfigurations.hostname.config.system.build.toplevel' --no-link
```
