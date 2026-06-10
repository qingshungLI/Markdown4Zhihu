# 非线性物理从 0 到 1：从相空间到混沌与斑图

非线性物理不是一门“把方程解出来”的课。多数时候，方程根本没有漂亮的解析解；真正重要的是看出系统的长期命运：它会停在稳态、绕成周期运动、突然跳变、进入混沌，还是在空间中自发长出斑图与螺旋波。

这份讲义按一条主线写：


<img src="https://www.zhihu.com/equation?tex=\text{相空间}
\rightarrow
\text{不动点与分岔}
\rightarrow
\text{振荡与极限环}
\rightarrow
\text{混沌}
\rightarrow
\text{反应扩散与时空结构}
" alt="\text{相空间}
\rightarrow
\text{不动点与分岔}
\rightarrow
\text{振荡与极限环}
\rightarrow
\text{混沌}
\rightarrow
\text{反应扩散与时空结构}
" class="ee_img tr_noresize" eeimg="1">

所有公式都服务于一个问题：当参数改变时，速度场的结构怎样改变？只要抓住这件事，鞍结、Hopf、同宿、SNIC、Turing、螺旋波就不再是零散名词，而是一套连续的图像。

![吸引子的几种典型形态：点、环、环面与奇异吸引子](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/22_attractor_types.png)

## 0. 先建立地图：非线性系统到底看什么

一个自治动力系统写成


<img src="https://www.zhihu.com/equation?tex=\dot{\mathbf x}=\mathbf F(\mathbf x;\mu),
" alt="\dot{\mathbf x}=\mathbf F(\mathbf x;\mu),
" class="ee_img tr_noresize" eeimg="1">

其中  <img src="https://www.zhihu.com/equation?tex=\mathbf x" alt="\mathbf x" class="ee_img tr_noresize" eeimg="1">  是状态， <img src="https://www.zhihu.com/equation?tex=\mu" alt="\mu" class="ee_img tr_noresize" eeimg="1">  是控制参量。相空间中每个点都挂着一个速度箭头  <img src="https://www.zhihu.com/equation?tex=\mathbf F" alt="\mathbf F" class="ee_img tr_noresize" eeimg="1"> ，轨道就是沿箭头走出的曲线。

初学时最容易被公式淹没。先记住七个动作：

1. 设右端为零，找不动点或均匀稳态。
2. 在线性近似下算 Jacobian。
3. 用特征值、迹、行列式判断局部稳定性。
4. 参数变化时，盯住特征值是否碰到临界位置： <img src="https://www.zhihu.com/equation?tex=0" alt="0" class="ee_img tr_noresize" eeimg="1">  或虚轴。
5. 一旦线性项失效，就看最低阶非线性项，也就是正则形。
6. 加上空间扩散时，把扰动拆成 Fourier 模式，令  <img src="https://www.zhihu.com/equation?tex=\nabla^2\mapsto -k^2" alt="\nabla^2\mapsto -k^2" class="ee_img tr_noresize" eeimg="1"> 。
7. 有延迟时，代入指数试探  <img src="https://www.zhihu.com/equation?tex=e^{\lambda t}" alt="e^{\lambda t}" class="ee_img tr_noresize" eeimg="1"> ，特征方程里会出现  <img src="https://www.zhihu.com/equation?tex=e^{-\lambda\tau}" alt="e^{-\lambda\tau}" class="ee_img tr_noresize" eeimg="1"> 。

贯穿全书的统一直觉是：

> 定性变化来自“速度为零或接近为零的地方”如何出现、消失、碰撞、改变稳定性。

不动点是严格零速度点；极限环是一条速度不为零但绕回原处的闭轨；慢区是速度很小、轨道会在那里停留很久的区域。后面所有分岔都可以用这三类对象解释。

## 1. 一维流：从“根”读懂分岔

一维自治系统是


<img src="https://www.zhihu.com/equation?tex=\dot x=f(x;r).
" alt="\dot x=f(x;r).
" class="ee_img tr_noresize" eeimg="1">

不动点满足


<img src="https://www.zhihu.com/equation?tex=f(x^*;r)=0.
" alt="f(x^*;r)=0.
" class="ee_img tr_noresize" eeimg="1">

令  <img src="https://www.zhihu.com/equation?tex=x=x^*+\eta" alt="x=x^*+\eta" class="ee_img tr_noresize" eeimg="1"> ，保留一阶项：


<img src="https://www.zhihu.com/equation?tex=\dot\eta=f_x(x^*;r)\eta,
\qquad
\eta(t)=\eta(0)e^{f_x(x^*;r)t}.
" alt="\dot\eta=f_x(x^*;r)\eta,
\qquad
\eta(t)=\eta(0)e^{f_x(x^*;r)t}.
" class="ee_img tr_noresize" eeimg="1">

因此：


<img src="https://www.zhihu.com/equation?tex=f_x(x^*;r)<0 \Rightarrow \text{稳定},
\qquad
f_x(x^*;r)>0 \Rightarrow \text{不稳定}.
" alt="f_x(x^*;r)<0 \Rightarrow \text{稳定},
\qquad
f_x(x^*;r)>0 \Rightarrow \text{不稳定}.
" class="ee_img tr_noresize" eeimg="1">

如果  <img src="https://www.zhihu.com/equation?tex=f_x=0" alt="f_x=0" class="ee_img tr_noresize" eeimg="1"> ，一阶判据失效，常常意味着分岔。图像上，一维分岔就是  <img src="https://www.zhihu.com/equation?tex=f(x;r)" alt="f(x;r)" class="ee_img tr_noresize" eeimg="1">  与  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  轴的交点结构发生改变。

![一维常见分岔：鞍结、跨临界、超临界叉形、亚临界叉形](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/01_one_dimensional_bifurcations.png)

### 1.1 为什么根的数目会改变

普通根是横截交点。参数轻微改变时，横截交点只会平滑移动，不会突然消失。要让两个根相遇并消失，曲线必须与  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  轴相切：


<img src="https://www.zhihu.com/equation?tex=f(x^*;r^*)=0,
\qquad
f_x(x^*;r^*)=0.
" alt="f(x^*;r^*)=0,
\qquad
f_x(x^*;r^*)=0.
" class="ee_img tr_noresize" eeimg="1">

这就是鞍结等局部分岔的基本条件。

把分岔点平移到  <img src="https://www.zhihu.com/equation?tex=(x,r)=(0,0)" alt="(x,r)=(0,0)" class="ee_img tr_noresize" eeimg="1"> ，Taylor 展开：


<img src="https://www.zhihu.com/equation?tex=\dot x=f(x;r)=ar+bx^2+\cdots.
" alt="\dot x=f(x;r)=ar+bx^2+\cdots.
" class="ee_img tr_noresize" eeimg="1">

经过缩放，最低阶结构化成


<img src="https://www.zhihu.com/equation?tex=\dot x=r\pm x^2.
" alt="\dot x=r\pm x^2.
" class="ee_img tr_noresize" eeimg="1">

这就是正则形：保留改变局部拓扑结构的最低阶项，丢掉不影响类型的细节。

### 1.2 四种基本一维分岔

**鞍结分岔。**


<img src="https://www.zhihu.com/equation?tex=\dot x=r-x^2.
" alt="\dot x=r-x^2.
" class="ee_img tr_noresize" eeimg="1">

当  <img src="https://www.zhihu.com/equation?tex=r>0" alt="r>0" class="ee_img tr_noresize" eeimg="1">  时，


<img src="https://www.zhihu.com/equation?tex=x_\pm=\pm\sqrt r,
\qquad
f_x=-2x.
" alt="x_\pm=\pm\sqrt r,
\qquad
f_x=-2x.
" class="ee_img tr_noresize" eeimg="1">

所以  <img src="https://www.zhihu.com/equation?tex=x_+=\sqrt r" alt="x_+=\sqrt r" class="ee_img tr_noresize" eeimg="1">  稳定， <img src="https://www.zhihu.com/equation?tex=x_-=-\sqrt r" alt="x_-=-\sqrt r" class="ee_img tr_noresize" eeimg="1">  不稳定。 <img src="https://www.zhihu.com/equation?tex=r\to0^+" alt="r\to0^+" class="ee_img tr_noresize" eeimg="1">  时一稳一不稳碰撞， <img src="https://www.zhihu.com/equation?tex=r<0" alt="r<0" class="ee_img tr_noresize" eeimg="1">  后根消失。

**跨临界分岔。**


<img src="https://www.zhihu.com/equation?tex=\dot x=rx-x^2=x(r-x).
" alt="\dot x=rx-x^2=x(r-x).
" class="ee_img tr_noresize" eeimg="1">

两条分支  <img src="https://www.zhihu.com/equation?tex=x=0" alt="x=0" class="ee_img tr_noresize" eeimg="1">  与  <img src="https://www.zhihu.com/equation?tex=x=r" alt="x=r" class="ee_img tr_noresize" eeimg="1">  始终存在，在  <img src="https://www.zhihu.com/equation?tex=r=0" alt="r=0" class="ee_img tr_noresize" eeimg="1">  交换稳定性。它常出现于“两个状态都有物理意义，并在临界处互换角色”的问题。

**超临界叉形分岔。**


<img src="https://www.zhihu.com/equation?tex=\dot x=rx-x^3.
" alt="\dot x=rx-x^3.
" class="ee_img tr_noresize" eeimg="1">

当  <img src="https://www.zhihu.com/equation?tex=r<0" alt="r<0" class="ee_img tr_noresize" eeimg="1">  时只有稳定原点；当  <img src="https://www.zhihu.com/equation?tex=r>0" alt="r>0" class="ee_img tr_noresize" eeimg="1">  时原点失稳，出现两个稳定非零态：


<img src="https://www.zhihu.com/equation?tex=x=\pm\sqrt r.
" alt="x=\pm\sqrt r.
" class="ee_img tr_noresize" eeimg="1">

这是对称系统中“一个中心态分裂成两个对称稳定态”的典型图像。

**亚临界叉形分岔。**


<img src="https://www.zhihu.com/equation?tex=\dot x=rx+x^3.
" alt="\dot x=rx+x^3.
" class="ee_img tr_noresize" eeimg="1">

非零分支出现在  <img src="https://www.zhihu.com/equation?tex=r<0" alt="r<0" class="ee_img tr_noresize" eeimg="1"> ，但它们不稳定； <img src="https://www.zhihu.com/equation?tex=r>0" alt="r>0" class="ee_img tr_noresize" eeimg="1">  后原点也不稳定。真实系统通常还要靠更高阶项把远处振幅限制住，因此亚临界结构常伴随跳变与滞后。

### 1.3 不完美叉形：对称性被打破会怎样

完美叉形依赖  <img src="https://www.zhihu.com/equation?tex=x\mapsto -x" alt="x\mapsto -x" class="ee_img tr_noresize" eeimg="1">  对称。如果加入二次项，


<img src="https://www.zhihu.com/equation?tex=\dot x=rx+ax^2-x^3,
" alt="\dot x=rx+ax^2-x^3,
" class="ee_img tr_noresize" eeimg="1">

对称性被破坏。此时不动点为


<img src="https://www.zhihu.com/equation?tex=x=0,
\qquad
x=\frac{a\pm\sqrt{a^2+4r}}2.
" alt="x=0,
\qquad
x=\frac{a\pm\sqrt{a^2+4r}}2.
" class="ee_img tr_noresize" eeimg="1">

非零分支存在条件是


<img src="https://www.zhihu.com/equation?tex=a^2+4r\ge0,
\qquad
r\ge-\frac{a^2}4.
" alt="a^2+4r\ge0,
\qquad
r\ge-\frac{a^2}4.
" class="ee_img tr_noresize" eeimg="1">

