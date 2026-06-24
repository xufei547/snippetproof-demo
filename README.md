# SnippetProof demo

![examples](https://pageindex.dev/api/badge/xufei547/snippetproof-demo)

This repo demonstrates [SnippetProof](https://github.com/xufei547/snippetproof) catching a
broken code example in CI. **The failing check on this repo is intentional** — SnippetProof
ran the two examples below and flagged the broken one, with an inline annotation on the exact line.

## A working example

```js
const nums = [1, 2, 3, 4];
const total = nums.reduce((sum, n) => sum + n, 0);
console.log("total:", total); // -> total: 10
```

## A broken example (SnippetProof catches this)

```js
const name = "world";
// `toUpperCaseStr` is not a real String method — this example no longer runs.
console.log("HELLO " + name.toUpperCaseStr());
```

When you push, the SnippetProof check runs both examples, passes the first, and **fails the
build on the second** (`TypeError: name.toUpperCaseStr is not a function`) — exactly the kind of
silent doc rot it's built to catch.
