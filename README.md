# Coding Challenges

A compilation of my programming challenges and solutions. They are language agnostic which means most can be solved in any programming language. Each challenge is divided into a folder, called challenge{number}, and contains a README.md file with the problem description and a solution file, called answers.md, with the solution code. Feel free to contribute with your own solutions, add new challenges, or improve the existing ones by submitting a pull request. You can also suggest challenges by opening an issue with the label "challenge suggestion".

## These challenges are for you if:
- You are a beginner/intermediate programmer and want to practice.
- You want to experiment with a new language.

## Contributing
Please see the [CONTRIBUTING.md](/CONTRIBUTING.md) AND the text below for more information on how to contribute.

### General Steps to Add a New Challenge
Please follow the format of the existing challenges.

- Fork the repository
- if you want to add a new challenge called "New Challenge", you would create a folder called `challenge{number}`
- Inside the folder, you would create a `README.md` file with the challenge description
    - you will put the challenge name as the title with a # {name (New Challenge)}
    - you will put the challenge description as the first paragraph
    - you will put the example test case /output as a code block
- You would also create an `answers.md` file with the solutions
    - you will put the solutions in this general format
        - \#\# {Language}
        - \`\`\`{language}
        - {code}
        - \`\`\`
- Add the challenge to the `SUMMARY.md` file with the correct format.
- Create a pull request


#### Special Instructions for Rust (And Python) Solutions
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
    let x = 5;
    let y = 6;

    println!("{}", x + y);
```

In python, you will replace `rust` with `python` and replace the `#` with a `~` and it will output similarly.

However, they can click in the top right corner and run the code on their machine. More info [here](https://rust-lang.github.io/mdBook/format/mdbook.html).

(CODE SOURCE: [mdBook](https://rust-lang.github.io/mdBook/format/mdbook.html))

## License

This book is licensed under the MIT License. See here for more details: [LICENSE](https://raw.githubusercontent.com/ImmutableVariable/Coding-Challenges/main/LICENSE)