这条边界是两条非零分支相切合并的位置，也就是鞍结曲线。原本一个完美叉形被拆成“一个跨临界结构 + 一个鞍结结构”。

![不完美叉形：对称性破缺后分支被拆开](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/02_imperfect_pitchfork.png)

### 1.4 例题：锁相、过阻尼摆与慢区

相位锁定问题常化成一维方程：


<img src="https://www.zhihu.com/equation?tex=\dot\phi=\Delta\omega-K\sin\phi.
" alt="\dot\phi=\Delta\omega-K\sin\phi.
" class="ee_img tr_noresize" eeimg="1">

不动点存在要求


<img src="https://www.zhihu.com/equation?tex=|\Delta\omega|\le K.
" alt="|\Delta\omega|\le K.
" class="ee_img tr_noresize" eeimg="1">

等号处两个相位锁定点碰撞消失，是鞍结分岔。若  <img src="https://www.zhihu.com/equation?tex=|\Delta\omega|>K" alt="|\Delta\omega|>K" class="ee_img tr_noresize" eeimg="1"> ，相位差无法停住，会持续滑移。

过阻尼摆也有同样结构：


<img src="https://www.zhihu.com/equation?tex=\dot\theta=\Omega-\sin\theta.
" alt="\dot\theta=\Omega-\sin\theta.
" class="ee_img tr_noresize" eeimg="1">

当  <img src="https://www.zhihu.com/equation?tex=|\Omega|<1" alt="|\Omega|<1" class="ee_img tr_noresize" eeimg="1"> ，有静止角度；当  <img src="https://www.zhihu.com/equation?tex=|\Omega|>1" alt="|\Omega|>1" class="ee_img tr_noresize" eeimg="1"> ，摆会持续转动。临界  <img src="https://www.zhihu.com/equation?tex=|\Omega|=1" alt="|\Omega|=1" class="ee_img tr_noresize" eeimg="1">  附近，系统经过某一角度时速度极小，这就是慢区。穿过慢区的时间满足


<img src="https://www.zhihu.com/equation?tex=T\sim\int\frac{d\theta}{\Omega-\sin\theta},
" alt="T\sim\int\frac{d\theta}{\Omega-\sin\theta},
" class="ee_img tr_noresize" eeimg="1">

并在临界附近变得很长。这个图像会在 SNIC 分岔里再次出现。

## 2. 二维线性系统：迹、行列式和相图分类

二维线性系统写成


<img src="https://www.zhihu.com/equation?tex=\dot{\mathbf x}=A\mathbf x,
\qquad
A=
\begin{pmatrix}
a&b\\
c&d
\end{pmatrix}.
" alt="\dot{\mathbf x}=A\mathbf x,
\qquad
A=
\begin{pmatrix}
a&b\\
c&d
\end{pmatrix}.
" class="ee_img tr_noresize" eeimg="1">

特征方程为


<img src="https://www.zhihu.com/equation?tex=\lambda^2-\tau\lambda+\Delta=0,
\qquad
\tau=a+d,
\quad
\Delta=ad-bc.
" alt="\lambda^2-\tau\lambda+\Delta=0,
\qquad
\tau=a+d,
\quad
\Delta=ad-bc.
" class="ee_img tr_noresize" eeimg="1">

因此所有局部类型都由迹  <img src="https://www.zhihu.com/equation?tex=\tau" alt="\tau" class="ee_img tr_noresize" eeimg="1">  和行列式  <img src="https://www.zhihu.com/equation?tex=\Delta" alt="\Delta" class="ee_img tr_noresize" eeimg="1">  决定。

![二维线性系统分类：迹-行列式平面](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/03_linear_system_classification.png)

### 2.1 分类从哪里来

如果  <img src="https://www.zhihu.com/equation?tex=\Delta<0" alt="\Delta<0" class="ee_img tr_noresize" eeimg="1"> ，两个特征值一正一负，轨道沿一个方向进、另一个方向出，是鞍点。

如果  <img src="https://www.zhihu.com/equation?tex=\Delta>0" alt="\Delta>0" class="ee_img tr_noresize" eeimg="1">  且  <img src="https://www.zhihu.com/equation?tex=\tau<0" alt="\tau<0" class="ee_img tr_noresize" eeimg="1"> ，两个特征值实部都为负，是稳定结点或稳定焦点。

如果  <img src="https://www.zhihu.com/equation?tex=\Delta>0" alt="\Delta>0" class="ee_img tr_noresize" eeimg="1">  且  <img src="https://www.zhihu.com/equation?tex=\tau>0" alt="\tau>0" class="ee_img tr_noresize" eeimg="1"> ，两个特征值实部都为正，是不稳定结点或不稳定焦点。

区分结点和焦点看判别式：


<img src="https://www.zhihu.com/equation?tex=\tau^2-4\Delta.
" alt="\tau^2-4\Delta.
" class="ee_img tr_noresize" eeimg="1">

若它为正，特征值为实数，是结点；若为负，特征值为共轭复数，是焦点；若  <img src="https://www.zhihu.com/equation?tex=\tau=0" alt="\tau=0" class="ee_img tr_noresize" eeimg="1">  且  <img src="https://www.zhihu.com/equation?tex=\Delta>0" alt="\Delta>0" class="ee_img tr_noresize" eeimg="1"> ，特征值为纯虚数，是中心或 Hopf 临界的线性部分。

### 2.2 例题：为什么 Hopf 在二维里写成  <img src="https://www.zhihu.com/equation?tex=\tau=0,\Delta>0" alt="\tau=0,\Delta>0" class="ee_img tr_noresize" eeimg="1"> 

二维特征值可写成


<img src="https://www.zhihu.com/equation?tex=\lambda_\pm=\frac\tau2\pm\frac12\sqrt{\tau^2-4\Delta}.
" alt="\lambda_\pm=\frac\tau2\pm\frac12\sqrt{\tau^2-4\Delta}.
" class="ee_img tr_noresize" eeimg="1">

Hopf 要求一对复特征值穿过虚轴，因此在临界点：


<img src="https://www.zhihu.com/equation?tex=\operatorname{Re}\lambda_\pm=\frac\tau2=0.
" alt="\operatorname{Re}\lambda_\pm=\frac\tau2=0.
" class="ee_img tr_noresize" eeimg="1">

同时要是复数而不是两个实数，所以


<img src="https://www.zhihu.com/equation?tex=\Delta>0.
" alt="\Delta>0.
" class="ee_img tr_noresize" eeimg="1">

再加上穿越条件：


<img src="https://www.zhihu.com/equation?tex=\frac{d\tau}{d\mu}\ne0.
" alt="\frac{d\tau}{d\mu}\ne0.
" class="ee_img tr_noresize" eeimg="1">

但这只说明焦点稳定性改变，不能说明出现稳定环还是不稳定环。后者要看非线性项。

## 3. 二维非线性系统：零解线、线性化与相平面

二维非线性系统写成


<img src="https://www.zhihu.com/equation?tex=\dot x=f(x,y),
\qquad
\dot y=g(x,y).
" alt="\dot x=f(x,y),
\qquad
\dot y=g(x,y).
" class="ee_img tr_noresize" eeimg="1">

不动点由


<img src="https://www.zhihu.com/equation?tex=f(x,y)=0,
\qquad
g(x,y)=0
" alt="f(x,y)=0,
\qquad
g(x,y)=0
" class="ee_img tr_noresize" eeimg="1">

共同确定。两条曲线分别叫  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  零解线和  <img src="https://www.zhihu.com/equation?tex=y" alt="y" class="ee_img tr_noresize" eeimg="1">  零解线，它们的交点就是不动点。

在不动点  <img src="https://www.zhihu.com/equation?tex=(x^*,y^*)" alt="(x^*,y^*)" class="ee_img tr_noresize" eeimg="1">  附近线性化：


<img src="https://www.zhihu.com/equation?tex=\begin{pmatrix}\dot\xi\\\dot\eta\end{pmatrix}
=
J
\begin{pmatrix}\xi\\\eta\end{pmatrix},
\qquad
J=
\begin{pmatrix}
f_x&f_y\\
g_x&g_y
\end{pmatrix}_{(x^*,y^*)}.
" alt="\begin{pmatrix}\dot\xi\\\dot\eta\end{pmatrix}
=
J
\begin{pmatrix}\xi\\\eta\end{pmatrix},
\qquad
J=
\begin{pmatrix}
f_x&f_y\\
g_x&g_y
\end{pmatrix}_{(x^*,y^*)}.
" class="ee_img tr_noresize" eeimg="1">

局部稳定性由  <img src="https://www.zhihu.com/equation?tex=J" alt="J" class="ee_img tr_noresize" eeimg="1">  的特征值决定。

### 3.1 相平面操作顺序

分析一个二维非线性模型，按下面顺序最稳：

1. 画或求  <img src="https://www.zhihu.com/equation?tex=f=0" alt="f=0" class="ee_img tr_noresize" eeimg="1"> 、 <img src="https://www.zhihu.com/equation?tex=g=0" alt="g=0" class="ee_img tr_noresize" eeimg="1">  两条零解线。
2. 找交点。
3. 在交点处算 Jacobian。
4. 用  <img src="https://www.zhihu.com/equation?tex=\tau,\Delta" alt="\tau,\Delta" class="ee_img tr_noresize" eeimg="1">  判断局部类型。
5. 再看全局约束：是否存在闭轨、轨道是否被困在有界区域、是否存在势函数或 Dulac 函数。

### 3.2 例题：一个带参数的二维分岔系统

设


<img src="https://www.zhihu.com/equation?tex=\dot x=-x+2y+x^2,
" alt="\dot x=-x+2y+x^2,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\dot y=(2-\alpha)x-y-3x^2+\frac32xy.
" alt="\dot y=(2-\alpha)x-y-3x^2+\frac32xy.
" class="ee_img tr_noresize" eeimg="1">

从第一式零解线得


<img src="https://www.zhihu.com/equation?tex=y=\frac{x-x^2}2.
" alt="y=\frac{x-x^2}2.
" class="ee_img tr_noresize" eeimg="1">

代入第二式，得到分支关系


<img src="https://www.zhihu.com/equation?tex=x\left(-\alpha+\frac32-\frac74x-\frac34x^2\right)=0.
" alt="x\left(-\alpha+\frac32-\frac74x-\frac34x^2\right)=0.
" class="ee_img tr_noresize" eeimg="1">

所以原点一直存在，非零分支满足


<img src="https://www.zhihu.com/equation?tex=\alpha=\frac32-\frac74x-\frac34x^2.
" alt="\alpha=\frac32-\frac74x-\frac34x^2.
" class="ee_img tr_noresize" eeimg="1">

原点处


<img src="https://www.zhihu.com/equation?tex=J_0=
\begin{pmatrix}
-1&2\\
2-\alpha&-1
\end{pmatrix},
\qquad
\Delta_0=2\alpha-3.
" alt="J_0=
\begin{pmatrix}
-1&2\\
2-\alpha&-1
\end{pmatrix},
\qquad
\Delta_0=2\alpha-3.
" class="ee_img tr_noresize" eeimg="1">

因此  <img src="https://www.zhihu.com/equation?tex=\alpha=3/2" alt="\alpha=3/2" class="ee_img tr_noresize" eeimg="1">  是零特征值分岔点。

非零分支上的鞍结来自分支曲线相切：


