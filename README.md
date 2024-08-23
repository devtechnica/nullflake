# The Null Flake

The **Null Flake** is a simple Nix flake designed to provide an empty attribute set as an output. It's especially useful for overriding specific inputs, such as secrets, in `nixosConfiguration` tests without introducing unnecessary complexity.

### Why Use the Null Flake?

When testing NixOS configurations, you might encounter situations where certain inputs need to be overridden with a flake that has no meaningful content (e.g., secrets or sensitive data). The Null Flake serves this purpose by providing a placeholder flake that you can easily integrate into your build process.

### Example Usage

Below is an example of how to use the Null Flake in a Dockerfile to override an input when checking the build of a NixOS configuration:

```bash
RUN nix --extra-experimental-features flakes --extra-experimental-features nix-command flake lock --override-input sec "github:devtechnica/nullflake?shallow=1"
CMD nix --extra-experimental-features flakes --extra-experimental-features nix-command build '.#nixosConfigurations.hostname.config.system.build.toplevel' --no-link
```
