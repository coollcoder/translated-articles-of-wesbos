# the original http://wesbos.com/javascript-modules/
##An Intro To Using npm and ES6 Modules for Front End Development
将npm 和ES6模块机制用在前端开发中的一些相关信息

- <b>A big thanks to bitHound for sponsoring my time to research and write this article. Check out their service, which provides continuous analysis and quality checks for both your front and back end JavaScript and its dependencies.</b>
####很感谢bitHound赞助我研究和撰写这篇文章。研究他们的提供的服务，他们的服务提供了持续的分析和质量的检查，在前端和后端的js和其相应的依赖。

####The JavaScript landscape is changing quickly and along with it the way that we work with dependencies in our websites and applications.
#### 伴随着JavaScript世界日新月异的变化，我和我们的网站以及应用中的各种依赖文件打交道的方式也在发生着变化

#### This post is for developers who are currently loading in their JavaScript via multiple script tags and finding that dependency management is becoming a little cumbersome as their webpages or applications start to grow.
#### 这篇博文，适合于那些仍然用多个script标签加载js，发现随着他们的网页数量和应用规模扩大，依赖管理将变得越来越麻烦

#### For a deep dive into everything the spec has to offer, as well as some great comparisons to CommonJS and AMD, check out Axel Rauschmayer’s Exploring ES6 book, particularly chapter 17.
#### 如果想要深入了解ES6模块规范内容，以及它和Commonjs和AMD的差别，请查看Axel Rauschmayer’s Exploring ES6 book，尤其适合第17章

#What are JavaScript Modules?
#### 什么是JavaScript的模块(组件)

####JavaScript modules allow us to chunk our code into separate files inside our project or to use open source modules that we can install via npm. Writing your code in modules helps with organization, maintenance, testing, and most importantly, dependency management.
#### `JavaScript modules`允许我们将代码成块的分离成文件到我们的项目中或者通过安装NPM`Node.js的模块依赖管理工具`来使用开源的模块.依靠模块编写代码时可以帮助你组织，维护，测试你的项目,更重要的是,`JavaScript modules`依赖管理.