<img src="https://www.zhihu.com/equation?tex=\frac{d\alpha}{dx}=-\frac74-\frac32x=0,
\qquad
x=-\frac76.
" alt="\frac{d\alpha}{dx}=-\frac74-\frac32x=0,
\qquad
x=-\frac76.
" class="ee_img tr_noresize" eeimg="1">

代回得到


<img src="https://www.zhihu.com/equation?tex=\alpha=\frac{121}{48}.
" alt="\alpha=\frac{121}{48}.
" class="ee_img tr_noresize" eeimg="1">

非零分支上的 Hopf 来自迹为零。Jacobian 的迹是


<img src="https://www.zhihu.com/equation?tex=\tau=-2+\frac72x.
" alt="\tau=-2+\frac72x.
" class="ee_img tr_noresize" eeimg="1">

令  <img src="https://www.zhihu.com/equation?tex=\tau=0" alt="\tau=0" class="ee_img tr_noresize" eeimg="1">  得


<img src="https://www.zhihu.com/equation?tex=x=\frac47,
\qquad
\alpha=\frac{25}{98}.
" alt="x=\frac47,
\qquad
\alpha=\frac{25}{98}.
" class="ee_img tr_noresize" eeimg="1">

这个例子把“零解线、分支、鞍结、Hopf”放在同一个模型里，适合反复练。

![参数分岔例子：分支、稳定性与临界点](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/13_parameter_bifurcation_examples.png)

## 4. 势、梯度系统、Dulac 与指数：闭轨能不能存在

线性化只能告诉我们不动点附近发生什么。要判断系统有没有极限环，需要全局工具。

### 4.1 梯度系统为什么没有稳定极限环

若系统能写成


<img src="https://www.zhihu.com/equation?tex=\dot{\mathbf x}=-\nabla V(\mathbf x),
" alt="\dot{\mathbf x}=-\nabla V(\mathbf x),
" class="ee_img tr_noresize" eeimg="1">

则


<img src="https://www.zhihu.com/equation?tex=\frac{dV}{dt}
=\nabla V\cdot\dot{\mathbf x}
=-|\nabla V|^2\le0.
" alt="\frac{dV}{dt}
=\nabla V\cdot\dot{\mathbf x}
=-|\nabla V|^2\le0.
" class="ee_img tr_noresize" eeimg="1">

沿轨道势函数单调下降，除非到达不动点，否则不能回到原来的  <img src="https://www.zhihu.com/equation?tex=V" alt="V" class="ee_img tr_noresize" eeimg="1">  值。因此非平凡周期轨不存在。稳定极限环不是梯度系统的产物。

二维向量场  <img src="https://www.zhihu.com/equation?tex=\mathbf F=(P,Q)" alt="\mathbf F=(P,Q)" class="ee_img tr_noresize" eeimg="1">  若要来自势函数，常用交叉偏导检查：


<img src="https://www.zhihu.com/equation?tex=\frac{\partial P}{\partial y}
=
\frac{\partial Q}{\partial x}
" alt="\frac{\partial P}{\partial y}
=
\frac{\partial Q}{\partial x}
" class="ee_img tr_noresize" eeimg="1">

或在负梯度约定下相差一个整体符号。

### 4.2 Dulac 判据

在单连通区域  <img src="https://www.zhihu.com/equation?tex=R" alt="R" class="ee_img tr_noresize" eeimg="1">  内，若存在函数  <img src="https://www.zhihu.com/equation?tex=B(x,y)" alt="B(x,y)" class="ee_img tr_noresize" eeimg="1">  使


<img src="https://www.zhihu.com/equation?tex=\frac{\partial (Bf)}{\partial x}
+\frac{\partial (Bg)}{\partial y}
" alt="\frac{\partial (Bf)}{\partial x}
+\frac{\partial (Bg)}{\partial y}
" class="ee_img tr_noresize" eeimg="1">

不变号且不恒为零，则该区域内没有闭轨。

直觉来自 Green 定理：如果存在闭轨，向量场沿闭轨切向流动，法向通量为零；但散度在内部积分若严格同号，就会给出非零通量，矛盾。

### 4.3 Poincare-Bendixson 与指数

Poincare-Bendixson 定理说：二维自治系统中，若一条轨道被困在不含不动点的有界闭区域内，则它的极限集是闭轨。它常用来证明极限环存在。

指数理论则限制闭轨内部的不动点配置。一条简单闭轨的指标为  <img src="https://www.zhihu.com/equation?tex=+1" alt="+1" class="ee_img tr_noresize" eeimg="1"> 。稳定结点、源、焦点、中心的指标都是  <img src="https://www.zhihu.com/equation?tex=+1" alt="+1" class="ee_img tr_noresize" eeimg="1"> ；鞍点指标是  <img src="https://www.zhihu.com/equation?tex=-1" alt="-1" class="ee_img tr_noresize" eeimg="1"> 。因此闭轨内部孤立不动点的指标和必须为


<img src="https://www.zhihu.com/equation?tex=+1.
" alt="+1.
" class="ee_img tr_noresize" eeimg="1">

例如，一个极限环内部不能只有一个鞍点，因为指标为  <img src="https://www.zhihu.com/equation?tex=-1" alt="-1" class="ee_img tr_noresize" eeimg="1"> ；可以有一个焦点，也可以有两个结点加一个鞍点。

![Poincare 映射与全局分岔：从闭轨到截面](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/07_poincare_map_and_global_bifurcation.png)

## 5. 极限环与自激振荡：Van der Pol、Lienard、可激发系统

极限环是一条孤立闭轨：


<img src="https://www.zhihu.com/equation?tex=\mathbf x(t+T)=\mathbf x(t).
" alt="\mathbf x(t+T)=\mathbf x(t).
" class="ee_img tr_noresize" eeimg="1">

如果附近轨道都趋向它，就是稳定极限环，对应自激振荡。

### 5.1 Lienard 与 Van der Pol：小振幅供能，大振幅耗能

Lienard 方程常写成


<img src="https://www.zhihu.com/equation?tex=x''+f(x)x'+g(x)=0.
" alt="x''+f(x)x'+g(x)=0.
" class="ee_img tr_noresize" eeimg="1">

Van der Pol 方程是最典型的例子：


<img src="https://www.zhihu.com/equation?tex=x''-\mu(1-x^2)x'+x=0,
\qquad
\mu>0.
" alt="x''-\mu(1-x^2)x'+x=0,
\qquad
\mu>0.
" class="ee_img tr_noresize" eeimg="1">

把阻尼项看成


<img src="https://www.zhihu.com/equation?tex=-\mu(1-x^2)x'.
" alt="-\mu(1-x^2)x'.
" class="ee_img tr_noresize" eeimg="1">

当  <img src="https://www.zhihu.com/equation?tex=|x|<1" alt="|x|<1" class="ee_img tr_noresize" eeimg="1"> ，等效阻尼为负，系统从外界吸收能量；当  <img src="https://www.zhihu.com/equation?tex=|x|>1" alt="|x|>1" class="ee_img tr_noresize" eeimg="1"> ，等效阻尼为正，系统耗散能量。于是小振幅被放大，大振幅被压回，最终形成稳定极限环。

![Van der Pol 振子：相平面中的稳定极限环](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/05_van_der_pol_limit_cycle.png)

### 5.2 可激发系统：稳定点也能产生大响应

可激发系统不是自振荡系统。单个局部系统通常只有一个稳定静息态：

1. 小扰动回到静息态。
2. 超过阈值后出现一次大幅响应。
3. 响应后进入恢复期，再回到静息态。

FitzHugh-Nagumo 型快慢系统写成


<img src="https://www.zhihu.com/equation?tex=\dot u=F(u,v),
\qquad
\dot v=\epsilon G(u,v),
\qquad
0<\epsilon\ll1.
" alt="\dot u=F(u,v),
\qquad
\dot v=\epsilon G(u,v),
\qquad
0<\epsilon\ll1.
" class="ee_img tr_noresize" eeimg="1">

 <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1">  是快变量，负责快速激发； <img src="https://www.zhihu.com/equation?tex=v" alt="v" class="ee_img tr_noresize" eeimg="1">  是慢变量，负责恢复。加上扩散后，一个点的激发可以触发邻近点，这就是触发波和螺旋波的基础。

![可激发系统：阈值、大响应与恢复期](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/17_excitable_media.png)

### 5.3 Oregonator：化学振荡中的 Hopf 与可激发性

化学振荡模型里常出现快慢结构。例如某个 Oregonator 形式可抽象为


<img src="https://www.zhihu.com/equation?tex=\epsilon\dot x=F(x,z;f,q),
\qquad
\dot z=x-z.
" alt="\epsilon\dot x=F(x,z;f,q),
\qquad
\dot z=x-z.
" class="ee_img tr_noresize" eeimg="1">

稳态先由  <img src="https://www.zhihu.com/equation?tex=z=x" alt="z=x" class="ee_img tr_noresize" eeimg="1">  给出，再代入  <img src="https://www.zhihu.com/equation?tex=F=0" alt="F=0" class="ee_img tr_noresize" eeimg="1"> 。若


<img src="https://www.zhihu.com/equation?tex=F(x,z)=x-x^2-fz\frac{x-q}{x+q},
" alt="F(x,z)=x-x^2-fz\frac{x-q}{x+q},
" class="ee_img tr_noresize" eeimg="1">

非零稳态满足


<img src="https://www.zhihu.com/equation?tex=f=\frac{(1-x)(x+q)}{x-q}.
" alt="f=\frac{(1-x)(x+q)}{x-q}.
" class="ee_img tr_noresize" eeimg="1">

Jacobian 可写成


<img src="https://www.zhihu.com/equation?tex=J=
\begin{pmatrix}
F_x/\epsilon&F_z/\epsilon\\
1&-1
\end{pmatrix}.
" alt="J=
\begin{pmatrix}
F_x/\epsilon&F_z/\epsilon\\
1&-1
\end{pmatrix}.
" class="ee_img tr_noresize" eeimg="1">

Hopf 临界来自


<img src="https://www.zhihu.com/equation?tex=\operatorname{tr}J=0,
\qquad
F_x=\epsilon.
" alt="\operatorname{tr}J=0,
\qquad
F_x=\epsilon.
" class="ee_img tr_noresize" eeimg="1">

代入稳态关系，就可以用一个变量确定 Hopf 点。

![Oregonator 模型中的 Hopf 临界](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/11_oregonator_hopf.png)

## 6. Hopf 分岔：焦点失稳后，轨道去哪了

Hopf 分岔描述的是：稳定焦点变成不稳定焦点时，附近产生小振幅周期运动。

线性层面，特征值为


<img src="https://www.zhihu.com/equation?tex=\lambda_\pm=\alpha(\mu)\pm i\omega(\mu).
" alt="\lambda_\pm=\alpha(\mu)\pm i\omega(\mu).
" class="ee_img tr_noresize" eeimg="1">

当


<img src="https://www.zhihu.com/equation?tex=\alpha(0)=0,
\qquad
\omega(0)\ne0,
\qquad
\alpha'(0)\ne0,
" alt="\alpha(0)=0,
\qquad
\omega(0)\ne0,
\qquad
\alpha'(0)\ne0,
" class="ee_img tr_noresize" eeimg="1">

焦点稳定性穿过临界。

### 6.1 Hopf 的真正机制

线性分析只说明“轨道向内螺旋”变成“轨道向外螺旋”。它没有回答：向外螺旋的轨道最后在哪里停住。

把临界二维变量合成


<img src="https://www.zhihu.com/equation?tex=z=x+iy.
" alt="z=x+iy.
" class="ee_img tr_noresize" eeimg="1">

Hopf 点附近的正则形为


