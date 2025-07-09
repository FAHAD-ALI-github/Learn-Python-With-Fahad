
# 📘 Learn Python with Fahad

Welcome to **LearnPythonWithFahad** – a complete and practical guide to learning Python programming from scratch to advanced concepts.

🌐 **Live link**: [Click to View](https://fahad-ali-github.github.io/Learn-Python-With-Fahad/intro.html)  


---

## 📖 What This Book Covers

This book is designed for:

- 🧑‍💻 **Beginners** starting their coding journey  
- 👩‍🏫 **Intermediate learners** looking to strengthen core skills  
- 🧠 **Advanced coders** exploring Python’s real-world applications  

Each chapter includes clear explanations, examples, and interactive code so you can learn by doing.

---

## 🚀 How to Run Locally

If you'd like to build the book yourself:

### Step 1: Clone the repository:
   ```bash
   git clone https://github.com/FAHAD-ALI-github/learn-python-with-fahad.git
   cd learn-python-with-fahad
   ```

### **Install Jupyter Book** (if not installed):
   ```bash
   pip install -U jupyter-book
   ```

### Step 2: Create Jupyter Book Configuration

Create a `_config.yml` file in the root directory:

```yaml
# Book settings
title: Python Core Concepts
author: FAHAD-ALI-github
logo: logo.png  # Optional: Add your logo

# Force re-execution of notebooks on each build
execute:
  execute_notebooks: force

# Define the name of the latex output file for PDF builds
latex:
  latex_documents:
    targetname: book.tex

# Add a bibtex file so that we can create citations
bibtex_bibfiles:
  - references.bib  # Optional

# Information about where the book exists on the web
repository:
  url: https://github.com/FAHAD-ALI-github/PYTHON_CORE_notebooks
  path_to_book: docs
  branch: main

# Add GitHub buttons to your book
html:
  use_issues_button: true
  use_repository_button: true
  use_edit_page_button: true
```

### Step 3: Create Table of Contents

Create a `_toc.yml` file:

```yaml
# Table of contents
# Learn more at https://jupyterbook.org/customize/toc.html

format: jb-book
root: intro
chapters:
- file: day1_Introduction
- file: day2_data_structures
- file: day3_operators_if_else_loops
- file: day4_functions
- file: day5_OOP_part1
- file: day6_OOP_part2
```

### Step 4: Create Introduction Page

Create an `intro.md` file:

```markdown
# Python Core Concepts

Welcome to the Python Core Concepts learning journey! This interactive book covers fundamental Python programming concepts through hands-on Jupyter notebooks.

## What You'll Learn

- Python basics and syntax
- Data structures (lists, dictionaries, tuples, sets)
- Control flow (conditionals and loops)
- Functions and modular programming
- Object-oriented programming (OOP)

## How to Use This Book

Each chapter is a Jupyter notebook that you can run interactively. Click on any chapter to get started!

## Getting Started

If you're new to Python, start with **Day 1: Introduction** and work your way through each chapter sequentially.

Happy coding! 🐍
```

### Step 5: Build the Book

```bash
# Build the book
jupyter-book build .

# Or if you want to clean build
jupyter-book clean .
jupyter-book build .
```

### Step 6: Deploy to GitHub Pages

#### Option A: Using GitHub Actions (Recommended)

1. Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy Jupyter Book

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  deploy-book:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Set up Python 3.9
      uses: actions/setup-python@v4
      with:
        python-version: 3.9

    - name: Install dependencies
      run: |
        pip install jupyter-book

    - name: Build the book
      run: |
        jupyter-book build .

    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      if: github.ref == 'refs/heads/main'
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./_build/html
```

2. Push changes to GitHub:

```bash
git add .
git commit -m "Add Jupyter Book configuration"
git push origin main
```

3. Enable GitHub Pages:
   - Go to your repository settings
   - Navigate to "Pages" section
   - Set source to "Deploy from a branch"
   - Select "gh-pages" branch
   - Click "Save"

#### Option B: Manual Deployment

```bash
# Install ghp-import
pip install ghp-import

# Build the book
jupyter-book build .

# Deploy to gh-pages branch
ghp-import -n -p -f _build/html
```

### Step 7: Access Your Website

Your Jupyter Book will be available at:
```
https://FAHAD-ALI-github.github.io/PYTHON_CORE_notebooks/
```

### 🔧 Customization Options

#### Adding Interactive Elements

Add to `_config.yml`:

```yaml
# Enable interactive widgets
execute:
  execute_notebooks: cache

# Add launch buttons
launch_buttons:
  notebook_interface: classic
  binderhub_url: https://mybinder.org
  colab_url: https://colab.research.google.com
  thebe: true
```

#### Styling

Create `_static/custom.css` for custom styling:

```css
/* Custom styles for your book */
.bd-main .bd-content .bd-article-container {
  max-width: 60rem;
}

/* Custom color scheme */
:root {
  --pst-color-primary: #2196F3;
  --pst-color-secondary: #FFC107;
}
```

#### Add Logo

1. Add your logo image to the root directory
2. Update `_config.yml`:

```yaml
logo: your-logo.png
```

### 🚀 Advanced Features

#### Enable Comments

Add to `_config.yml`:

```yaml
html:
  comments:
    hypothesis: true
    # OR
    utterances:
      repo: "FAHAD-ALI-github/PYTHON_CORE_notebooks"
```

#### Add Search

```yaml
html:
  use_fullscreen_button: true
  use_repository_button: true
  use_issues_button: true
  use_edit_page_button: true
  use_download_button: true
  
sphinx:
  extra_extensions:
    - sphinx_search.extension
```

### 📱 Mobile Responsive

The generated website is automatically mobile-responsive and includes:
- Responsive navigation
- Touch-friendly interface
- Optimized for all screen sizes

### 🔄 Updating the Website

To update your website:

1. Make changes to your notebooks or configuration
2. Commit and push to GitHub
3. GitHub Actions will automatically rebuild and deploy

### 🛠️ Troubleshooting

#### Common Issues:

1. **Build fails**: Check that all notebook files are valid and can execute
2. **Missing dependencies**: Ensure all required packages are installed
3. **GitHub Pages not updating**: Check the Actions tab for deployment status

#### Debug Commands:

```bash
# Check book structure
jupyter-book toc --help

# Validate configuration
jupyter-book config sphinx .

# Clean build
jupyter-book clean . --all
```


### 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test the book build locally
5. Submit a pull request



**Happy Learning!** 🐍✨

For questions or support, please open an issue in this repository.
