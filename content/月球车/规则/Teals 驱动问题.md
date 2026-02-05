https://zhuanlan.zhihu.com/p/353130007
如果您看到“ Mesa”，“ Software Rasterizer”或“ GDI Generic”，则表明当前未安装硬件驱动程序，并且您的计算机当前正在使用OpenGL的慢速软件仿真：

```powershell
$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
...
```

I want to rendering a 3D scenes with my server(tesla p100). But after many try, it does’t work. Although opengl4.5 is said to be supported in the document of 410.104 driver, I still wonder whether the P100 support opengl or 3d rendering? Thank you in advanced
https://forums.developer.nvidia.com/t/does-tesla-p100-support-opengl/79022

```
Thank you for your work  
  
P100 requires a special driver that fully supports OpenGL, however, it is too slow. M40 faster than it.  

K80 hardware specifications worse than M40, so, V100 worth trying.
```

```
M40/M60/K80/V100 driver version is: 387.34，it's FREE.  
  
P100 requires special drivers included with NV Grid 5.1. This driver needs to pay. Free drivers do not have OpenGL features.

```