<img src="https://www.zhihu.com/equation?tex=\dot z=(\mu+i\omega)z+\ell z|z|^2+O(|z|^4).
" alt="\dot z=(\mu+i\omega)z+\ell z|z|^2+O(|z|^4).
" class="ee_img tr_noresize" eeimg="1">

令  <img src="https://www.zhihu.com/equation?tex=z=re^{i\theta}" alt="z=re^{i\theta}" class="ee_img tr_noresize" eeimg="1"> ：


<img src="https://www.zhihu.com/equation?tex=\dot r=\mu r+a r^3+\cdots,
\qquad
\dot\theta=\omega+\cdots,
" alt="\dot r=\mu r+a r^3+\cdots,
\qquad
\dot\theta=\omega+\cdots,
" class="ee_img tr_noresize" eeimg="1">

其中  <img src="https://www.zhihu.com/equation?tex=a=\operatorname{Re}\ell" alt="a=\operatorname{Re}\ell" class="ee_img tr_noresize" eeimg="1"> 。角向方程说明系统在转；径向方程决定振幅长大还是饱和。

![Hopf 机制：焦点失稳后由非线性项决定振幅](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/14_hopf_mechanism.png)

### 6.2 超临界与亚临界

超临界 Hopf：


<img src="https://www.zhihu.com/equation?tex=\dot r=\mu r-r^3.
" alt="\dot r=\mu r-r^3.
" class="ee_img tr_noresize" eeimg="1">

当  <img src="https://www.zhihu.com/equation?tex=\mu>0" alt="\mu>0" class="ee_img tr_noresize" eeimg="1"> ，出现稳定小环


<img src="https://www.zhihu.com/equation?tex=r=\sqrt\mu.
" alt="r=\sqrt\mu.
" class="ee_img tr_noresize" eeimg="1">

振幅从零连续长大，起振温和。

亚临界 Hopf 常写成


<img src="https://www.zhihu.com/equation?tex=\dot r=\mu r+r^3-r^5.
" alt="\dot r=\mu r+r^3-r^5.
" class="ee_img tr_noresize" eeimg="1">

小的不稳定环与远处稳定大环共同存在。参数穿过临界后，原点失稳，轨道可能突然跳到大振幅吸引子，并伴随滞后。

![超临界 Hopf 与亚临界 Hopf 的分支图](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/04_hopf_supercritical_subcritical.png)

### 6.3 例题：Hopf 周期为什么有限

Hopf 新生环很小，但角速度接近  <img src="https://www.zhihu.com/equation?tex=\omega" alt="\omega" class="ee_img tr_noresize" eeimg="1"> ，因此周期近似为


<img src="https://www.zhihu.com/equation?tex=T\approx\frac{2\pi}\omega.
" alt="T\approx\frac{2\pi}\omega.
" class="ee_img tr_noresize" eeimg="1">

这点很重要：Hopf 起振时周期通常有限。后面同宿分岔和 SNIC 的周期会趋于无穷，区别就在于它们的轨道撞上了慢区或零速度点。

## 7. 周期运动怎样消失：同宿、SNIC、倍周期

Hopf 讲的是周期运动如何从不动点附近出现。接下来问：一个已有周期运动还能怎样改变或消失？

### 7.1 同宿分岔：极限环贴上鞍点

鞍点有稳定流形和不稳定流形。如果某个参数下，不稳定流形从鞍点出发，绕一圈后又接回同一个鞍点的稳定流形，就形成同宿轨道。

分岔过程是：

1. 临界前有普通极限环。
2. 极限环逐渐靠近鞍点。
3. 临界时极限环碰到鞍点，变成同宿环。
4. 临界后闭轨断开，极限环消失。

![同宿分岔：极限环撞上鞍点](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/15_homoclinic_bifurcation.png)

为什么周期发散？轨道经过鞍点附近时速度很小。若离鞍点距离为  <img src="https://www.zhihu.com/equation?tex=\delta" alt="\delta" class="ee_img tr_noresize" eeimg="1"> ，沿不稳定方向离开的时间近似为


<img src="https://www.zhihu.com/equation?tex=T_{\rm slow}\sim\frac1{\lambda_u}\ln\frac1\delta.
" alt="T_{\rm slow}\sim\frac1{\lambda_u}\ln\frac1\delta.
" class="ee_img tr_noresize" eeimg="1">

而  <img src="https://www.zhihu.com/equation?tex=\delta" alt="\delta" class="ee_img tr_noresize" eeimg="1">  与参数距离成正比，因此


<img src="https://www.zhihu.com/equation?tex=T\sim-\frac1{\lambda_u}\ln|\mu-\mu_c|.
" alt="T\sim-\frac1{\lambda_u}\ln|\mu-\mu_c|.
" class="ee_img tr_noresize" eeimg="1">

同宿分岔的标志是对数发散。

### 7.2 SNIC / 无限周期：环上的鞍结慢区

SNIC 是 Saddle-Node on an Invariant Circle，即不变环上的鞍结分岔。它也常叫无限周期分岔。

临界前，系统沿环运动；接近临界时，环上某段速度越来越小；临界时环上出现鞍结点，轨道到了那里就停住，绕一圈时间趋于无穷；临界后环断开，系统停在稳定结点。

![SNIC 分岔：极限环撞上环上的鞍结点](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/16_snic_bifurcation.png)

局部正则形为


<img src="https://www.zhihu.com/equation?tex=\dot x=\mu+x^2.
" alt="\dot x=\mu+x^2.
" class="ee_img tr_noresize" eeimg="1">

穿过慢区的时间为


<img src="https://www.zhihu.com/equation?tex=T\sim\int\frac{dx}{\mu+x^2}
=\frac\pi{\sqrt\mu}.
" alt="T\sim\int\frac{dx}{\mu+x^2}
=\frac\pi{\sqrt\mu}.
" class="ee_img tr_noresize" eeimg="1">

因此 SNIC 的周期是幂律发散：


<img src="https://www.zhihu.com/equation?tex=T\sim\frac1{\sqrt{\mu-\mu_c}}.
" alt="T\sim\frac1{\sqrt{\mu-\mu_c}}.
" class="ee_img tr_noresize" eeimg="1">

这也解释了神经元 Type I 兴奋性：振荡频率可以从零连续升起，因为周期可以变成无穷大。

### 7.3 倍周期：绕两圈才回到原处

取 Poincare 截面，周期轨道变成映射的不动点：


<img src="https://www.zhihu.com/equation?tex=s_{n+1}=P(s_n).
" alt="s_{n+1}=P(s_n).
" class="ee_img tr_noresize" eeimg="1">

稳定性由乘子  <img src="https://www.zhihu.com/equation?tex=P'(s^*)" alt="P'(s^*)" class="ee_img tr_noresize" eeimg="1">  决定。若


<img src="https://www.zhihu.com/equation?tex=P'(s^*)=-1,
" alt="P'(s^*)=-1,
" class="ee_img tr_noresize" eeimg="1">

截面上的扰动每绕一圈翻到不动点另一侧，第二圈再翻回来，于是出现“绕两圈才闭合”的新周期轨道。这就是倍周期分岔。

连续倍周期可形成


<img src="https://www.zhihu.com/equation?tex=1\to2\to4\to8\to\cdots
" alt="1\to2\to4\to8\to\cdots
" class="ee_img tr_noresize" eeimg="1">

的级联，是通向混沌的常见路线。

### 7.4 五种振荡机制对照

| 机制 | 发生了什么 | 起始周期 | 起始振幅 |

|---|---|---:|---:|

| 超临界 Hopf | 焦点失稳，长出稳定小环 | 有限 | 从 0 连续长大 |

| 亚临界 Hopf | 焦点失稳，跳到远处大环 | 有限 | 突然有限大 |

| 极限环鞍结 | 稳定环与不稳定环碰撞 | 有限 | 有限 |

| SNIC | 环撞上鞍结慢区 | 无穷 | 有限 |

| 同宿 | 环撞上鞍点 | 无穷 | 有限 |


这张表的用法是：先问“是焦点附近的小振幅问题，还是已有环撞上了某种零速度结构？”再判断周期是有限还是发散。

## 8. 高维、中心流形与 Lorenz 混沌

二维自治连续系统受 Poincare-Bendixson 定理限制，不能产生真正混沌。要出现混沌，至少需要三维自治系统，或非自治系统、延迟系统、映射等有效高维结构。

### 8.1 中心流形：高维分岔为什么能降维

高维系统在不动点附近线性化：


<img src="https://www.zhihu.com/equation?tex=\dot{\boldsymbol\eta}=J\boldsymbol\eta.
" alt="\dot{\boldsymbol\eta}=J\boldsymbol\eta.
" class="ee_img tr_noresize" eeimg="1">

特征值实部为负的方向快速衰减；实部为正的方向快速离开；真正决定局部分岔的是实部为零的临界方向。由这些临界方向张成的不变曲面就是中心流形。

中心流形维度等于临界特征值的个数：

| 分岔 | 临界特征值 | 中心流形维度 |

|---|---|---:|

| 鞍结、跨临界、叉形 | 一个零特征值 | 1 |

| Hopf | 一对纯虚特征值  <img src="https://www.zhihu.com/equation?tex=\pm i\omega" alt="\pm i\omega" class="ee_img tr_noresize" eeimg="1">  | 2 |


所以无论原系统是几维，普通 Hopf 分岔的核心动力学都在二维中心流形上。

### 8.2 吸引子与奇异吸引子

吸引子是长期吸引附近轨道的不变集合。它可以是稳定不动点、稳定极限环、环面，也可以是奇异吸引子。

奇异吸引子的特征是：

1. 轨道被吸引到有限区域。
2. 长期运动不周期。
3. 对初值敏感，最大 Lyapunov 指数为正。
4. 几何结构通常具有分形特征。

二维自治连续系统可以有极限环，但没有真正奇异吸引子；三维及以上可以有点、环、环面和奇异吸引子。

### 8.3 Lorenz 系统

Lorenz 系统为


<img src="https://www.zhihu.com/equation?tex=\dot x=\sigma(y-x),
" alt="\dot x=\sigma(y-x),
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\dot y=rx-y-xz,
" alt="\dot y=rx-y-xz,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\dot z=xy-bz.
" alt="\dot z=xy-bz.
" class="ee_img tr_noresize" eeimg="1">

![Lorenz 吸引子：三维自治系统中的折叠与拉伸](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/06_lorenz_attractor.png)

不动点由  <img src="https://www.zhihu.com/equation?tex=y=x" alt="y=x" class="ee_img tr_noresize" eeimg="1">  和  <img src="https://www.zhihu.com/equation?tex=z=x^2/b" alt="z=x^2/b" class="ee_img tr_noresize" eeimg="1">  推出。一个解是原点；当  <img src="https://www.zhihu.com/equation?tex=r>1" alt="r>1" class="ee_img tr_noresize" eeimg="1"> ，还有


<img src="https://www.zhihu.com/equation?tex=C_\pm=
\left(
\pm\sqrt{b(r-1)},
\pm\sqrt{b(r-1)},
r-1
\right).
" alt="C_\pm=
\left(
\pm\sqrt{b(r-1)},
\pm\sqrt{b(r-1)},
r-1
\right).
" class="ee_img tr_noresize" eeimg="1">

标准参数  <img src="https://www.zhihu.com/equation?tex=\sigma=10" alt="\sigma=10" class="ee_img tr_noresize" eeimg="1"> 、 <img src="https://www.zhihu.com/equation?tex=b=8/3" alt="b=8/3" class="ee_img tr_noresize" eeimg="1">  下，非零平衡点在


