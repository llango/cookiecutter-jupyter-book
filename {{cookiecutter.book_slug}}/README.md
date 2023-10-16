# {{ cookiecutter.book_name }}
{{ cookiecutter.book_short_description }}
该图书使用 [Jupyter-book](https://jupyterbook.org/intro.html)构建。

## 命令

- 安装
```
pip install jupyter-book
```

在该项目目录，然后如下命令进行构建

- 构建
```
jupyter-book build docs
```

- 发布
```
ghp-import -n -p -f course-website/_build/html -m "提交信息"
```

如果ghp-import命令没有，可以使用如下命令进行安装
```
sudo apt install ghp-import
```

## 使用

### 构建图书

如果要构建{{ cookiecutter.book_name }} 图书, 你应当:

1. 克隆这仓库
2. 运行 `pip install -r requirements.txt` (推荐在一个虚拟环境中操作)
3. 编辑 `{{ cookiecutter.book_slug }}/` 目录下文件
4. 运行 `jupyter-book clean {{ cookiecutter.book_slug }}/` 移除已经构建的builds
5. 运行 `jupyter-book build {{ cookiecutter.book_slug }}/` 构建
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