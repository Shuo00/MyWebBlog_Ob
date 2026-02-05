atkin是由ROS社区开发的元[编译系统](https://www.zhihu.com/search?q=%E7%BC%96%E8%AF%91%E7%B3%BB%E7%BB%9F&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2318990933%7D)（meta-buildsystem），最初目的是用于编译ROS社区中多个相互依赖的CMake工程。主要有几个阶段：

### catkin_make

刚开始是以catkin_make为代表的命令行工具，主要是封装一系列的[cmake命令](https://www.zhihu.com/search?q=cmake%E5%91%BD%E4%BB%A4&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2318990933%7D)。catkin_make相当于：

```text
$ mkdir build
$ cd build
$ cmake ../src -DCATKIN_DEVEL_SPACE=../devel -DCMAKE_INSTALL_PREFIX=../install
$ make -j<number of cores> -l<number of cores> [optional target, e.g. install]
```

但是catkin_make自身有些缺陷。比如，没有编译时的错误隔离。

### catkin_make_isolated

后来catkin_make_isolated解决了隔离的问题，但是编译速度还是慢，因为不支持并行编译。

### catkin tools（推荐使用）

再后来catkin tools独立出来，推出一系列python编写的编译命令。其中catkin build支持隔离和并行编译。其他主要命令有：

```text
catkin build --编译包
catkin clean --清空编译空间
catkin config --配置编译工作空间
catkin create --创建包
catkin env --环境变量工具
catkin init --初始化编译空间
catkin list --查看包信息
catkin locate --定位编译目录
catkin profile --指定编译配置
catkin test --测试包
```

catkin tools官方文档：

[Catkin Command Line Tools​catkin-tools.readthedocs.io/en/latest/index.html](https://link.zhihu.com/?target=https%3A//catkin-tools.readthedocs.io/en/latest/index.html)