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

---

## 🚀 Usage Example

use Plum;

foreach my $item (1..3) {
  print "Item $item";
}

my $total = sum(2, 4, 6);
print "Total is $total";

my $pid = spawn(sub {
  print "Running in parallel!";
});
waitpid($pid, 0);

---

## 🧱 How It Works

Plum uses Filter::Simple to inspect source code before compilation, catching bad syntax like:

for my $x (...)     # ❌ use foreach
eval { ... }        # ❌ disallowed
goto LABEL;         # ❌ disallowed
$$var = ...         # ❌ disallowed symbolic ref
local $x = ...      # ❌ use 'my'
require Foo;        # ❌ use 'use'

It also reads the current source file during import() to check formatting:

| Rule              | Message                                                         |
| ----------------- | --------------------------------------------------------------- |
| Tab characters    | `Plum format warning: use spaces, not tabs`                     |
| Misaligned indent | `Plum indent warning: indent should be multiple of 2 spaces`    |
| Misplaced braces  | `Plum format warning: opening brace should be on the same line` |

---

## ⚠ Limitations

Source filtering is static and may not catch dynamic code (eval $string, etc.)
No AST-level enforcement (yet)
Not all formatting issues cause failure (warnings only for now)

---

## 🔮 Future Roadmap

✨ plumfmt — automatic formatter for Plum code
🧮 Built-in vector/matrix math utilities
🔐 Strong typing and type annotations (my Int $x)
🌐 Channel-based concurrency (like Go's goroutines)
🧪 Test suite for validating Plum compliance
🚀 Compiled Plum runtime (a forked Perl interpreter)

---

## 🤝 Contributing

Want to help shape Plum? File issues or submit PRs to:

    Add new language features
    Improve static checking
    Add useful standard library functions

---

## 📄 License

MIT License (c) 2025 Richard Westmoreland and contributors
