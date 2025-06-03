<style>
    body {
      font-family: "Helvetica Neue", sans-serif;
      
      margin: 0 auto;
      padding: 20px;
      background-color: #f8f9fa;
      color: #333;
      text-align: center;
      background-image: url('../assets/blog-backgrounds/stellar1.png');
    background-size: cover;       /* 让背景图片铺满全屏 */
    background-position: center;  /* 图片居中 */
    background-repeat: no-repeat; /* 不重复 */
    background-attachment: fixed; /* 滚动时背景固定 */
    }
</style>
<body>

# 宝宝椅恒星物理

写这篇md主要是想总结一下这学期上的Stellar Astrophysics，由于Stefan Jordan老爷爷上课基本全靠念稿实在撑不住只能靠自己学了……

## 基本方程

在写基本方程之前还是要把流体力学里的欧拉和拉格朗日表述解释一下，简单来说欧拉表述有一个框死的坐标架，此时描述的物理量是根据坐标确定的：
$$\vec{v} = \vec{v}(x,y,z,t)$$
而拉格朗日表述可以简单理解为随体，跟踪研究一个流体元的运动：
$$\vec{r} = \vec{r}(a,b,c,t)$$
这里的a,b,c就不是空间坐标，而是流体的内禀坐标，那么显然对流体元位移的拉格朗日导数（就是随体导数）可以写成：
$$\frac{D\vec{v}}{Dt} = \frac{\partial v}{\partial t}+\frac{\partial v}{\partial x^i}\frac{\partial x^i}{\partial t} = \frac{\partial v}{\partial t}+(\vec{v}\cdot\nabla)\vec{v}$$
好了，关于流体力学两套表述的东西先说这么多，后面又要用的再补充。

### Mass Distribution and Gravitational Field in Spherical Stars

考虑厚度$dr$的球壳，在欧拉表述下，该球壳对$r$和$t$的依赖可以写成：
$$dm = 4\pi r^2 dr - 4\pi r^2\rho v dt$$
那么$m(r,t)$(一般也记作$M_r$，表示半径$r$内的质量)关于$r$的偏导可以写成：
$$\frac{\partial m}{\partial r} = 4\pi r^2 \rho$$
关于$t$的偏导可以写成：
$$\frac{\partial m}{\partial t} = -4\pi r^2 \rho v$$
一般情况下，交叉项的偏导与求导的先后顺序无关，这样我们可以得到：
$$4\pi \frac{\partial (r^2\rho)}{\partial t}  = -4\pi \frac{\partial (r^2\rho v)}{\partial r}$$
$$\frac{\partial \rho}{\partial t} = -\frac{1}{r^2}\frac{\partial(r^2\rho v)}{\partial r}$$
这其实就是连续性方程，关于连续性方程的推导有很多种方法，比如我们也可以用拉格朗日坐标出发，对一个追踪的流体元而言，它的质量应当是不变的，即：
$$\frac{Dm}{Dt} = \frac{D}{Dt}\int\rho\delta\tau = \int\frac{D\rho}{Dt}\delta\tau + \int\rho(\nabla\cdot\vec{v})\delta\tau =  0$$
其中$\delta\tau$是该流体元的体积，很好理解，对追踪的流体元而言其质量的变化率与密度和体积都有关，至于体积的变化率为什么可以写成这样，从定性的角度理解，速度的散度可以看作是该流体元的膨胀/收缩速率，再考虑到我们的流体元质量守恒，那么连续性方程可以写作：
$$\frac{D\rho}{Dt}+\rho(\nabla\cdot\vec{v}) = 0$$
换成欧拉形式就是：
$$\frac{\partial\rho}{\partial t} + (\vec{v}\cdot\nabla)\rho + \rho(\nabla\cdot\vec{v}) = \frac{\partial\rho}{\partial t} + \nabla\cdot(\rho\vec{v}) = 0$$
这个方程放到球坐标下就和我们刚刚推导的结果一致了。