<img src="https://www.zhihu.com/equation?tex=r_H=
\frac{\sigma(\sigma+b+3)}{\sigma-b-1}
\approx24.74
" alt="r_H=
\frac{\sigma(\sigma+b+3)}{\sigma-b-1}
\approx24.74
" class="ee_img tr_noresize" eeimg="1">

附近发生 Hopf 失稳。经典混沌图像常取  <img src="https://www.zhihu.com/equation?tex=r=28" alt="r=28" class="ee_img tr_noresize" eeimg="1"> 。

Lorenz 系统是耗散的，因为


<img src="https://www.zhihu.com/equation?tex=\nabla\cdot\mathbf F=-\sigma-1-b<0.
" alt="\nabla\cdot\mathbf F=-\sigma-1-b<0.
" class="ee_img tr_noresize" eeimg="1">

相空间体积收缩，但轨道又不断被拉伸和折叠，于是形成奇异吸引子。

## 9. 延迟系统：过去状态怎样制造振荡

延迟方程的当前变化率依赖过去状态，例如


<img src="https://www.zhihu.com/equation?tex=\frac{dy}{dt}=ay(t)+by(t-\tau).
" alt="\frac{dy}{dt}=ay(t)+by(t-\tau).
" class="ee_img tr_noresize" eeimg="1">

只知道  <img src="https://www.zhihu.com/equation?tex=y(t)" alt="y(t)" class="ee_img tr_noresize" eeimg="1">  不足以预测未来，还需要知道整段历史  <img src="https://www.zhihu.com/equation?tex=y(s)" alt="y(s)" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=s\in[t-\tau,t]" alt="s\in[t-\tau,t]" class="ee_img tr_noresize" eeimg="1"> 。因此延迟系统等价于无限维系统。

### 9.1 特征方程为什么是超越方程

代入指数试探


<img src="https://www.zhihu.com/equation?tex=y(t)=e^{\lambda t},
\qquad
y(t-\tau)=e^{\lambda(t-\tau)}=e^{\lambda t}e^{-\lambda\tau}.
" alt="y(t)=e^{\lambda t},
\qquad
y(t-\tau)=e^{\lambda(t-\tau)}=e^{\lambda t}e^{-\lambda\tau}.
" class="ee_img tr_noresize" eeimg="1">

得到


<img src="https://www.zhihu.com/equation?tex=\lambda=a+be^{-\lambda\tau}.
" alt="\lambda=a+be^{-\lambda\tau}.
" class="ee_img tr_noresize" eeimg="1">

这不是有限阶多项式，因为含有  <img src="https://www.zhihu.com/equation?tex=e^{-\lambda\tau}" alt="e^{-\lambda\tau}" class="ee_img tr_noresize" eeimg="1"> 。

Hopf 临界令


<img src="https://www.zhihu.com/equation?tex=\lambda=i\omega.
" alt="\lambda=i\omega.
" class="ee_img tr_noresize" eeimg="1">

分离实部和虚部：


<img src="https://www.zhihu.com/equation?tex=0=a+b\cos(\omega\tau),
" alt="0=a+b\cos(\omega\tau),
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\omega=-b\sin(\omega\tau).
" alt="\omega=-b\sin(\omega\tau).
" class="ee_img tr_noresize" eeimg="1">

因此


<img src="https://www.zhihu.com/equation?tex=\omega^2=b^2-a^2.
" alt="\omega^2=b^2-a^2.
" class="ee_img tr_noresize" eeimg="1">

要有 Hopf，需要  <img src="https://www.zhihu.com/equation?tex=b^2>a^2" alt="b^2>a^2" class="ee_img tr_noresize" eeimg="1"> 。临界延迟满足


<img src="https://www.zhihu.com/equation?tex=\omega\tau_n=\arccos\left(-\frac ab\right)+2\pi n,
" alt="\omega\tau_n=\arccos\left(-\frac ab\right)+2\pi n,
" class="ee_img tr_noresize" eeimg="1">

并结合虚部符号选取对应分支。

![延迟负反馈导致 Hopf：超越特征方程的临界根](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/12_delay_hopf.png)

### 9.2 例题：自抑制基因为什么会振荡

基因负反馈可抽象为


<img src="https://www.zhihu.com/equation?tex=\dot x=\frac{\alpha}{1+x(t-\tau)^n}-dx.
" alt="\dot x=\frac{\alpha}{1+x(t-\tau)^n}-dx.
" class="ee_img tr_noresize" eeimg="1">

稳态  <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1">  满足


<img src="https://www.zhihu.com/equation?tex=dx^*=\frac{\alpha}{1+(x^*)^n}.
" alt="dx^*=\frac{\alpha}{1+(x^*)^n}.
" class="ee_img tr_noresize" eeimg="1">

令  <img src="https://www.zhihu.com/equation?tex=x=x^*+u" alt="x=x^*+u" class="ee_img tr_noresize" eeimg="1"> ，线性化得


<img src="https://www.zhihu.com/equation?tex=u'(t)=-du(t)+cu(t-\tau),
" alt="u'(t)=-du(t)+cu(t-\tau),
" class="ee_img tr_noresize" eeimg="1">

其中


<img src="https://www.zhihu.com/equation?tex=c=
-\frac{\alpha n(x^*)^{n-1}}{(1+(x^*)^n)^2}<0.
" alt="c=
-\frac{\alpha n(x^*)^{n-1}}{(1+(x^*)^n)^2}<0.
" class="ee_img tr_noresize" eeimg="1">

这就是延迟负反馈：当前偏高不会立刻被纠正，而是过一段时间才被压低，容易压过头；偏低时也会补过头，于是产生振荡。延迟越大、反馈越强，越容易 Hopf。

## 10. 反应扩散与 Turing：扩散怎样制造空间结构

前面的系统没有空间变量。反应扩散系统把局部反应和空间扩散合在一起：


<img src="https://www.zhihu.com/equation?tex=\frac{\partial\mathbf C}{\partial t}
=\mathbf F_R(\mathbf C)+D\nabla^2\mathbf C.
" alt="\frac{\partial\mathbf C}{\partial t}
=\mathbf F_R(\mathbf C)+D\nabla^2\mathbf C.
" class="ee_img tr_noresize" eeimg="1">

两变量形式为


<img src="https://www.zhihu.com/equation?tex=\frac{\partial x}{\partial t}=f(x,y)+D_x\nabla^2x,
" alt="\frac{\partial x}{\partial t}=f(x,y)+D_x\nabla^2x,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\frac{\partial y}{\partial t}=g(x,y)+D_y\nabla^2y.
" alt="\frac{\partial y}{\partial t}=g(x,y)+D_y\nabla^2y.
" class="ee_img tr_noresize" eeimg="1">

Turing 斑图的问题是：为什么没有空间结构的均匀稳态，会对某个非零波数的扰动失稳，从而长出静止空间斑图？

![Turing 斑图：条纹与空间波长的自发选择](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/21_turing_pattern_stripes.png)

### 10.1 均匀态先要稳定

均匀稳态满足


<img src="https://www.zhihu.com/equation?tex=f(x_s,y_s)=0,
\qquad
g(x_s,y_s)=0.
" alt="f(x_s,y_s)=0,
\qquad
g(x_s,y_s)=0.
" class="ee_img tr_noresize" eeimg="1">

局部反应的 Jacobian 为


<img src="https://www.zhihu.com/equation?tex=A=
\begin{pmatrix}
a_{11}&a_{12}\\
a_{21}&a_{22}
\end{pmatrix}
=
\begin{pmatrix}
f_x&f_y\\
g_x&g_y
\end{pmatrix}_{(x_s,y_s)}.
" alt="A=
\begin{pmatrix}
a_{11}&a_{12}\\
a_{21}&a_{22}
\end{pmatrix}
=
\begin{pmatrix}
f_x&f_y\\
g_x&g_y
\end{pmatrix}_{(x_s,y_s)}.
" class="ee_img tr_noresize" eeimg="1">

没有扩散时，均匀态稳定要求


<img src="https://www.zhihu.com/equation?tex=\tau_0=a_{11}+a_{22}<0,
\qquad
\Delta_0=a_{11}a_{22}-a_{12}a_{21}>0.
" alt="\tau_0=a_{11}+a_{22}<0,
\qquad
\Delta_0=a_{11}a_{22}-a_{12}a_{21}>0.
" class="ee_img tr_noresize" eeimg="1">

### 10.2 Fourier 模式与  <img src="https://www.zhihu.com/equation?tex=J_k" alt="J_k" class="ee_img tr_noresize" eeimg="1"> 

线性化反应扩散方程：


<img src="https://www.zhihu.com/equation?tex=\frac\partial{\partial t}
\begin{pmatrix}\xi\\\eta\end{pmatrix}
=
A\begin{pmatrix}\xi\\\eta\end{pmatrix}
+
\begin{pmatrix}D_x&0\\0&D_y\end{pmatrix}
\nabla^2
\begin{pmatrix}\xi\\\eta\end{pmatrix}.
" alt="\frac\partial{\partial t}
\begin{pmatrix}\xi\\\eta\end{pmatrix}
=
A\begin{pmatrix}\xi\\\eta\end{pmatrix}
+
\begin{pmatrix}D_x&0\\0&D_y\end{pmatrix}
\nabla^2
\begin{pmatrix}\xi\\\eta\end{pmatrix}.
" class="ee_img tr_noresize" eeimg="1">

对 Fourier 模式


<img src="https://www.zhihu.com/equation?tex=\begin{pmatrix}\xi\\\eta\end{pmatrix}
=\mathbf u_k e^{\lambda t+i\mathbf k\cdot\mathbf r},
" alt="\begin{pmatrix}\xi\\\eta\end{pmatrix}
=\mathbf u_k e^{\lambda t+i\mathbf k\cdot\mathbf r},
" class="ee_img tr_noresize" eeimg="1">

有


<img src="https://www.zhihu.com/equation?tex=\nabla^2\mapsto-k^2,
" alt="\nabla^2\mapsto-k^2,
" class="ee_img tr_noresize" eeimg="1">

所以


<img src="https://www.zhihu.com/equation?tex=\lambda\mathbf u_k=(A-k^2D)\mathbf u_k.
" alt="\lambda\mathbf u_k=(A-k^2D)\mathbf u_k.
" class="ee_img tr_noresize" eeimg="1">

记


<img src="https://www.zhihu.com/equation?tex=A_k=A-k^2D.
" alt="A_k=A-k^2D.
" class="ee_img tr_noresize" eeimg="1">

每个  <img src="https://www.zhihu.com/equation?tex=k" alt="k" class="ee_img tr_noresize" eeimg="1">  都是一个二维线性稳定性问题。

### 10.3 Turing 判据

对  <img src="https://www.zhihu.com/equation?tex=A_k" alt="A_k" class="ee_img tr_noresize" eeimg="1"> ，


<img src="https://www.zhihu.com/equation?tex=\tau_k=\tau_0-(D_x+D_y)k^2.
" alt="\tau_k=\tau_0-(D_x+D_y)k^2.
" class="ee_img tr_noresize" eeimg="1">

若  <img src="https://www.zhihu.com/equation?tex=\tau_0<0" alt="\tau_0<0" class="ee_img tr_noresize" eeimg="1">  且扩散系数为正，则  <img src="https://www.zhihu.com/equation?tex=\tau_k" alt="\tau_k" class="ee_img tr_noresize" eeimg="1">  对  <img src="https://www.zhihu.com/equation?tex=k>0" alt="k>0" class="ee_img tr_noresize" eeimg="1">  更负。失稳只能来自行列式：


