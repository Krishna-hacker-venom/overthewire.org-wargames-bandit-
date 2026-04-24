# OverTheWire Bandit Walkthrough (Levels 1–10)

This walkthrough explains commands, why they are used, and alternative approaches.

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

* `cat` reads file content.

Alternative:

```bash
less readme
more readme
```

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

* `-` is treated as stdin.
* `./-` forces it to be treated as a file.

Alternative:

```bash
cat -- -
less ./-
```

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

* Quotes handle spaces in filenames.

Alternative:

```bash
cat ./--spaces\ in\ this\ filename--
```

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

* `ls -a` shows hidden files.

Alternative:

```bash
ls -la
find . -name "...Hiding-From-You"
```

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

* Filename starts with `-`, treated as option.
* `./` fixes it.

Alternative:

```bash
cat -- -file07
```

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

* Finds file by size and type.

Alternative:

```bash
find . -type f -size 1033c -exec cat {} \;
```

---

## Level 7

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

Password:

```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

Explanation:

* Search entire system.
* `2>/dev/null` hides permission errors.

Alternative:

```bash
find / -size 33c 2>/dev/null | grep bandit7
```

---

## Level 8

```bash
grep "millionth" data.txt
```

Password:

```
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

Explanation:

* `grep` searches for text inside file.

Alternative:

```bash
cat data.txt | grep millionth
```

---

## Level 9

```bash
sort data.txt | uniq -u
```

Password:

```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

Explanation:

* `sort` organizes data.
* `uniq -u` shows unique lines.

Alternative:

```bash
uniq -u <(sort data.txt)
```

---

## Level 10

```bash
strings data.txt | grep "===="
```

Password:

```
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

Explanation:

* `strings` extracts readable text from binary files.
* `grep` filters useful lines.

Alternative:

```bash
strings data.txt | less
```

---

## Key Takeaways

* Use `cat`, `less` to read files
* Use `ls -a` for hidden files
* Use `find` for searching files
* Use `grep` for filtering text
* Use `sort` + `uniq` for data processing
* Handle tricky filenames with:

  * quotes `" "`
  * escape `\`
  * `./` or `--`

---

