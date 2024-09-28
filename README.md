[![构建状态](https://travis-ci.org/QubesOS/qubesos.github.io.svg?branch=master)](https://travis-ci.org/QubesOS/qubesos.github.io)

# Qubes OS 官方网站

规范网址: https://www.qubes-os.org

这是 [Qubes OS项目](https://github.com/QubesOS) 网站的主要存储库。Qubes 是一款面向安全的开源个人电脑操作系统。它使用虚拟化来实现 [分区安全](https://www.qubes-os.org/intro/)并支持 Linux 和 Windows 虚拟环境。

--------------------------------------------------------------------------------

## 支持的内容

此存储库由一个 [Jekyll](https://jekyllrb.com/) 站点和多个
Git 内容子模块组成：

 - `qubes-doc` (官方文档)
 - `qubes-attachment` (二进制文件与图像)
 - `qubes-hcl` （由 YAML 版本的 `qubes-hcl-report` 生成的硬件兼容性列表 (HCL) 报告）
 - `qubes-posts` (新闻和博客文章)

## 指导

### 容器详情

这些说明已在 Fedora 33 qube 上进行了测试。Podman 在 Debian 10 中不可用。您必须使用基于 Fedora 的机器或 Debian 11。

1. 安装 `podman` 和 `podman-compose`。

2. 启动 Podman 守护进程，例如：

$ sudo systemctl start podman

3. 克隆此 repo（包括所有子模块）并输入：

$ git clone --recursive https://github.com/QubesOS/qubesos.github.io.git
$ cd qubesos.github.io/

4. 启动并运行网站：

$ sudo make

5. 打开浏览器并导航至：

http://127.0.0.1:4000/

### 其他文档

 - 要更新子模块，请使用 `git submodule foreach git pull --tags`.
 - 有关 RubyGems 的故障排除，请参阅: <http://guides.rubygems.org/>
 - 有关使用 Jekyll 进行故障排除，请参阅: <https://jekyllrb.com/docs/home/>
 - 有关使用 GitHub pages 和 Jekyll 进行故障排除的信息，请参阅:
   <https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/>
 - 要在 Git 接收后钩子上运行，请使用:

        GIT_REPO=/usr/home/git/repositories/www.qubes-os.org.git
        GIT_CLONE=/usr/home/git/tmp/www.qubes-os.org
        PUBLIC_WWW=/usr/local/www/qubes-os.org/www/

        if [ ! -d "$GIT_CLONE" ]; then
            git clone --recursive $GIT_REPO $GIT_CLONE
        else
            git --work-tree=$GIT_CLONE --git-dir=$GIT_CLONE/.git pull
        fi
        cd $GIT_CLONE && jekyll build -s $GIT_CLONE -d $PUBLIC_WWW

        find $PUBLIC_WWW -type f -print0 | xargs -0 chmod 666
        find $PUBLIC_WWW -type d -print0 | xargs -0 chmod 777

        exit

## 技术文档

若要对文档做出贡献，请参阅[如何编辑文档](https://www.qubes-os.org/doc/how-to-edit-the-documentation).

### 依赖项和第三方文档

- [Jekyll 文档](http://jekyllrb.com/docs/) - 模板渲染
引擎
- [Bootstrap 3](http://getbootstrap.com) - 样式和 CSS 结构
- [FontAwesome](http://fontawesome.io) - 整个网站的图标字体
- [jQuery 1.7](http://api.jquery.com) - javascript 帮助库
- [jQuery ToC MD 生成器](https://github.com/dafi/tocmd-generator) - 渲染
文档部分上的标题菜单

## 弃用的文档

- [qubes-os.org-3.2-EOL.zip](https://github.com/QubesOS/qubesos.github.io/releases/download/3.2-EOL/qubes-os.org-3.2-EOL.zip)
包含 [Qubes OS 3.2 达到 EOL](https://www.qubes-os.org/news/2019/03/28/qubes-3-2-has-reached-eol/) 时 Qubes 网站的状态。
您只需使用 Web 浏览器即可浏览它。
- 这是 [Qubes OS 3.2 达到 EOL](https://www.qubes-os.org/news/2019/03/28/qubes-3-2-has-reached-eol/) 时此 repo 和所有子模块的状态：
- https://github.com/QubesOS/qubesos.github.io/tree/3.2-EOL
- https://github.com/QubesOS/qubes-doc/tree/3.2-EOL
- https://github.com/QubesOS/qubes-hcl/tree/3.2-EOL
- https://github.com/QubesOS/qubes-posts/tree/3.2-EOL
- https://github.com/QubesOS/qubes-attachment/tree/3.2-EOL

