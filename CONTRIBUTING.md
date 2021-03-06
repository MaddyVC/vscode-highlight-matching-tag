# Contributing to VSCode Highlight Matching Tag

## Submitting a bug report/question/feature request

Github [issues](https://github.com/vincaslt/vscode-highlight-matching-tag/issues) is the best place to submit feature requests, bug reports or ask questions. To get best help or avoid the issue being rejected, please make sure that:

* you have provided detailed description of the issue/request,
* you support the issue with relevant code examples and/or screenshots,
* you have read the documentation on the plugin's [github page](https://github.com/vincaslt/vscode-highlight-matching-tag#vscode-highlight-matching-tag) first.

## How Can I Contribute?

Contributions in the following areas are welcome:

* Bug reports
* Enhancement ideas
* Feature requests
* Writing code

## Writing code

If you want to help with some coding tasks, you're welcome to look for unsolved bug reports or enhancements in the github issues. If you decide you want to take on the task, please __write a comment__ under the issue, then fork a clone of the repository, and submit a pull request when ready.

To ensure your code will get merged please make sure that:

* your code is reasonably clean and works
* your code has unit tests if needed
* your pull request references the issue you're solving

### Plugin's code

The plugin uses [typescript](https://www.typescriptlang.org).
The plugin uses [yarn](https://yarnpkg.com/) package manager, once installed, just run: `yarn` to pull the dependencies.
The unit tests are run when creating a pull request, but you can run them with `yarn test` or from vscode.

Following is a short description of the different parts of plugin and how they work.

#### Commands

The plugin has a few [commands](https://github.com/vincaslt/vscode-highlight-matching-tag#commands). The functions implementing them are under `commands.ts` file.

#### Configuration

Different configuration options are declared in `package.json` under `contributes`. Any new options must be documented and typed. They should be accesed from `Configuration` instance, which is declared in `configuration.ts`. Configuration object supports migrations when some configuration options need to be forcibly removed or renamed. It will also be updated every time the user's configuration file has changed.

#### Lexer, Parser, Matcher and Styler

__Lexer__ is a generic syntax declaration, that should resolve any code into tokens describing the code.
__Parser__ uses tokens generated by the lexer to build a structure that represents tags in code. It returns an array of tag pairs as found in the code reading from top to bottom. This structure is basis for all extension's functionality.
__Matcher__ performs matching tag search using the structure generated by the parser.
__Styled__ applies styling to a pair of tags.

