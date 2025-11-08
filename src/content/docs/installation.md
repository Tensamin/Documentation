---
title: Installation
---

# Client

You can download the client from [GitHub](https://github.com/Tensamin/Frontend/releases) or directly from the [Homepage](https://tensamin.net).
For linux we have .deb and .rpm files on github and an [AUR Package](https://aur.archlinux.org/packages/tensamin-bin) (`paru -S tensamin-bin`) as well as a Nix Flake:

### Arch Linux

- This includes [>these distros<](https://wiki.archlinux.org/title/Arch-based_distributions)

Easy Install

- `paru -S tensamin-bin`
- `yay -S tensamin-bin`

Manual Install

```bash
git clone https://aur.archlinux.org/tensamin-bin
cd tensamin-bin
makepkg -si
```

### Nix Flakes

1. Add it to the Flake inputs.

```nix
{
  inputs = {
    tensamin.url = "github:Tensamin/Frontend";
    # ...
  };
  # ...
}
```

2. Add it to the `environment.systemPackages`.

```nix
{ }: {
  # ...
  environment.systemPackages = [ tensamin.packages.${system}.default ];
  # ...
}
```

# Iota

You can download the Iota from [GitHub](https://github.com/Tensamin/Iota/releases) or install it using on of these methods:

### Docker

Not available yet!

```yaml
/
```

`docker run /`

### Nix Flake

Not available yet!

```nix
services.iota = {
  enable = true;
  id = "<uuid>";
  users = [
    "<uuid>"
  ];
};
```

# Community
