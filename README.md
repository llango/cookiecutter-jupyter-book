# Cookiecutter Jupyter Book

<p align="center">
  <img src="{{cookiecutter.book_slug}}/{{cookiecutter.book_slug}}/images/logo.png" width="400">
</p>

一个用来创建 [Jupyter Book](https://jupyterbook.org/intro.html)的 cookiecutter模板，可以从 [这里](https://executablebooks.github.io/cookiecutter-jupyter-book/)查看cookiecutter-jupyer-book模板的效果。

## 模板

通过 cookiecutter 创建的cookiecutter模板包括如下文件:

```
my_book
├── .github
│   └── workflows
│       └── deploy.yml
├── CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── my_book
│   ├── _config.yml
│   ├── _toc.yml
│   ├── preface
|         ├──index.md
|         ├──content.md
│   ├── chapter0
|         ├──markdown.md
│   ├── chapter1
|         ├──notebooks.ipynb
│   ├── chapter2
|         ├──markdown-notebooks.md
│   ├── images
|         ├──logo.png
│   ├── static
|         ├──styles.css
│   └── references.bib
├── README.md
└── requirements.txt
└── notebooks
```

## 使用方式

1. 安装 [Cookiecutter](https://github.com/cookiecutter/cookiecutter/tree/1.7.2) :

```bash
$ pip install -U cookiecutter jupyter-book
```

2. 使用 `cookiecutter-jupyter-book` 来生成jupyer-book图书模板。

```bash
$ cookiecutter https://github.com/llango/cookiecutter-jupyter-book.git

author_name [凉葱落]: llango
github_username [llango]:
book_name [Jupyter 图书]:
book_slug [Jupyter_book]:
book_short_description [使用cookie创建一个简单的jupyter图书。该语句用来描述该书情况。]: 我的 Jupyter Book!
version ['0.1.0']:
Select open_source_license:
1 - MIT license
2 - BSD license
3 - Apache Software License 2.0
4 - CC BY 4.0
5 - CC BY-SA 4.0
6 - None
Choose from 1, 2, 3, 4, 5, 6 [1]:
Select include_ci:
1 - github
2 - gitlab
3 - no
Choose from 1, 2, 3 [1]:
```

3. 根据`requirements.txt`文件安装Jupyter Book 包依赖(推荐在虚拟环境中进行, 比如：使用conda [conda](https://docs.conda.io/en/latest/)):

```bash
# 推荐创建新的环境来进行操作
$ conda create --name mybook python=3.10 -y
$ conda activate mybook
```

```bash
$ cd my_book
$ pip install -r requirements.txt
```

4. 构建图书

```bash
$ jupyter-book build my_book/
```

5. 查看图书 `my_book/_build/html/index.html`。

6. 通过添加更多内容来编辑您的书，更新`my_book/_toc.yml`中的目录表。和/或编辑配置文件`my_book/_config.yml`。请参阅[Jupyter Book文档](https://jupyterbook.org/intro.html)了解有关定制图书的更多信息。

7. `cookecutter-jupyter-book`可选地附带CI工作流文件，以帮助您轻松地在线部署您的书籍。
   1. 确保你的书按照预期在本地构建(' jupyter-book build my_book/ ')，并且你已经更新了`requirements.txt`文件，以包含构建你的书所需的任何其他软件包;
   2. 创建一个新的公共[GitHub存储库](https://github.com/new)来托管你的书;
   3. 推送你当地的书(包括`.github`隐藏目录)到你的github仓库。有很多方法可以做到这一点，例如:
   ```bash
   $ git init
   $ git add。
   $ git commit -m "first commit"
   $ git remote add origin git@github.com:<user>/<repository-name>.git
   $ git push -u origin main
   ```
   4. cookiecutter提供的GitHub Actions工作流(`my_book/.gitHub/workflows/deploy.yml`)会在推送后自动将您的图书部署到存储库的`gh-pages`分支。它通常在几分钟后可在`https://<user>.github.io/<myonlinebook>/`。你可能需要去你的存储库的`Settings`选项卡，在`**GitHub Pages**`标题下，从`**Source**`下拉列表中选择`gh-pages branch`。有关在线部署图书的其他方法，请参阅参阅[Jupyter book文档](https://jupyterbook.org/intro.html)。

   >注意:默认情况下，这个cookecutter包含的GitHub Actions工作流文件使用Ubuntu和Python 3.10构建本书。你可以在`.github/workflows/deploy`文件中修改构建的OS/Python版本。

   >阅读更多关于GitHub Pages和Jupyter Book[在这里](https://jupyterbook.org/publish/gh-pages.html#automatically-host-your-book-with-github-actions)，或使用GitLab Pages[在这里](https://docs.gitlab.com/ee/user/project/pages/getting_started/pages_from_scratch.html)。

## 声明

该模板基于 [Cookiecutter project](https://github.com/cookiecutter/cookiecutter) 和 [Jupyter Book project](https://github.com/executablebooks/jupyter-book)创建的。
