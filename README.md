# C++ Rush Book

A book aimed at teaching fundamentals of C++ language quickly, without compromising on important details.

This project started as an incomplete blog post. I wanted to provide a quick start to the language, but found it difficult to condense all important concepts into a single blog. While typing it out, I felt this will be better presented as a short book.

This project is currently a WIP.

[SHARE YOUR THOUGHTS ON LICENSE](https://github.com/flyingcakes85/cpp-rush-book/discussions/1)

# Roadmap

- [ ] Complete basic topics - conditionals, loops, functions, pointers etc.
- [ ] Chapter on Strings
- [ ] Introduce structures
- [ ] Introduce Classes
      No plans of going into details of this right now. Focus will be on providing sufficient examples to make topics clear.
- [ ] Operator overloading
- [ ] Templates
- [ ] Introduction to Standard Template Library
- [ ] More topics? Feel free to share in [Discussions/Suggestions](https://github.com/flyingcakes85/cpp-rush-book/discussions/categories/suggestions)

## Contributing & Pull Requests

You can contribute by writing chapters, proofreading existiting chapters, adding more examples, rewriting sections etc. Please read CONTRIBUTING.md to know more. To see chapters requiring proof reading, [click here](https://github.com/flyingcakes85/cpp-rush-book/issues?q=is%3Aopen+is%3Aissue+label%3A%22proof+read%22).

## About The Template

The current template based on [wikiti/pandoc-book-template](https://github.com/wikiti/pandoc-book-template). This is only a temporary choice however. Right now focus is on content rather than formatting.

I will love to know if you have some good pandoc templates in mind. Share them in [Discussions/Suggestions](https://github.com/flyingcakes85/cpp-rush-book/discussions/categories/suggestions).

## Issues

I try to research topics before including them in the book. However, if you happen to find any errors, please bring it to my notice so that it can be fixed.

## Build

While this project is incomplete, I will not be regularly providing PDFs. It is easy to generate a PDF yourself.

### Dependencies

You need `pandoc` and basic Tex/LaTeX tools present on your system. On Arch Linux, you can install them via this command

```sh
sudo pacman -S texlive-latexextra pandoc
```

Other required packages will be pulled in as dependencies.

If using a different distro, you will probably be able to find these packages in the repos.

In addition, this project uses `make` as a build utility.

### Building PDF

Assuming you have the required dependencies, the following should be run at project root and it will place a PDF in `build/pdf/book.pdf`.

```sh
make pdf
```

## License

For now, this repository is licensed under MIT. However, I plan to change it to a different license.

[SHARE YOUR THOUGHTS ON LICENSE](https://github.com/flyingcakes85/cpp-rush-book/discussions/1)
