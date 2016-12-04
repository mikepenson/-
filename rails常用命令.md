$ bin/rails generate model person # 单数
$ bin/rails g controller people # 复数
$ 
$ bin/rails console # 进入rails控制台
$ bin/rails c
$ 
$ bin/rails c production # 生产环境
$ bin/rails c --sandbox # 沙箱模式
-> exit # 离开
$ 
$ bin/rails s # 开启rails服务器
$ bin/rails s -p 4000 -e production # 使用4000端口和production环境
$ 
$ bin/rails new my_app # 新建rails APP
$ bin/rails new my_app --database=mysql # 加上--database参数可以改变设定档的默认值
$ 
$ dbconsole #  开起一个数据库主控台 (可简写为 rails db)
$ destroy 删除 “generate” 所产生的档案
$ runner 在 Rails 环境中执行一段程式，例如 rails runner “puts Person.count”
$ 
$ bundle install # 检查安装gems
$ bundle outdated # 列出新版本
$ bundle update gem_name # 更新制定gems
$ bundle update # 更新所有gems
$ bundle open GEM_NAME # 打开指定gem源码
$ bundle package # 将所有用到的 Gems 打包进 vendor/cache 目录
$ 
$ rails g migration migration_name # 迁移数据库
$ bundle exex rake db:schema:load # 加载schema进入新的数据库
$ 