<img src="https://www.zhihu.com/equation?tex=\Delta_k
=\Delta_0-(D_ya_{11}+D_xa_{22})k^2+D_xD_yk^4.
" alt="\Delta_k
=\Delta_0-(D_ya_{11}+D_xa_{22})k^2+D_xD_yk^4.
" class="ee_img tr_noresize" eeimg="1">

令  <img src="https://www.zhihu.com/equation?tex=q=k^2" alt="q=k^2" class="ee_img tr_noresize" eeimg="1"> ，得到开口向上的抛物线


<img src="https://www.zhihu.com/equation?tex=\Delta(q)=\Delta_0-(D_ya_{11}+D_xa_{22})q+D_xD_yq^2.
" alt="\Delta(q)=\Delta_0-(D_ya_{11}+D_xa_{22})q+D_xD_yq^2.
" class="ee_img tr_noresize" eeimg="1">

存在  <img src="https://www.zhihu.com/equation?tex=q>0" alt="q>0" class="ee_img tr_noresize" eeimg="1">  使  <img src="https://www.zhihu.com/equation?tex=\Delta(q)<0" alt="\Delta(q)<0" class="ee_img tr_noresize" eeimg="1"> ，需要：


<img src="https://www.zhihu.com/equation?tex=D_ya_{11}+D_xa_{22}>0,
" alt="D_ya_{11}+D_xa_{22}>0,
" class="ee_img tr_noresize" eeimg="1">

并且最低点低于零：


<img src="https://www.zhihu.com/equation?tex=(D_ya_{11}+D_xa_{22})^2-4D_xD_y\Delta_0>0.
" alt="(D_ya_{11}+D_xa_{22})^2-4D_xD_y\Delta_0>0.
" class="ee_img tr_noresize" eeimg="1">

合在一起，标准 Turing 条件为


<img src="https://www.zhihu.com/equation?tex=\boxed{
\begin{aligned}
a_{11}+a_{22}&<0,\\
a_{11}a_{22}-a_{12}a_{21}&>0,\\
D_ya_{11}+D_xa_{22}&>0,\\
(D_ya_{11}+D_xa_{22})^2
-4D_xD_y(a_{11}a_{22}-a_{12}a_{21})&>0.
\end{aligned}}
" alt="\boxed{
\begin{aligned}
a_{11}+a_{22}&<0,\\
a_{11}a_{22}-a_{12}a_{21}&>0,\\
D_ya_{11}+D_xa_{22}&>0,\\
(D_ya_{11}+D_xa_{22})^2
-4D_xD_y(a_{11}a_{22}-a_{12}a_{21})&>0.
\end{aligned}}
" class="ee_img tr_noresize" eeimg="1">

如果  <img src="https://www.zhihu.com/equation?tex=D_x=D_y=D" alt="D_x=D_y=D" class="ee_img tr_noresize" eeimg="1"> ，


<img src="https://www.zhihu.com/equation?tex=A_k=A-Dk^2I,
" alt="A_k=A-Dk^2I,
" class="ee_img tr_noresize" eeimg="1">

特征值只是


<img src="https://www.zhihu.com/equation?tex=\lambda_i(k)=\lambda_i(0)-Dk^2.
" alt="\lambda_i(k)=\lambda_i(0)-Dk^2.
" class="ee_img tr_noresize" eeimg="1">

均匀态若稳定，非零模式更稳定。因此标准两变量对角扩散系统中，相同扩散不能产生 Turing 失稳。

### 10.4 最危险波数与斑图类型

临界时  <img src="https://www.zhihu.com/equation?tex=\Delta(q)" alt="\Delta(q)" class="ee_img tr_noresize" eeimg="1">  的最低点刚好碰到零。由


<img src="https://www.zhihu.com/equation?tex=\frac{d\Delta}{dq}=0
" alt="\frac{d\Delta}{dq}=0
" class="ee_img tr_noresize" eeimg="1">

得


<img src="https://www.zhihu.com/equation?tex=k_c^2=q_c
=\frac{D_ya_{11}+D_xa_{22}}{2D_xD_y}.
" alt="k_c^2=q_c
=\frac{D_ya_{11}+D_xa_{22}}{2D_xD_y}.
" class="ee_img tr_noresize" eeimg="1">

临界波长是


<img src="https://www.zhihu.com/equation?tex=\lambda_c=\frac{2\pi}{k_c}.
" alt="\lambda_c=\frac{2\pi}{k_c}.
" class="ee_img tr_noresize" eeimg="1">

线性理论选出最先增长的波数；非线性振幅方程决定最终是条纹、六角形还是混合态。临界附近常写


<img src="https://www.zhihu.com/equation?tex=\dot A=mA-g|A|^2A.
" alt="\dot A=mA-g|A|^2A.
" class="ee_img tr_noresize" eeimg="1">

若  <img src="https://www.zhihu.com/equation?tex=g>0" alt="g>0" class="ee_img tr_noresize" eeimg="1"> ，振幅饱和：


<img src="https://www.zhihu.com/equation?tex=|A|=\sqrt{\frac m g}.
" alt="|A|=\sqrt{\frac m g}.
" class="ee_img tr_noresize" eeimg="1">

二维中，多组临界波矢之间的共振会选择六角形、条纹等结构。

![Turing 斑图模拟：从随机小扰动到稳定空间结构](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/09_turing_pattern.png)

### 10.5 CIMA 实验的直觉

Turing 机制通常要求抑制子比激活子扩散更快。CIMA 实验中，加入淀粉会让碘离子与大分子形成复合物，降低激活子的有效扩散：


<img src="https://www.zhihu.com/equation?tex=D_{\rm activator,eff}\downarrow.
" alt="D_{\rm activator,eff}\downarrow.
" class="ee_img tr_noresize" eeimg="1">

这样更容易满足“快扩散抑制 + 慢扩散激活”的条件，从而观察到条纹、点阵、六角形等斑图。

## 11. Brusselator：把 Turing 判据完整算一遍

Brusselator 是最适合练反应扩散计算的模型。无量纲形式为


<img src="https://www.zhihu.com/equation?tex=\frac{\partial x}{\partial t}
=a-(1+b)x+x^2y+\nabla^2x,
" alt="\frac{\partial x}{\partial t}
=a-(1+b)x+x^2y+\nabla^2x,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\frac{\partial y}{\partial t}
=bx-x^2y+d\nabla^2y.
" alt="\frac{\partial y}{\partial t}
=bx-x^2y+d\nabla^2y.
" class="ee_img tr_noresize" eeimg="1">

### 11.1 从反应式到方程

典型反应链为


<img src="https://www.zhihu.com/equation?tex=A\to X,
\qquad
2X+Y\to3X,
\qquad
B+X\to Y+D,
\qquad
X\to E.
" alt="A\to X,
\qquad
2X+Y\to3X,
\qquad
B+X\to Y+D,
\qquad
X\to E.
" class="ee_img tr_noresize" eeimg="1">

按质量作用律，自催化反应  <img src="https://www.zhihu.com/equation?tex=2X+Y\to3X" alt="2X+Y\to3X" class="ee_img tr_noresize" eeimg="1">  的速率为  <img src="https://www.zhihu.com/equation?tex=k_2X^2Y" alt="k_2X^2Y" class="ee_img tr_noresize" eeimg="1"> ，对  <img src="https://www.zhihu.com/equation?tex=X" alt="X" class="ee_img tr_noresize" eeimg="1">  的净贡献是  <img src="https://www.zhihu.com/equation?tex=+1" alt="+1" class="ee_img tr_noresize" eeimg="1">  个  <img src="https://www.zhihu.com/equation?tex=X" alt="X" class="ee_img tr_noresize" eeimg="1"> ，对  <img src="https://www.zhihu.com/equation?tex=Y" alt="Y" class="ee_img tr_noresize" eeimg="1">  的贡献是  <img src="https://www.zhihu.com/equation?tex=-1" alt="-1" class="ee_img tr_noresize" eeimg="1">  个  <img src="https://www.zhihu.com/equation?tex=Y" alt="Y" class="ee_img tr_noresize" eeimg="1"> 。因此有量纲方程为


<img src="https://www.zhihu.com/equation?tex=\frac{\partial X}{\partial t}
=k_1A+k_2X^2Y-k_3BX-k_4X+D_X\nabla^2X,
" alt="\frac{\partial X}{\partial t}
=k_1A+k_2X^2Y-k_3BX-k_4X+D_X\nabla^2X,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\frac{\partial Y}{\partial t}
=k_3BX-k_2X^2Y+D_Y\nabla^2Y.
" alt="\frac{\partial Y}{\partial t}
=k_3BX-k_2X^2Y+D_Y\nabla^2Y.
" class="ee_img tr_noresize" eeimg="1">

无量纲化会把若干常数吸收入  <img src="https://www.zhihu.com/equation?tex=a,b" alt="a,b" class="ee_img tr_noresize" eeimg="1"> ，并把  <img src="https://www.zhihu.com/equation?tex=X" alt="X" class="ee_img tr_noresize" eeimg="1">  的扩散系数化为  <img src="https://www.zhihu.com/equation?tex=1" alt="1" class="ee_img tr_noresize" eeimg="1"> ，于是  <img src="https://www.zhihu.com/equation?tex=Y" alt="Y" class="ee_img tr_noresize" eeimg="1">  的扩散系数变成相对扩散比  <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1"> 。

### 11.2 均匀解与 Jacobian

均匀态下扩散项为零：


<img src="https://www.zhihu.com/equation?tex=a-(1+b)x+x^2y=0,
" alt="a-(1+b)x+x^2y=0,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=bx-x^2y=0.
" alt="bx-x^2y=0.
" class="ee_img tr_noresize" eeimg="1">

因为  <img src="https://www.zhihu.com/equation?tex=a>0" alt="a>0" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=x=0" alt="x=0" class="ee_img tr_noresize" eeimg="1">  不可能，所以  <img src="https://www.zhihu.com/equation?tex=xy=b" alt="xy=b" class="ee_img tr_noresize" eeimg="1"> 。代回得


<img src="https://www.zhihu.com/equation?tex=x^*=a,
\qquad
y^*=\frac ba.
" alt="x^*=a,
\qquad
y^*=\frac ba.
" class="ee_img tr_noresize" eeimg="1">

反应项


<img src="https://www.zhihu.com/equation?tex=f=a-(1+b)x+x^2y,
\qquad
g=bx-x^2y.
" alt="f=a-(1+b)x+x^2y,
\qquad
g=bx-x^2y.
" class="ee_img tr_noresize" eeimg="1">

偏导为


<img src="https://www.zhihu.com/equation?tex=f_x=-(1+b)+2xy,
\quad
f_y=x^2,
" alt="f_x=-(1+b)+2xy,
\quad
f_y=x^2,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=g_x=b-2xy,
\quad
g_y=-x^2.
" alt="g_x=b-2xy,
\quad
g_y=-x^2.
" class="ee_img tr_noresize" eeimg="1">

在稳态处：


<img src="https://www.zhihu.com/equation?tex=J=
\begin{pmatrix}
b-1&a^2\\
-b&-a^2
\end{pmatrix}.
" alt="J=
\begin{pmatrix}
b-1&a^2\\
-b&-a^2
\end{pmatrix}.
" class="ee_img tr_noresize" eeimg="1">

### 11.3 均匀 Hopf

无扩散时


<img src="https://www.zhihu.com/equation?tex=\tau_0=b-1-a^2,
\qquad
\Delta_0=a^2>0.
" alt="\tau_0=b-1-a^2,
\qquad
\Delta_0=a^2>0.
" class="ee_img tr_noresize" eeimg="1">

