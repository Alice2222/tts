#### docker部署web入门

images: 虚拟机镜像，一个模板
container: imanges运行时状态

docker对于运行过的image都报了一个状态（container）,使用docker ps查看正在运行的container，对于已经退出的container，使用docker ps -a查看。

如果你退出了一个container而忘记保存其中的数据，你可以使用docker ps -a来找到对应的运行过的container使用docker commit命令将其保存为image然后运行。

所以当面临docker报错：Error response from daemon: Conflict. The container name “****“ is already in use by...问题，由于image被某个container引用（拿来运行），如果不将这个引用的container销毁（删除），那image肯定是不能被删除。

所以想要删除运行过的images必须首先删除它的container。继续来看刚才的例子，
 

