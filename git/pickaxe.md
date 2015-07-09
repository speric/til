Find any commit which introduces or removes a string from anywhere in it's commit:

```
$ git log -S "Elixir" --pretty=oneline --abbrev-commit
```

Outputs the following:

```
6849328 Elixir README
e49ed22 Elixir: pattern matching & default values
```

Note, it's not the commit message that's important, but the commit
itself (note "Elixir Learning" in the diff below):

```
$ git show 6849328

commit 684932824187d7af2479ca9cbb86b9c3865093b1
Author: Eric Farkas <eric@prudentiadigital.com>
Date:   Thu Jul 9 09:37:03 2015 -0400

    Elixir README

diff --git a/elixir/README.md b/elixir/README.md
new file mode 100644
index 0000000..078a0c1
--- /dev/null
+++ b/elixir/README.md
@@ -0,0 +1 @@
+### Elixir Learning
```

Reference:

http://www.philandstuff.com/2014/02/09/git-pickaxe.html