Hopf 临界由  <img src="https://www.zhihu.com/equation?tex=\tau_0=0" alt="\tau_0=0" class="ee_img tr_noresize" eeimg="1">  得


<img src="https://www.zhihu.com/equation?tex=b_H=1+a^2.
" alt="b_H=1+a^2.
" class="ee_img tr_noresize" eeimg="1">

在临界点特征值为


<img src="https://www.zhihu.com/equation?tex=\lambda_\pm=\pm ia.
" alt="\lambda_\pm=\pm ia.
" class="ee_img tr_noresize" eeimg="1">

### 11.4 Turing 临界

扩散矩阵为


<img src="https://www.zhihu.com/equation?tex=D=
\begin{pmatrix}
1&0\\
0&d
\end{pmatrix}.
" alt="D=
\begin{pmatrix}
1&0\\
0&d
\end{pmatrix}.
" class="ee_img tr_noresize" eeimg="1">

因此


<img src="https://www.zhihu.com/equation?tex=J_k=
\begin{pmatrix}
b-1-k^2&a^2\\
-b&-a^2-dk^2
\end{pmatrix}.
" alt="J_k=
\begin{pmatrix}
b-1-k^2&a^2\\
-b&-a^2-dk^2
\end{pmatrix}.
" class="ee_img tr_noresize" eeimg="1">

迹为


<img src="https://www.zhihu.com/equation?tex=\tau_k=b-1-a^2-(1+d)k^2.
" alt="\tau_k=b-1-a^2-(1+d)k^2.
" class="ee_img tr_noresize" eeimg="1">

若均匀反应稳定，即  <img src="https://www.zhihu.com/equation?tex=b<1+a^2" alt="b<1+a^2" class="ee_img tr_noresize" eeimg="1"> ，则  <img src="https://www.zhihu.com/equation?tex=\tau_k" alt="\tau_k" class="ee_img tr_noresize" eeimg="1">  不负责失稳。关键看


<img src="https://www.zhihu.com/equation?tex=\Delta_k
=a^2+[a^2-d(b-1)]k^2+dk^4.
" alt="\Delta_k
=a^2+[a^2-d(b-1)]k^2+dk^4.
" class="ee_img tr_noresize" eeimg="1">

令  <img src="https://www.zhihu.com/equation?tex=q=k^2" alt="q=k^2" class="ee_img tr_noresize" eeimg="1"> ：


<img src="https://www.zhihu.com/equation?tex=\Delta(q)=a^2+[a^2-d(b-1)]q+dq^2.
" alt="\Delta(q)=a^2+[a^2-d(b-1)]q+dq^2.
" class="ee_img tr_noresize" eeimg="1">

Turing 临界要求最低点碰零：


<img src="https://www.zhihu.com/equation?tex=\Delta(q_c)=0,
\qquad
\Delta'(q_c)=0.
" alt="\Delta(q_c)=0,
\qquad
\Delta'(q_c)=0.
" class="ee_img tr_noresize" eeimg="1">

由导数


<img src="https://www.zhihu.com/equation?tex=q_c=\frac{d(b-1)-a^2}{2d}.
" alt="q_c=\frac{d(b-1)-a^2}{2d}.
" class="ee_img tr_noresize" eeimg="1">

判别式为零：


<img src="https://www.zhihu.com/equation?tex=[a^2-d(b-1)]^2-4da^2=0.
" alt="[a^2-d(b-1)]^2-4da^2=0.
" class="ee_img tr_noresize" eeimg="1">

取使  <img src="https://www.zhihu.com/equation?tex=q_c>0" alt="q_c>0" class="ee_img tr_noresize" eeimg="1">  的分支：


<img src="https://www.zhihu.com/equation?tex=d(b-1)-a^2=2a\sqrt d.
" alt="d(b-1)-a^2=2a\sqrt d.
" class="ee_img tr_noresize" eeimg="1">

所以


<img src="https://www.zhihu.com/equation?tex=b_T=1+\frac{a^2}d+\frac{2a}{\sqrt d},
" alt="b_T=1+\frac{a^2}d+\frac{2a}{\sqrt d},
" class="ee_img tr_noresize" eeimg="1">

并且


<img src="https://www.zhihu.com/equation?tex=k_c^2=q_c=\frac a{\sqrt d}.
" alt="k_c^2=q_c=\frac a{\sqrt d}.
" class="ee_img tr_noresize" eeimg="1">

![Brusselator 的 Hopf 临界、Turing 临界与最危险波数](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/08_brusselator_turing_analysis.png)

Brusselator 的速查表是：


<img src="https://www.zhihu.com/equation?tex=\boxed{
\begin{aligned}
x^*&=a,\qquad y^*=\frac ba,\\
J&=
\begin{pmatrix}
b-1&a^2\\
-b&-a^2
\end{pmatrix},\\
b_H&=1+a^2,\\
b_T&=1+\frac{a^2}d+\frac{2a}{\sqrt d},\\
k_c^2&=\frac a{\sqrt d}.
\end{aligned}}
" alt="\boxed{
\begin{aligned}
x^*&=a,\qquad y^*=\frac ba,\\
J&=
\begin{pmatrix}
b-1&a^2\\
-b&-a^2
\end{pmatrix},\\
b_H&=1+a^2,\\
b_T&=1+\frac{a^2}d+\frac{2a}{\sqrt d},\\
k_c^2&=\frac a{\sqrt d}.
\end{aligned}}
" class="ee_img tr_noresize" eeimg="1">

要真正出现扩散诱导斑图，需要 Turing 临界先于均匀 Hopf 临界：


<img src="https://www.zhihu.com/equation?tex=b_T<b_H.
" alt="b_T<b_H.
" class="ee_img tr_noresize" eeimg="1">

这通常要求  <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1">  足够大，也就是  <img src="https://www.zhihu.com/equation?tex=y" alt="y" class="ee_img tr_noresize" eeimg="1">  比  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  扩散快得多。

## 12. 行波：PDE 怎样变成 ODE，波速从哪里来

Turing 斑图是静止空间结构。接下来讨论会动的空间结构：触发波、行波、波列、螺旋波。

### 12.1 可激发介质中的触发波

加扩散的 FitzHugh-Nagumo 型系统可写成


<img src="https://www.zhihu.com/equation?tex=\frac{\partial u}{\partial t}
=F(u,v)+D_u\nabla^2u,
" alt="\frac{\partial u}{\partial t}
=F(u,v)+D_u\nabla^2u,
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\frac{\partial v}{\partial t}
=\epsilon G(u,v)+D_v\nabla^2v.
" alt="\frac{\partial v}{\partial t}
=\epsilon G(u,v)+D_v\nabla^2v.
" class="ee_img tr_noresize" eeimg="1">

局部系统有稳定静息态和阈值。超过阈值的点发生大响应，并通过扩散把激发传给邻近点，于是形成触发波。

![FitzHugh-Nagumo 介质中的波前与螺旋几何](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/10_fhn_spiral_geometry.png)

### 12.2 行波变换

一维行波形状不变、整体平移。设


<img src="https://www.zhihu.com/equation?tex=z=x-ct,
\qquad
u(x,t)=U(z),
\qquad
v(x,t)=V(z).
" alt="z=x-ct,
\qquad
u(x,t)=U(z),
\qquad
v(x,t)=V(z).
" class="ee_img tr_noresize" eeimg="1">

则


<img src="https://www.zhihu.com/equation?tex=\frac{\partial u}{\partial t}=-cU',
\qquad
\frac{\partial^2u}{\partial x^2}=U''.
" alt="\frac{\partial u}{\partial t}=-cU',
\qquad
\frac{\partial^2u}{\partial x^2}=U''.
" class="ee_img tr_noresize" eeimg="1">

PDE 变为 ODE：


<img src="https://www.zhihu.com/equation?tex=-cU'=F(U,V)+D_uU'',
" alt="-cU'=F(U,V)+D_uU'',
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=-cV'=\epsilon G(U,V)+D_vV''.
" alt="-cV'=\epsilon G(U,V)+D_vV''.
" class="ee_img tr_noresize" eeimg="1">

这里波速  <img src="https://www.zhihu.com/equation?tex=c" alt="c" class="ee_img tr_noresize" eeimg="1">  不是随便给的，而是和波形一起由边界条件选出来的本征值。

### 12.3 面积判据与 Luther 关系

对双稳前沿


<img src="https://www.zhihu.com/equation?tex=DU''+cU'+f(U)=0,
" alt="DU''+cU'+f(U)=0,
" class="ee_img tr_noresize" eeimg="1">

乘以  <img src="https://www.zhihu.com/equation?tex=U'" alt="U'" class="ee_img tr_noresize" eeimg="1">  并积分：


