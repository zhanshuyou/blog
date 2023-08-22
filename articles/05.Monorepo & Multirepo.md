# Monorepo & Multirepo
## Monorepo 优点
1. 代码复用
2. 源码调试方便，不需要进入 node_modules
3. 依赖共享
4. 编码规范统一
5. CI/CD 统一
## Monorepo 缺点
1. 仓库变得巨大
2. 变更频繁
3. CI/CD 运行时间长
## Multirepo优点
1. 每个项目可以根据自己的情况选择自己擅长的技术和工具，相对比较灵活，可以使单个团队的效率最大化
## Multirepo缺点
1. 多个仓库之间切换，耗费时间
2. 调试不方便
3. 依赖在多个项目之间重复安装
4. 不同项目依赖版本不同
5. 不利于团队协作，代码库权限，依赖库出现 bug 不能及时修复，需要依赖开发者
6. CI/CD 重复配置
## 参考资料：
1. [精读《Monorepo 的优势》](https://zhuanlan.zhihu.com/p/65533186)
2. [REPO 风格之争：MONO VS MULTI](https://zhuanlan.zhihu.com/p/31289463)
3. [Monorepo与multirepo区别何在？为什么大公司像谷歌.微软.优步都在Monorepo?](https://zhuanlan.zhihu.com/p/75078526)
