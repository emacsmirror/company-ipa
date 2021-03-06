company-ipa
===========

![screencast](screencast-out.gif)

This package adds ipa completion for company.

Usage
=====

To install clone this package directly.

```emacs
(load-file "PATH/company-ipa.el")
```

Alternatively it should now be on MELPA.

After the package is installed, you can enable `company-ipa` by adding the following to your init file:

```emacs
(add-to-list 'company-backends 'company-ipa-symbols-unicode)
```

It is highly recomended that you use company-flx, otherwise completions will not work very well.

Use the variable `company-ipa-symbol-prefix` to change the prefix to trigger completion.
By default this is bound to `~pp`. You can change this with:

```emacs
(company-ipa-set-trigger-prefix "¬")
```

Completion without company-flx
------------------------------

If you do not wish to use company-flx, completion is more cumbersome, but still
possible. First, you should make sure that the completion trigger
(`company-ipa-symbol-prefix`) is at least as long as
`company-minimum-prefix-length`. (In the default setup for company and
company-ipa this is the case.) Then, after typing the trigger, you should first
type a single category character to narrow down the list of candidates to a
manageable number:

- For IPA vowels and consonants: the Latin alphabet character that most closely
  resembles the IPA character (e.g., `a` for `ɐ, ɒ, ɑ` and `æ`, `b` for `β,
  ɓ`and `ʙ`, etc.) Characters based on the glottal stop `ʔ` use `?` as the
  category character.
- For Clicks: `|` (pipe).
- Diacritics: `'` (apostrophe).
- For superscripts: `^` (circumflex).
- For subscripts: `_` (underscore).

After typing the category character, the list of possible completions should be
sufficiently small to be able to locate the character with `M-n` and `M-p`, but
it is of course possible to type further characters or `TAB` to narrow down the
list further.

You can customise the list of symbols, the description strings and even the
category characters by modifying the variable `company-ipa-symbol-list-basic`.
See the doc string of that variable for details.

Note that the category character can be longer than a single character. This can
be used to make some characters easily accessible. For example, if you set the
category character for `æ` to `ae`, you can select this character by typing the
trigger prefix followed by `ae` and then `RET`.
