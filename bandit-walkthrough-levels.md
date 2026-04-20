
````markdown
# OverTheWire Bandit Walkthrough 

This walkthrough explains what to type, why it works, and alternative ways to achieve the same result.

---

## Level 1

```bash
cat readme
````

Password:

```
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

Explanation:

* `cat` is used to read file content.
* `readme` contains the password.

Alternative methods:

```bash
less readme
more readme
head readme
```

* `less` / `more` → interactive viewing
* `head` → shows first few lines

---

## Level 2

```bash
cat ./-
```

Password:

```
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

Explanation:

* `-` is normally treated as stdin.
* `./-` forces it to be treated as a file in the current directory.

Alternative methods:

```bash
cat -- -
less ./-
```

* `--` stops option parsing

---

## Level 3

```bash
cat "./--spaces in this filename--"
```

Password:

```
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

Explanation:

* Filename contains spaces.
* Quotes ensure it's treated as a single argument.

Alternative methods:

```bash
cat ./--spaces\ in\ this\ filename--
less "./--spaces in this filename--"
```

* `\` escapes spaces

---

## Level 4

```bash
ls -a
cat ...Hiding-From-You
```

Password:

```
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

Explanation:

* `ls -a` shows hidden files (starting with `.`).
* The hidden file contains the password.

Alternative methods:

```bash
ls -la
find . -name "...Hiding-From-You"
less ...Hiding-From-You
```

* `ls -la` → detailed listing
* `find` → locate hidden files

---

## Level 5

```bash
cat ./-file07
```

Password:

```
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

Explanation:

* Filename starts with `-`, which can be misinterpreted as an option.
* `./` ensures it is treated as a file.

Alternative methods:

```bash
cat -- -file07
less ./-file07
```

* `--` stops option parsing

---

## Level 6

```bash
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
```

Password:

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

Explanation:

* `find .` → search current directory
* `-type f` → only files
* `-size 1033c` → file size is 1033 bytes
* `! -executable` → exclude executable files

Alternative methods:

```bash
find . -type f -size 1033c | xargs ls -l
find . -type f -size 1033c -exec cat {} \;
```

* `xargs` → passes results as arguments
* `-exec` → runs command on each result

Then:

```bash
cat ./maybehere07/.file2
```

---

## Key Takeaways

* Use `ls -a` to reveal hidden files
* Use `cat`, `less`, or `more` to read files
* Handle tricky filenames:

  * spaces → quotes or `\`
  * starting with `-` → `./` or `--`
* Use `find` for precise searching

---


