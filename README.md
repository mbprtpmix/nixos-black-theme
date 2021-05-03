# [NixOS](http://nixos.org) black [SLiM](http://slim.berlios.de/) and [Tiny](https://github.com/off-world/lightdm-tiny-greeter) theme

![preview](https://raw.githubusercontent.com/mbprtpmix/nixos-black-theme/main/preview.png)

# Usage

Put the following snippets in your `configuration.nix`.

## SLiM

``` nix

  services.xserver.displayManager.slim = {
    enable = true;
    theme = pkgs.fetchurl {
      url = "https://github.com/mbprtpmix/nixos-black-theme/archive/v1.0.tar.gz";
      sha256 = "13bm7k3p6k7yq47nba08bn48cfv536k4ipnwwp1q1l2ydlp85r9d";
    };
  };

```

## LightDM Tiny

``` nix

  services.xserver.displayManager.lightdm = {
    enable = true;
    greeter.tiny = {
      enable = true;
      extraConfig = let
        black = import (builtins.fetchTarball {
            url = "https://github.com/mbprtpmix/nixos-black-theme/archive/v1.0.tar.gz";
            sha256 = "16qmz1c22arn614zfrfn9a6y7k091227ghvnm97xn8nvgd11hlhz";
        });
      in
        black.lightdm-tiny;
      };
  };

```
