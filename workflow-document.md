# Document-writing guideline

To write a useful document, following parts are necessary:

+ Basic information
+ Usage
+ How to contribute

If it's a internal project, another part is needed.

+ How to deploy

README is a good place to store these parts. But if any of them is too long, just make it a independent part and link it in README.

Note: All the examples in this guideline are from [twitter/bootstrap](https://github.com/twbs/bootstrap)

## Basic infomation

Several sentences to describe the project.

> Bootstrap is a sleek, intuitive, and powerful front-end framework for faster and easier web development, created by [Mark Otto](https://twitter.com/mdo) and [Jacob Thornton](https://twitter.com/fat), and maintained by the [core team](https://github.com/orgs/twbs/people) with the massive support and involvement of the community.


## Usage

Or you can call it `Quick Start`. Several commands to have a try.

> Four quick start options are available:
> 
> - [Download the latest release](https://github.com/twbs/bootstrap/archive/v3.3.1.zip).
> - Clone the repo: `git clone https://github.com/twbs/bootstrap.git`.
> - Install with [Bower](http://bower.io): `bower install bootstrap`.
> - Install with [npm](https://www.npmjs.org): `npm install bootstrap`.

## How to contribute

The project is awesome, but how to join it?

> Please read through our [contributing guidelines](https://github.com/twbs/bootstrap/blob/master/CONTRIBUTING.md). Included are directions for opening issues, coding standards, and notes on development.

> Moreover, if your pull request contains JavaScript patches or features, you must include relevant unit tests. All HTML and CSS should conform to the [Code Guide](https://github.com/mdo/code-guide), maintained by [Mark Otto](https://github.com/mdo).

> Editor preferences are available in the [editor config](https://github.com/twbs/bootstrap/blob/master/.editorconfig) for easy use in common text editors. Read more and download plugins at <http://editorconfig.org>.

## How to deploy

For internal project, you should also write about deployment.

+ machine IP and path
+ how to deploy the project to there
+ how to start, stop, restart the server
+ where is the log file

Furthermore, the document should mention how to prepare the environment. You can just write it down, or use a Configure Mangement Tool to handle it, such as [ansible](http://www.ansible.com). The source code can tell the env setup procedure.


