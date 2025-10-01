# Anderson Teala Blog

[![Deploy Workflow](https://github.com/AndersonTeala/andersonteala.com.br/actions/workflows/main.yml/badge.svg)](https://github.com/AndersonTeala/andersonteala.com.br/actions/workflows/main.yml)

This repository contains the source code for my personal blog, [andersonteala.com.br](https://andersonteala.com.br/).

## Features

- **Static Site Generation**: Built with [Hugo](https://gohugo.io/), a fast and flexible static site generator.
- **Clean and Responsive Design**: Uses the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.
- **Automated Deployments**: CI/CD pipeline using [GitHub Actions](/.github/workflows/main.yml) to automatically deploy the site to an server via SSH/rsync on every push to the `main` branch.
- **Interactive Comments**: Comment system powered by [Utterances](https://utteranc.es/).

## Built With

- [Hugo](https://gohugo.io/)
- [PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)
- [GitHub Actions](https://github.com/features/actions)
- [Utterances](https://utteranc.es/)

## Getting Started

To run this project locally, you will need to have [Hugo](https://gohugo.io/getting-started/installing/) installed.

1.  **Clone the repository:**

    Since this repository uses a git submodule for the theme, you can clone it recursively:
    ```bash
    git clone --recurse-submodules https://github.com/AndersonTeala/andersonteala.com.br.git
    ```
    If you have already cloned the repository without the `--recurse-submodules` flag, you can initialize the submodule by running:
    ```bash
    git submodule update --init --recursive
    ```

2.  **Run the Hugo server:**

    Navigate to the project directory and start the local server:
    ```bash
    cd andersonteala.com.br
    hugo server -D
    ```
    The `-D` flag includes posts marked as drafts. Your site will be available at `http://localhost:1313/`.

## License

This project is open source. You can choose a license that fits your needs, such as the [MIT License](https://opensource.org/licenses/MIT).
