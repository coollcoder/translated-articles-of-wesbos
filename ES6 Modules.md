# the original http://wesbos.com/javascript-modules/
## An Intro To Using npm and ES6 Modules for Front End Development
**将npm 和ES6模块机制用在前端开发中的一些相关信息**

  A big thanks to bitHound for sponsoring my time to research and write this article. Check out their service, which provides continuous analysis and quality checks for both your front and back end JavaScript and its dependencies.

  很感谢bitHound赞助我研究和撰写这篇文章。研究他们的提供的服务，他们的服务提供了持续的分析和质量的检查，在前端和后端的js和其相应的依赖。

  The JavaScript landscape is changing quickly and along with it the way that we work with dependencies in our websites and applications.

  伴随着JavaScript世界日新月异的变化，我和我们的网站以及应用中的各种依赖文件打交道的方式也在发生着变化

  This post is for developers who are currently loading in their JavaScript via multiple script tags and finding that dependency management is becoming a little cumbersome as their webpages or applications start to grow.

  这篇博文，适合于那些仍然用多个script标签加载js，发现随着他们的网页数量和应用规模扩大，依赖管理将变得越来越麻烦

  For a deep dive into everything the spec has to offer, as well as some great comparisons to CommonJS and AMD, check out Axel Rauschmayer’s Exploring ES6 book, particularly chapter 17.
  
  如果想要深入了解ES6模块规范内容，以及它和Commonjs和AMD的差别，请查看Axel Rauschmayer’s Exploring ES6 book，尤其适合第17章

## What are JavaScript Modules?
**什么是JavaScript的模块(组件)**

  JavaScript modules allow us to chunk our code into separate files inside our project or to use open source modules that we can install via npm. Writing your code in modules helps with organization, maintenance, testing, and most importantly, dependency management.

  `JavaScript modules`允许我们将代码成块的分离成文件到我们的项目中或者通过安装NPM`Node.js的模块依赖管理工具`来使用开源的模块。依靠模块编写代码时可以帮助你组织，维护，测试你的项目，更重要的是，`JavaScript modules`依赖管理。
  
  When we write JavaScript, it’s ideal if we can make modules that do one thing and one thing well. This separation allows us to pull in various modules only when we need them. Modules represent the core principle behind npm — when we need specific functionality, we can install the modules we need and load them into our application.
  
  当我们编写JavaScript代码时，如果我们能做出能完成一件事或者把事情完成得更棒的模块是理想的情况。而这种分离允许我们拉动(使用)这些模块仅当我们需要它们的时候。模块代表着NPM背后的核心原则 - 当我们需要特定的功能时,我们可以安装加载我们所需要的模块到我们的应用程序里。
  
  As time goes on, we’re seeing fewer large frameworks that do everything under the sun while seeing more small modules that do one thing and one thing well.
  
  随着时间的推移，我们可以在阳光下看见更少的用来完成很多事情的大框架但是出现了更多更小的只完成一件事或者优化一件事的小模块。
  
  For example, many of us learned jQuery. It included methods for doing absolutely everything from CSS manipulation to ajax calls. Now, many of us are migrating to libraries like React where often we need to pull in additional packages to perform tasks like ajax or routing.
  
  例如，大多数人都学过jQuery。jQuery涵盖了一切从操作css到调用ajax的方法。而如今，大多数人开始迁移到了像react(前端框架）这种库去。通常来说，在用react的时候，我们只需要将其他依赖包加载进来就可以执行任务了,像执行ajax和路由这种任务。

  This article will take a look at using npm and ES6 Modules. There are other registries (e.g. Bower) and other module loaders (e.g. CommonJS and AMD), but there are plenty of articles already on those topics.
  
  本文将介绍下使用NPM和ES6模块。还有其他登记的(如Bower)等模块加载器(例如CommonJS和AMD)，但是有很多文章已经针对这些议题。

  Whether you are doing Node or front end development, I believe that ES6 modules and npm are the way forward. If you look at any of the popular open source projects today, such as React or lodash, you’ll see they have also adopted ES6 modules + npm.
  
  无论你是做节点或前端方向，我相信ES6模块或者NPM是一个发展的方向，如今你看看任何流行的开源项目,如React或者lodash，你都会看到他们也都采用了ES6+NPM。
  
## Current workflow
**工作流**

- Many workflows for JavaScript look like this:
  JavaScript的许多工作流程是这样的：

1. Find a plugin or library that you want and download it from GitHub
  
  找到你想要一个插件或库，并从GitHub下载

2. Load it into your website via a script tag

  通过脚本标签加载到您的网站
  
3. Access it via a global variable or as a jQuery plugin

  通过一个全局变量或作为一个jQuery插件来访问

- This type of workflow has worked fairly well for years, but not without its issues:
  这种类型的工作流程已工作相当好几年了，但不是没有它的问题：
 
1. Updates to the plugins have to be done manually — it’s hard to know when there are critical bug fixes or new functionality available.
 
  更新插件必须手动完成 — 这是很难知道什么时候有严重的bug修补或新功能可用。

2. Messy source control history — all dependencies need to be checked into source control and unpleasantness can result when libraries are updated.

  凌乱的源代码控制历史 - 所有的依赖需要签入到源控制还有库更新时可能会导致不愉快的事情。
  
3. Little to no dependency management — many scripts duplicate functionality but could easily share that functionality via a small module.

  几乎没有依赖关系管理 — 许多脚本功能重复，但可以很容易地通过一个小模块来共享重复的功能。
  
4. Pollution and possible collisions within the global name space.
 
  污染和全局命名空间内可能碰撞。

  The idea of writing JavaScript modules isn’t new, but with the arrival of ES6 and the industry settling on npm as the preferred package manager for JavaScript, we’re starting to see many devs migrate away from the above workflow and standardizing on using ES6 and npm.
  
  编写JavaScript模块的想法并不新鲜，但随着ES6的到来和行业解决上NPM为JavaScript的首选包管理器，我们开始看到许多开发者从上面的流程迁移出来，并使用ES6规范和NPM。
