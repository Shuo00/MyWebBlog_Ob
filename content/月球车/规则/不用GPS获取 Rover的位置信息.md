我们可以通过下面的代码行来获取巡视器的实例：

```python
robot = sup.getFromDef('Rover')
```

然后，我们可以通过以下代码来获取机器人的当前位置：
```python
robot_translation = robot.getTranslation()
```

在rover_controller能否调用？