[![MELPA](https://melpa.org/packages/leetcode-badge.svg)](https://melpa.org/#/leetcode)
# Introduction

LeetCode brings you offer, and now Emacs brings you LeetCode!

# Usage

![screencast](images/screencast.gif)

1. Execute `leetcode` command, and in problem list buffer:

| Keymap | Description                            |
|--------|----------------------------------------|
| n      | cursor move down                       |
| p      | cursor move up                         |
| l      | change prefer language                 |
| s      | filter problems by regex               |
| t      | filter problems by tag                 |
| d      | filter problems by difficulty          |
| /      | clear filters                          |
| g      | refresh without fetching from LeetCode |
| G      | refresh all data                       |
| RET    | show current problem description       |
| TAB    | view current problem description       |

More advanced navigation hotkeys can be found [here](#advanced-navigation).

2. Press `<RET>`, show problem description, move cursor to "solve it", press
   `<RET>` again, start coding!

3. After finishing your code, you can edit testcase and execute `leetcode-try`
   or execute `leetcode-submit`.

![leetcode-submit](images/leetcode-submit.png)

## Advanced Navigation

Here are some advanced navigation hotkeys that may be useful in problem list buffer:

| Keymap | Command                                    | Description                         |
|--------|--------------------------------------------|-------------------------------------|
| o      | `leetcode-show-current-problem`            | show/open the current problem       |
| O      | `leetcode-show-problem`                    | show/open a problem by id           |
| v      | `leetcode-view-current-problem`            | view the current problem            |
| V      | `leetcode-view-problem`                    | view a problem by id                |
| b      | `leetcode-show-current-problem-in-browser` | show the current problem in browser |
| B      | `leetcode-show-problem-in-browser`         | show a problem by id in browser     |
| c      | `leetcode-solve-current-problem`           | start coding the current problem    |
| C      | `leetcode-solve-problem`                   | start coding a problem by id        |

# Installation

- Vanilla Emacs: `package-install` it from melpa directly
- [Spacemacs](https://github.com/syl20bnr/spacemacs):
  [leetcode-emacs-layer](https://github.com/anmoljagetia/leetcode-emacs-layer)

LeetCode do not allow third party login, one workaround is restore LeetCode
session from local Firefox or Chrome cookies. By default, this package will
install a Python3 package called
[my\_cookies](https://github.com/kaiwk/my_cookies), or you can install it
manually: `pip3 install my_cookies`.

## Manually

1. Clone this repository and install all dependencies
2. Move it to your load-path
3. Require it in your emacs config

# Configuration

You can set your preferred LeetCode programming language and SQL by setting
`leetcode-prefer-language` and `leetcode-prefer-sql`:

```elisp
(setq leetcode-prefer-language "python3")
(setq leetcode-prefer-sql "mysql")
```

All supported languages can be found in variable
`leetcode--prefer-language-suffixes`.

You can save solution by setting `leetcode-save-solutions`:

```elisp
(setq leetcode-save-solutions t)
(setq leetcode-directory "~/leetcode")
```

You can specify code template by setting `leetcode-template-directory`:

```elisp
(setq leetcode-template-directory "~/leetcode/templates")
;; Any file with the lang as the basename in this directory will be taken
;; as the template for that lang.  For example, both file `cpp.cpp` and
;; file `cpp.cc` represents the template for cpp (so please avoid using
;; them at the same time).  In each template file, the string token
;; `leetcode-code-placeholder` will be replaced with the code snippet
;; that fetched from the leetcode when starting coding.
```

And a code template file would be like this:
```
#ifdef __APPLE__
#include "base.h"
#endif  // __APPLE__


$%CODE%$  // the default value for `leetcode-code-placeholder`
```

# Debug

Call `leetcode-toggle-debug`, log will output in `*leetcode-log*` buffer.

# Contributing

Please submit PR to develop branch.