<img src="https://www.zhihu.com/equation?tex=c\int_{-\infty}^\infty (U')^2dz
+
\int_{U(-\infty)}^{U(\infty)} f(U)dU=0.
" alt="c\int_{-\infty}^\infty (U')^2dz
+
\int_{U(-\infty)}^{U(\infty)} f(U)dU=0.
" class="ee_img tr_noresize" eeimg="1">

因此


<img src="https://www.zhihu.com/equation?tex=c=
-\frac{\int_{U(-\infty)}^{U(\infty)} f(U)dU}
{\int_{-\infty}^\infty (U')^2dz}.
" alt="c=
-\frac{\int_{U(-\infty)}^{U(\infty)} f(U)dU}
{\int_{-\infty}^\infty (U')^2dz}.
" class="ee_img tr_noresize" eeimg="1">

分母为正，波速方向由反应项曲线下的有符号面积决定。

Luther 关系给出速度量级：


<img src="https://www.zhihu.com/equation?tex=c\sim\sqrt{D\cdot\text{reaction rate}}.
" alt="c\sim\sqrt{D\cdot\text{reaction rate}}.
" class="ee_img tr_noresize" eeimg="1">

扩散决定激发传播距离，反应速率决定前方被点燃的快慢。

### 12.4 波列色散关系

周期性刺激产生波列。刺激周期太短时，介质还没恢复，下一波传播会变慢甚至失败；刺激周期足够长时，波速接近孤立脉冲速度。因此可写


<img src="https://www.zhihu.com/equation?tex=c=c(T).
" alt="c=c(T).
" class="ee_img tr_noresize" eeimg="1">

这和 Turing 的  <img src="https://www.zhihu.com/equation?tex=\lambda(k)" alt="\lambda(k)" class="ee_img tr_noresize" eeimg="1">  不同。Turing 色散关系描述空间模式增长率；这里描述波速随刺激周期或波列波数的变化。

## 13. 程函关系与螺旋波

二维波前的速度会受曲率影响。取波前法向坐标  <img src="https://www.zhihu.com/equation?tex=n" alt="n" class="ee_img tr_noresize" eeimg="1">  和切向坐标  <img src="https://www.zhihu.com/equation?tex=s" alt="s" class="ee_img tr_noresize" eeimg="1"> ，Laplacian 近似为


<img src="https://www.zhihu.com/equation?tex=\nabla^2\approx
\frac{\partial^2}{\partial n^2}
+\kappa\frac\partial{\partial n}
+\cdots.
" alt="\nabla^2\approx
\frac{\partial^2}{\partial n^2}
+\kappa\frac\partial{\partial n}
+\cdots.
" class="ee_img tr_noresize" eeimg="1">

曲率项会修正一维平面波速度，得到程函关系：


<img src="https://www.zhihu.com/equation?tex=\boxed{c_n=c_0-D_{\rm eff}\kappa}.
" alt="\boxed{c_n=c_0-D_{\rm eff}\kappa}.
" class="ee_img tr_noresize" eeimg="1">

其中  <img src="https://www.zhihu.com/equation?tex=c_n" alt="c_n" class="ee_img tr_noresize" eeimg="1">  是法向速度， <img src="https://www.zhihu.com/equation?tex=c_0" alt="c_0" class="ee_img tr_noresize" eeimg="1">  是平面波速度， <img src="https://www.zhihu.com/equation?tex=\kappa" alt="\kappa" class="ee_img tr_noresize" eeimg="1">  是曲率， <img src="https://www.zhihu.com/equation?tex=D_{\rm eff}>0" alt="D_{\rm eff}>0" class="ee_img tr_noresize" eeimg="1">  是有效扩散系数。

![程函关系：曲率如何修正波前法向速度](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/18_eikonal_relation.png)

### 13.1 为什么行波通常稳定

若波前出现局部凸起，曲率较大，程函关系使它传播变慢；凹陷处相对更快。于是凸起被拖住，凹陷追上，波前趋于平坦。这就是平面行波对横向扰动通常稳定的几何原因。

如果某些系统中有效曲率系数符号反过来，凸起更快、凹陷更慢，扰动会放大，出现横向不稳定和迷宫状前沿。

### 13.2 螺旋波如何诞生

在可激发介质中，完整波前会向前传播。如果波前被切断，断端成为自由端。波前中段仍向前走，自由端因为没有完整邻近约束而绕转，最终形成螺旋。

![螺旋波诞生：断裂波前产生自由端](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/19_spiral_birth.png)

成熟螺旋波的中心是相位奇点：绕核心走一圈，相位累计变化  <img src="https://www.zhihu.com/equation?tex=2\pi" alt="2\pi" class="ee_img tr_noresize" eeimg="1"> ，但核心点本身无法定义普通相位。

![成熟螺旋波：相位奇点与旋转波臂](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/非线性物理从0到1知乎讲义/20_spiral_mature.png)

相位可写成


<img src="https://www.zhihu.com/equation?tex=\Phi=m\theta+\Omega t+\psi(r).
" alt="\Phi=m\theta+\Omega t+\psi(r).
" class="ee_img tr_noresize" eeimg="1">

等相位线  <img src="https://www.zhihu.com/equation?tex=\Phi=\text{constant}" alt="\Phi=\text{constant}" class="ee_img tr_noresize" eeimg="1">  就是螺旋臂。远离核心时，螺旋局部像平面波；近核心处曲率很大，必须由程函关系约束。

### 13.3 哪些介质容易产生螺旋波

可激发介质最典型：阈值、恢复期和断裂波前共同提供旋转自由端。

振荡介质也能产生螺旋波：局部系统 Hopf 后有极限环，每个空间点都有相位；相位奇点会组织出螺旋波。近 Hopf 时，慢振幅常由复 Ginzburg-Landau 方程描述：


<img src="https://www.zhihu.com/equation?tex=\frac{\partial A}{\partial t}
=\mu A+(1+i\alpha)\nabla^2A-(1+i\beta)|A|^2A.
" alt="\frac{\partial A}{\partial t}
=\mu A+(1+i\alpha)\nabla^2A-(1+i\beta)|A|^2A.
" class="ee_img tr_noresize" eeimg="1">

平面波解可写成


<img src="https://www.zhihu.com/equation?tex=A=R e^{i(\mathbf q\cdot\mathbf r-\Omega t)}.
" alt="A=R e^{i(\mathbf q\cdot\mathbf r-\Omega t)}.
" class="ee_img tr_noresize" eeimg="1">

不同波数的稳定性会出现 Eckhaus、Benjamin-Feir、对流不稳定、绝对不稳定等现象；在图像上表现为稳定螺旋、漂移螺旋、螺旋破碎与湍动。

## 14. 双稳前沿、Ising-Bloch 与 Faraday 斑图

双稳系统有两个稳定均匀态，前沿连接二者：


<img src="https://www.zhihu.com/equation?tex=\text{state 1}
\longleftrightarrow
\text{state 2}.
" alt="\text{state 1}
\longleftrightarrow
\text{state 2}.
" class="ee_img tr_noresize" eeimg="1">

前沿速度由两侧状态的势差或面积差决定。二维中曲率仍会修正速度。对称前沿常称 Ising front；运动前沿常称 Bloch front；两者之间的转变叫 Ising-Bloch transition。在非对称情形下，这种转变可以呈现鞍结样结构。

### 14.1 Faraday 斑图是什么

Faraday 斑图来自周期外驱动：竖直方向周期性振动液体，当驱动超过阈值，液面出现驻波斑图，例如条纹、方格、六角形。

它和 Turing、Hopf 的区别是：


<img src="https://www.zhihu.com/equation?tex=\text{Hopf: 自治系统的时间振荡}
" alt="\text{Hopf: 自治系统的时间振荡}
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\text{Turing: 自治反应扩散系统的静止空间斑图}
" alt="\text{Turing: 自治反应扩散系统的静止空间斑图}
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\text{Faraday: 周期外驱动系统中的驻波斑图}
" alt="\text{Faraday: 周期外驱动系统中的驻波斑图}
" class="ee_img tr_noresize" eeimg="1">

### 14.2 为什么是鞍结样失稳

对平液面态做线性稳定性分析，扰动写成


<img src="https://www.zhihu.com/equation?tex=\delta A\sim e^{\lambda t+i\mathbf k\cdot\mathbf r}.
" alt="\delta A\sim e^{\lambda t+i\mathbf k\cdot\mathbf r}.
" class="ee_img tr_noresize" eeimg="1">

黏性耗散会压低振荡型复根的实部，因此失稳通常不是一对复特征值穿过虚轴的普通 Hopf。临界时更像某个实特征值过零，新的驻波解出现，因此常称为鞍结样分岔。

Faraday 和 Turing 相似之处在于：两者都会选择一个临界波数  <img src="https://www.zhihu.com/equation?tex=k_c" alt="k_c" class="ee_img tr_noresize" eeimg="1"> ，最终形成空间图案。不同之处在于：Turing 是扩散诱导的自治失稳，Faraday 是周期外驱动下的参数激发。

## 15. 从模型到判断：把全书连成一套工作流

面对一个新的非线性模型，可以按下面的顺序读：

1. **没有空间、没有延迟**：先找不动点，算 Jacobian。
2. **一维系统**：看  <img src="https://www.zhihu.com/equation?tex=f=0" alt="f=0" class="ee_img tr_noresize" eeimg="1">  的根如何随参数改变，判断鞍结、跨临界、叉形。
3. **二维局部问题**：用  <img src="https://www.zhihu.com/equation?tex=\tau,\Delta" alt="\tau,\Delta" class="ee_img tr_noresize" eeimg="1">  分类； <img src="https://www.zhihu.com/equation?tex=\tau=0,\Delta>0" alt="\tau=0,\Delta>0" class="ee_img tr_noresize" eeimg="1">  是 Hopf 的入口。
4. **二维全局问题**：用 Poincare-Bendixson、Dulac、势函数、指数判断闭轨。
5. **已有周期运动**：用 Poincare 映射和 Floquet 乘子判断倍周期、环面分岔或极限环鞍结。
6. **周期变得很长**：问轨道撞上的是鞍点还是鞍结慢区。同宿给对数发散，SNIC 给  <img src="https://www.zhihu.com/equation?tex=1/\sqrt{}" alt="1/\sqrt{}" class="ee_img tr_noresize" eeimg="1">  发散。
7. **高维系统**：用中心流形降到临界方向；三维以上可能有混沌。
8. **延迟系统**：代入  <img src="https://www.zhihu.com/equation?tex=e^{\lambda t}" alt="e^{\lambda t}" class="ee_img tr_noresize" eeimg="1"> ，得到含  <img src="https://www.zhihu.com/equation?tex=e^{-\lambda\tau}" alt="e^{-\lambda\tau}" class="ee_img tr_noresize" eeimg="1">  的特征方程。
9. **反应扩散系统**：找均匀态，算  <img src="https://www.zhihu.com/equation?tex=J-k^2D" alt="J-k^2D" class="ee_img tr_noresize" eeimg="1"> ，比较 Hopf、Turing、wave instability。
10. **会动的空间结构**：用行波变换、程函关系和相位奇点理解波、前沿、螺旋。

### 15.1 概念速查

| 概念 | 一句话 |

|---|---|

| 不动点 | 速度为零的点 |

| 稳定性 | 小扰动是否回到原结构 |

| 分岔 | 参数变化导致相空间拓扑结构改变 |

| 极限环 | 孤立闭轨，代表自维持周期运动 |

| Hopf | 焦点失稳，非线性项决定小环是否稳定 |

| 同宿 | 极限环撞上鞍点，周期对数发散 |

| SNIC | 环上发生鞍结，周期按  <img src="https://www.zhihu.com/equation?tex=1/\sqrt{}" alt="1/\sqrt{}" class="ee_img tr_noresize" eeimg="1">  发散 |

| 倍周期 | Floquet 乘子穿过  <img src="https://www.zhihu.com/equation?tex=-1" alt="-1" class="ee_img tr_noresize" eeimg="1"> ，绕两圈闭合 |

| 中心流形 | 临界慢方向构成的低维不变曲面 |

| 奇异吸引子 | 吸引但混沌、常带分形结构的集合 |

| Turing | 均匀态稳定，但某个  <img src="https://www.zhihu.com/equation?tex=k\ne0" alt="k\ne0" class="ee_img tr_noresize" eeimg="1">  模式被扩散放大 |

| 程函关系 | 曲率修正波前法向速度 |

| 螺旋波 | 波前自由端或相位奇点组织出的旋转波 |


### 15.2 最后一页：不要背孤立公式

非线性物理最有用的不是某个孤立公式，而是公式背后的入口问题：


<img src="https://www.zhihu.com/equation?tex=f=0 \Rightarrow \text{不动点},
\qquad
f_x=0 \Rightarrow \text{根结构可能改变},
" alt="f=0 \Rightarrow \text{不动点},
\qquad
f_x=0 \Rightarrow \text{根结构可能改变},
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=\tau=0,\Delta>0 \Rightarrow \text{Hopf 入口},
\qquad
J-k^2D \Rightarrow \text{空间模式稳定性},
" alt="\tau=0,\Delta>0 \Rightarrow \text{Hopf 入口},
\qquad
J-k^2D \Rightarrow \text{空间模式稳定性},
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=e^{\lambda t} \Rightarrow \text{线性增长率},
\qquad
e^{-\lambda\tau} \Rightarrow \text{延迟系统},
" alt="e^{\lambda t} \Rightarrow \text{线性增长率},
\qquad
e^{-\lambda\tau} \Rightarrow \text{延迟系统},
" class="ee_img tr_noresize" eeimg="1">


<img src="https://www.zhihu.com/equation?tex=c_n=c_0-D_{\rm eff}\kappa \Rightarrow \text{曲率调速},
\qquad
\Phi=m\theta+\Omega t+\psi(r) \Rightarrow \text{螺旋相位}.
" alt="c_n=c_0-D_{\rm eff}\kappa \Rightarrow \text{曲率调速},
\qquad
\Phi=m\theta+\Omega t+\psi(r) \Rightarrow \text{螺旋相位}.
" class="ee_img tr_noresize" eeimg="1">

把这些入口串起来，就能从零开始读懂非线性物理：先看相空间，再看分岔；先看局部稳定性，再看全局结构；先看均匀态，再看空间模式；先看平面波，再看弯曲波前和螺旋波。
