| Pattern                  | Common symptom                          | Typical fix                                        |
| ------------------------ | --------------------------------------- | -------------------------------------------------- |
| Off-by-one               | One extra/one missing iteration         | Recheck `<` vs `<=`, `>` vs `>=`                   |
| Fencepost                | Counting boundaries instead of elements | Decide whether you're counting intervals or points |
| State update order       | Value is correct one iteration late     | Check before vs after update                       |
| Aliasing                 | Two variables change together           | Copy instead of reference                          |
| Mutation while iterating | Items skipped or duplicated             | Iterate over a copy or collect changes first       |
| Empty input              | Code crashes on `[]`                    | Add base case                                      |
| Single element           | Works for many cases but fails on one   | Test `n = 1`                                       |
