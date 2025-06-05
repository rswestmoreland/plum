# 🌸 Plum — A Safer, Cleaner Perl

**Plum** is a modernized Perl-based language with an emphasis on clarity, scientific utility, and safe concurrency. It begins life as a Perl module (`Plum.pm`) that enforces cleaner syntax and adds built-in utility functions, and it is designed to evolve into a standalone compiled language.

---

## ✨ Features

- ✅ **Clean Syntax Defaults**
  - `print` adds newline automatically (like Python’s `print` or Perl’s `say`)
  - All loops must use `foreach` — bare `for (...)` is disallowed
  - Tabs are disallowed; enforce 2-space indentation
  - Opening braces must be on the same line as conditionals

- 🧠 **Dangerous Features Disabled**
  - `eval` (block and string form) — ❌ disallowed
  - `goto` — ❌ disallowed
  - Symbolic references (`$$var`) — ❌ disallowed
  - `local` — ❌ disallowed (use `my`)
  - `require` — ❌ disallowed (use `use` instead)

- 🔢 **Built-in Utilities**
  - `print(...)` → newline-terminated output
  - `sum(@values)` → simple sum
  - `spawn(sub { ... })` → fork-based parallelization

- 📏 **Static Code Formatting Warnings**
  - Tabs → ❌ use 2 spaces
  - Indent levels must be multiples of 2
  - Braces must appear on same line as conditionals or function headers

---

## 📦 Installing Plum

1. Copy `Plum.pm` into your Perl project (`lib/Plum.pm`)
2. In your Perl file:

```perl
use lib 'lib';    # if needed
use Plum;
