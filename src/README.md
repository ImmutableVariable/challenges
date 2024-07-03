# Coding Challenges

This is a compilation of my programming challenges along with some solutions in multiple languages. I try to provide a acceptable solution for each problem but I am not perfect, feel free to add better or your own solutions by creating a pull request. The challenges are not in any particular order, so feel free to jump around and try to solve them. All challenges are language agnostic, so you can solve them in any language you like.

## These challenges are for you if:
- You are a beginner/intermediate programmer and want to practice.
- You want to experiment with a new language.

## General Steps to Add a New Challenge
You can also add new challenges! However, please follow the format of the existing challenges.

- Fork the repository
- if you want to add a new challenge called "New Challenge", you would create a folder called `challenge{number}`
- Inside the folder, you would create a `README.md` file with the challenge description
    - you will put the challenge name as the title with a # {name (New Challenge)}
    - you will put the challenge description as the first paragraph
    - you will put the example test case/output as a code block
- You would also create an `answers.md` file with the solutions
    - you will put the solutions in this general format
        - \#\# {Language}
        - \`\`\`{language}
        - {code}
        - \`\`\`
- Add the challenge to the `SUMMARY.md` file
- Create a pull request

### Special Instructions for Rust Solutions
MdBook features a runtime for the builtin code blocks, please include the valid code to run the test/code in the code block. You can use the following syntax to run the code block:

```bash
# fn main() { // # is used to hide this line
    let x = 5;
    let y = 6;

    println!("{}", x + y);
# } // # is used to hide this line
```

Therefore, all the end user will see is

```rust
#fn main() {
    let x = 5;
    let y = 6;

    println!("{}", x + y);
#}
```

However, they can click in the top right corner and run the code on their machine. More info [here](https://rust-lang.github.io/mdBook/format/mdbook.html).

(CODE SOURCE: [mdBook](https://rust-lang.github.io/mdBook/format/mdbook.html))

## License

This book is licensed under the MIT License. See here for more details: [LICENSE](https://raw.githubusercontent.com/ImmutableVariable/Coding-Challenges/main/LICENSE)
