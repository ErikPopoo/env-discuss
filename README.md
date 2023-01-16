# env-discuss

## local 环境

- 开发人员本地开发环境，可以正常启动整个程序，不存在外部依赖

- 对应 git 的 `features/xxx` 分支（xxx 表示功能）

- 开发人员本地应安装所有依赖中间件（MySQL，ES，Redis 等）

- 开发时在本地启动所有依赖的微服务，或者通过 mock 的方式处理微服务依赖

- 其它成员若有依赖更新，应先把该成员的功能拉到本地再进行后续开发


## dev 环境

- 开发联调环境，用于单个功能完成后进行功能联调，代码合并到 `dev` 分支后，CI 自动触发构建

- 对应 git 的 `dev` 分支

- 所有中间件（MySQL，ES，Redis 等）提供给`开发人员`使用管理，但不提供公网连接，需要通过 jump server 或者有认证系统的 dashboard 进行操作

- 联调过程中需要修改代码，可在原 `features/xxx` 分支，或者基于 `dev` 分支开一个 `hotfix/xxx` 分支进行修改，再合回 `dev` 分支


## test 环境

- 测试环境，申请转测后提供给测试人员进行测试的稳定环境（不受功能开发联调影响），代码合并到 `test` 分支后，CI 自动触发构建

- 对应 git 的 `test` 分支

- 所有中间件（MySQL，ES，Redis 等）提供给`测试人员`使用管理，但不提供公网连接，需要通过 jump server 或者有认证系统的 dashboard 进行操作

- 测试过程中如果有 bug，应基于 `test` 分支开一个 `hotfix/xxx` 分支（xxx 应为一个或一组 bug 号）进行修改，再合回 `test` 分支


## staging 环境

- 预发布环境/类生产环境，用于发布前的环境测试，运行中的性能测试，及发布胡的生产环境问题复现，代码合并到 `staging` 分支后，CI 自动触发构建

- 对应 git 的 `staging` 分支

- 所有中间件（MySQL，ES，Redis 等）提供给`运维人员`使用管理，但不提供公网连接，需要通过 jump server 或者有认证系统的 dashboard 进行操作


## prod 环境

- 正式环境，和相关负责人确认发布时间后，代码合并到 `prod` 分支后，手动触发 CI 自动构建

- 对应 git 的 `prod` 分支

- 所有中间件（MySQL，ES，Redis 等）提供给 `运维人员` 或 `DBA` 使用管理，但不提供公网连接，需要通过 jump server 或者有认证系统的 dashboard 进行操作
