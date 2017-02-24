### 开源的obj加载器

>计算机图形学课程的副产物，现课程已结束故将其开源，其中部分源代码参考了《WebGl编程指南》中的样例，本obj加载器主要是给初中级WebGl学习者完善

**注意：由于在项目中考虑到复用关系，我目前的代码没有做充分封装，请使用的时候注意变量冲突的情况**

### 文件内容

* lib:数学库函数，和obj加载没有直接关系，但是在WebGl种很有用
* src:带有注释的项目源代码
* dist:可用于生产环境的项目代码
* example:使用实例

另外，我们小组使用了我个人开发的obj加载器，作为测试，效果还算良好，可以移步小组项目主页：https://github.com/WebGLproj/WebGLpro

### 详细使用说明

展示1个obj只需要一行代码:

```readOBJFile('./models/cube.obj', modelObject, mtlArray, objArray, 20, false, 0);
```再添加1个纹理只需要两行代码:

```readOBJFile('./models/cube.obj', modelObject, mtlArray, objArray, 20, false, 0); 
TextureArray[0]={ifTexture:0.0,TextureUrl:'none',n:0};```改变透明度、默认颜 、缩放、旋转、方位、只需要三行代码:

```readOBJFile('./models/cube.obj', modelObject, mtlArray, objArray, 20, false, 0); 
TextureArray[0]={ifTexture:0.0,TextureUrl:'none',n:0};  
updateDrawInfo(0,[0.0,90.0,0.0, 0.0,6.0,0.0, 0.75,0.4,0.5,   0.5,0.5,0.5,1,0 ,1]);
```

注：关于第三种各个参数的位置，可以直接查看updateDrawInfo函数：

```
function updateDrawInfo(index,someDrawInfo){
    if(!modelDrawInfo[index])
        modelDrawInfo[index]={};

    //旋转参数
    modelDrawInfo[index].rotateX=someDrawInfo[0];
    modelDrawInfo[index].rotateY=someDrawInfo[1];
    modelDrawInfo[index].rotateZ=someDrawInfo[2];

    //位置参数
    modelDrawInfo[index].offsetX=someDrawInfo[3];
    modelDrawInfo[index].offsetY=someDrawInfo[4];
    modelDrawInfo[index].offsetZ=someDrawInfo[5];

    //缩放参数
    modelDrawInfo[index].scaleX=someDrawInfo[6];
    modelDrawInfo[index].scaleY=someDrawInfo[7];
    modelDrawInfo[index].scaleZ=someDrawInfo[8];

    //自定义颜色参数
    modelDrawInfo[index].r=someDrawInfo[9];
    modelDrawInfo[index].g=someDrawInfo[10];
    modelDrawInfo[index].b=someDrawInfo[11];
    modelDrawInfo[index].a=someDrawInfo[12];
    modelDrawInfo[index].u_ifCertainColor=someDrawInfo[13];

    //是否隐藏
    modelDrawInfo[index].ifShow=someDrawInfo[14];

}
```

关于具体的使用方式，我已经给出了详细的例子，在example文件夹下的computerRoom.html 和 computerRoom.js 中。

*解释权归个人所有，联系方式:networknxt@gmail.com*

### 协议

MIT
