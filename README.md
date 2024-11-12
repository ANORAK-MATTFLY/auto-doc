# Code Documentation Generator GitHub Action

![GitHub release (latest by date)](https://img.shields.io/github/v/release/username/auto-doc-generator-action)  
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/username/auto-doc-generator-action/Documentation%20Generator)  
![GitHub License](https://img.shields.io/github/license/username/auto-doc-generator-action)

This GitHub Action automates the process of generating code documentation whenever a commit, push, or pull request is made. By seamlessly integrating with your repository, this action ensures that your code documentation is always up-to-date, enhancing code quality and consistency.

## ✨ Features

- **Automated Documentation**: Generates code documentation at every commit, push, or pull request, ensuring it’s always aligned with your codebase.
- **Customizable Documentation Output**: Configure documentation style, output format, and language preferences as needed.
- **Supports Multiple Languages**: Works with popular programming languages like Python, JavaScript, and more.
- **Fast and Efficient**: Uses a highly optimized model trained on a vast dataset of high-quality code documentation.

## 🚀 Usage

To use this GitHub Action in your repository, follow these steps:

1. **Create a Workflow File**:  
   Add a new file under `.github/workflows` directory in your repository, for example `.github/workflows/generate-docs.yml`.

2. **Add the Action Configuration**:

   ```yaml
   name: Generate Documentation

   on:
     push:
       branches:
         - main
     pull_request:
       branches:
         - main
     workflow_dispatch:

   jobs:
     generate-docs:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout code
           uses: actions/checkout@v2

         - name: Run Documentation Generator
           uses: username/auto-doc-generator-action@v1
           with:
             output-directory: docs

         - name: Commit and Push Documentation
           env:
             GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
           run: |
             git config --global user.name "github-actions[bot]"
             git config --global user.email "41898282+github-actions[bot]@users.noreply.github.com"
             git add docs/
             git commit -m "Auto-generate documentation"
             git push
   ```

3. **Customize Input Parameters**:  
   - **`format`**: Specify the output format (`markdown`, `html`, etc.).
   - **`language`**: Define the programming language used in the project.
   - **`output-directory`**: Directory where documentation files will be generated (e.g., `docs`).

## 🔧 Inputs

- **`format`** *(required)*: Format for the generated documentation (e.g., `markdown`, `html`).
- **`language`** *(required)*: Specify the programming language for the codebase (e.g., `python`, `javascript`).
- **`output-directory`** *(optional)*: Directory to save the generated documentation. Default is `docs`.

## 📂 Outputs

This action will create a directory (e.g., `docs`) in your repository, containing up-to-date code documentation in the specified format. You can configure your repository to use this directory for GitHub Pages or for easy access within your repository.

## 💡 Example Scenarios

- **For Python Projects**: Set `language` to `python` and `format` to `markdown` for code comments and docstrings in Markdown format.
- **For JavaScript Projects**: Set `language` to `javascript` and choose the output format accordingly.

## 🤝 Contributing

We welcome contributions! If you'd like to improve this GitHub Action, please submit a pull request or open an issue.

## 📝 License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.

--- 

This README provides clear instructions on setup, configuration, and usage, making it easy for users to integrate the action into their projects and keep their code documentation consistently up-to-date.
