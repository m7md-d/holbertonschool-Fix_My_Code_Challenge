# Challenge — fixed solutions

The fixed version of each task. The matching broken sources are in
[../0x00-Fix_My_Code_Challenge-main/](../0x00-Fix_My_Code_Challenge-main/).

## Tasks

Each task is independent — a separate language and a separate kind of bug.

| Task | File | Language | Bug | Fix |
|------|------|----------|-----|-----|
| 0 | [0-fizzbuzz.py](0-fizzbuzz.py) | Python | `if/elif` checked `% 3` before `% 3 and % 5`, so multiples of 15 printed `Fizz` and the `FizzBuzz` branch was unreachable | Test the `% 3 and % 5` case first |
| 1 | [1-print_square.js](1-print_square.js) | JavaScript | `parseInt(argv[2], 16)` read the size as hexadecimal | Parse in base 10 |
| 2 | [2-sort.rb](2-sort.rb) | Ruby | `result.insert(i - 1, i_arg)` inserted one slot too early (off-by-one), corrupting the sorted order | Insert at `i` |
| 3 | [3-user.py](3-user.py) | Python | Setter wrote to `self._password` (single underscore) instead of `__password`, and `is_valid_password` compared an upper-cased hash against a lower-cased one | Assign `__password` and compare with `.lower()` |
| 4 | [4-delete_dnodeint/delete_dnodeint_at_index.c](4-delete_dnodeint/delete_dnodeint_at_index.c) | C | Deleting a non-head node corrupted `prev` instead of relinking, and dereferenced `*head` after `free` (use-after-free) | Save the node, relink `prev->next`/`next->prev`, then free |

## Run it

The Python, JavaScript, and Ruby tasks are standalone scripts:

```bash
cd challenge
./0-fizzbuzz.py 89
./1-print_square.js 8
./2-sort.rb 9 8 7 6 5 4 3 2 1 0
./3-user.py
```

The C task ([4-delete_dnodeint/](4-delete_dnodeint/)) builds with a `main.c`
driver:

```bash
cd challenge/4-delete_dnodeint
gcc -Wall -Werror -Wextra -pedantic *.c -o delete_dnodeint
./delete_dnodeint
```
