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

- dev 所有中间件（MySQL，ES，Redis 等）不能由开发本地走公网连接，需要通过 jump server 或者有认证系统的 dashboard 进行操作

- 联调过程中需要修改代码，可在原 `features/xxx` 分支，或者在 `dev` 分支开一个 `hotfix/xxx` 分支进行修改，再合回 `dev` 分支


## test 环境

- 测试环境，申请转测后提供给测试人员进行测试的稳定环境（不受功能开发联调影响），代码合并到 `test` 分支后，CI 自动触发构建

- 对应 git 的 `test` 分支

## staging 环境

- 对应 git 的 `staging` 分支

## prod 环境

- 对应 git 的 `prod` 分支
