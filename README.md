# 1p

1p is a small wrapper around `op`, the [1Password CLI utility](https://app-updates.agilebits.com/product_history/CLI) that makes it more useable.

## Dependencies

- `op` binary in your `$PATH`
- a CLI utility that can copy things to your clipboard
	- `xsel -ibk`
	- `xclip`
	- `pbcopy`
	- [`wayclip`](https://github.com/rahulg/wayclip) (personal favourite, but I'm biased)

## Usage

`1p` needs some information from you to function, it'll write this to `~/.config/1p/config`.
Note that your session keys are also stored in this file. Everything but the clipboard command really belongs in `~/.local/share/1p`, but I haven't gotten around to it yet.

```
$ 1p init
account name [foo.1password.com]: my_account.1password.com
email [bar@foo.test]: hello@me.com
secret key [A3-XXXXXX-XXXXXX...]: A3-12345-12312-41234214
clipboard copy command [xsel -ibk]: wayclip -i
```

What was my Amazon login called again?

```
$ 1p grep amazon
Amazon.com: <redacted-email> [www.amazon.com]
```

Ah yes. Let's get that password, shall we?

```
$ 1p cp Amazon.com
```

What if I wanted to pipe my password to something?

```
$ 1p get Amazon.com
<redacted-password>
```