放到球对称的恒星模型背景下，有时我们习惯直接对$m$求偏导而不是对半径$r$，此时转换关系
$$\frac{\partial}{\partial m} = \frac{\partial}{\partial r}\frac{\partial r}{\partial m}$$
$$\left(\frac{\partial}{\partial t}\right)_m = \frac{\partial}{\partial r}\left(\frac{\partial r}{\partial t}\right)_m + \left(\frac{\partial}{\partial t}\right)_r$$
通过上式我们也可以很简单的得到：
$$\frac{\partial r}{\partial m} = \frac{1}{4\pi r^2\rho}$$
代换回去就得到：
$$\frac{\partial}{\partial m} = \frac{1}{4\pi r^2\rho}\frac{\partial}{\partial r}$$

最后我们简单讨论一下引力势。大家在小学都学过Poisson方程，但是经常记不住正负号，连Stefan教授的slides上符号都打错了，可以想见这个符号有多容易记错：
$$\nabla^2\Phi = 4\pi G\rho$$
我想记错的一大原因应该是和电势的Poisson方程记混了：
$$\nabla^2\Phi = -\frac{\rho}{\epsilon_0}$$
为什么会和电势的Poisson方程记混呢，笔者思考良久，觉得是Gauss定理的问题：
$$\nabla\cdot\vec{E} = \frac{\rho}{\epsilon_0},\ \nabla\cdot\vec{g} = -4\pi G\rho$$
对电场而言，正电荷是源，负电荷是汇，所以Gauss定理是没有负号的（或者说是Gauss定理的符号定义了正负电荷）。而重力场就很奇怪了，因为质量都是正的，但对引力场的贡献都是负的（或者说都是汇），所以在Gauss定理这里就冒出来一个负号。再有根据势的定义，场的正方向定义为势减小的方向$\vec{g}=-\nabla\Phi$，所以这里又有一个负号，负负得正于是引力场的Poisson方程是没有负号的。剩下在球坐标内的表达就是比较trivial的事了（Poisson方程不也很trivial吗），在这里按下方程不表：
$$g = \frac{Gm}{r^2} = \frac{\partial\Phi}{\partial r}$$
$$\frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial\Phi}{\partial r}\right) = 4\pi G\rho$$
还有一个人尽皆知的条件，就是我们一般默认无穷远处的引力势为0，这意味着在全是吸引力的世界里引力势只可能是负的。如果认为质量集中于一个点，那么引力势就会在靠近这个奇点的位置趋近于负无穷大，但在一个有限大的球对称质量分布下，引力势当然也会有一个有限的极小值。


### 动量守恒
一般在流体力学中质量守恒被叫做连续性方程，动量守恒就关系着动力学（或者静力学）方程。由于恒星在主序阶段演化极慢，一般可以近似认为处于平衡态，此时我们仍考虑一个球壳$dr$，球壳内外的压力差应当与该球壳受到的引力平衡，即：
$$\frac{\partial P}{\partial r} + g\rho = 0$$
$$\frac{\partial P}{\partial r} = -\frac{Gm}{r^2}\rho$$
利用我们上一部分得到的$dm$和$dr$关系，可以把质量作为第一性的自变量：
$$\frac{\partial P}{\partial m} = -\frac{Gm}{4\pi r^2}$$

#### The Role of Density and Simple Solutions
利用现有的条件，我们已经获得了两个基本方程（将$m$作为独立变量）
$$\frac{\partial r}{\partial m} = \frac{1}{4\pi r^2\rho},\ \frac{\partial P}{\partial m} = -\frac{Gm}{4\pi r^2}$$
将$m$作为自变量的好处是，作为恒星的基本参数可以通过观测和质光关系定出大致准确的值（这是我编的），不过总之我们就有了三个未知数$r,P,\rho$。不过很不巧的是我们只有两个微分方程，为了解出它们我们至少还需要这三者间的另一个方程，比如密度$\rho$是关于压强$P$的函数。不过一般没办法找到这样的方程



</body>
