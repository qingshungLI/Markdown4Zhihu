# 非线性物理从 0 到 1：从相空间到混沌与斑图

非线性物理不是一门“把方程解出来”的课。多数时候，方程根本没有漂亮的解析解；真正重要的是看出系统的长期命运：它会停在稳态、绕成周期运动、突然跳变、进入混沌，还是在空间中自发长出斑图与螺旋波。

这份讲义按一条主线写：

$$
\text{相空间}
\rightarrow
\text{不动点与分岔}
\rightarrow
\text{振荡与极限环}
\rightarrow
\text{混沌}
\rightarrow
\text{反应扩散与时空结构}
$$

所有公式都服务于一个问题：当参数改变时，速度场的结构怎样改变？只要抓住这件事，鞍结、Hopf、同宿、SNIC、Turing、螺旋波就不再是零散名词，而是一套连续的图像。

![吸引子的几种典型形态：点、环、环面与奇异吸引子](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_01.jpg)

## 0. 先建立地图：非线性系统到底看什么

一个自治动力系统写成

$$
\dot{\mathbf x}=\mathbf F(\mathbf x;\mu),
$$

其中 $\mathbf x$ 是状态，$\mu$ 是控制参量。相空间中每个点都挂着一个速度箭头 $\mathbf F$，轨道就是沿箭头走出的曲线。

初学时最容易被公式淹没。先记住七个动作：

1. 设右端为零，找不动点或均匀稳态。
2. 在线性近似下算 Jacobian。
3. 用特征值、迹、行列式判断局部稳定性。
4. 参数变化时，盯住特征值是否碰到临界位置：$0$ 或虚轴。
5. 一旦线性项失效，就看最低阶非线性项，也就是正则形。
6. 加上空间扩散时，把扰动拆成 Fourier 模式，令 $\nabla^2\mapsto -k^2$。
7. 有延迟时，代入指数试探 $e^{\lambda t}$，特征方程里会出现 $e^{-\lambda\tau}$。

贯穿全书的统一直觉是：

> 定性变化来自“速度为零或接近为零的地方”如何出现、消失、碰撞、改变稳定性。

不动点是严格零速度点；极限环是一条速度不为零但绕回原处的闭轨；慢区是速度很小、轨道会在那里停留很久的区域。后面所有分岔都可以用这三类对象解释。

## 1. 一维流：从“根”读懂分岔

一维自治系统是

$$
\dot x=f(x;r).
$$

不动点满足

$$
f(x^*;r)=0.
$$

令 $x=x^*+\eta$，保留一阶项：

$$
\dot\eta=f_x(x^*;r)\eta,
\qquad
\eta(t)=\eta(0)e^{f_x(x^*;r)t}.
$$

因此：

$$
f_x(x^*;r)<0 \Rightarrow \text{稳定},
\qquad
f_x(x^*;r)>0 \Rightarrow \text{不稳定}.
$$

如果 $f_x=0$，一阶判据失效，常常意味着分岔。图像上，一维分岔就是 $f(x;r)$ 与 $x$ 轴的交点结构发生改变。

![一维常见分岔：鞍结、跨临界、超临界叉形、亚临界叉形](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_02.jpg)

### 1.1 为什么根的数目会改变

普通根是横截交点。参数轻微改变时，横截交点只会平滑移动，不会突然消失。要让两个根相遇并消失，曲线必须与 $x$ 轴相切：

$$
f(x^*;r^*)=0,
\qquad
f_x(x^*;r^*)=0.
$$

这就是鞍结等局部分岔的基本条件。

把分岔点平移到 $(x,r)=(0,0)$，Taylor 展开：

$$
\dot x=f(x;r)=ar+bx^2+\cdots.
$$

经过缩放，最低阶结构化成

$$
\dot x=r\pm x^2.
$$

这就是正则形：保留改变局部拓扑结构的最低阶项，丢掉不影响类型的细节。

### 1.2 四种基本一维分岔

**鞍结分岔。**

$$
\dot x=r-x^2.
$$

当 $r>0$ 时，

$$
x_\pm=\pm\sqrt r,
\qquad
f_x=-2x.
$$

所以 $x_+=\sqrt r$ 稳定，$x_-=-\sqrt r$ 不稳定。$r\to0^+$ 时一稳一不稳碰撞，$r<0$ 后根消失。

**跨临界分岔。**

$$
\dot x=rx-x^2=x(r-x).
$$

两条分支 $x=0$ 与 $x=r$ 始终存在，在 $r=0$ 交换稳定性。它常出现于“两个状态都有物理意义，并在临界处互换角色”的问题。

**超临界叉形分岔。**

$$
\dot x=rx-x^3.
$$

当 $r<0$ 时只有稳定原点；当 $r>0$ 时原点失稳，出现两个稳定非零态：

$$
x=\pm\sqrt r.
$$

这是对称系统中“一个中心态分裂成两个对称稳定态”的典型图像。

**亚临界叉形分岔。**

$$
\dot x=rx+x^3.
$$

非零分支出现在 $r<0$，但它们不稳定；$r>0$ 后原点也不稳定。真实系统通常还要靠更高阶项把远处振幅限制住，因此亚临界结构常伴随跳变与滞后。

### 1.3 不完美叉形：对称性被打破会怎样

完美叉形依赖 $x\mapsto -x$ 对称。如果加入二次项，

$$
\dot x=rx+ax^2-x^3,
$$

对称性被破坏。此时不动点为

$$
x=0,
\qquad
x=\frac{a\pm\sqrt{a^2+4r}}2.
$$

非零分支存在条件是

$$
a^2+4r\ge0,
\qquad
r\ge-\frac{a^2}4.
$$

这条边界是两条非零分支相切合并的位置，也就是鞍结曲线。原本一个完美叉形被拆成“一个跨临界结构 + 一个鞍结结构”。

![不完美叉形：对称性破缺后分支被拆开](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_03.jpg)

### 1.4 例题：锁相、过阻尼摆与慢区

相位锁定问题常化成一维方程：

$$
\dot\phi=\Delta\omega-K\sin\phi.
$$

不动点存在要求

$$
|\Delta\omega|\le K.
$$

等号处两个相位锁定点碰撞消失，是鞍结分岔。若 $|\Delta\omega|>K$，相位差无法停住，会持续滑移。

过阻尼摆也有同样结构：

$$
\dot\theta=\Omega-\sin\theta.
$$

当 $|\Omega|<1$，有静止角度；当 $|\Omega|>1$，摆会持续转动。临界 $|\Omega|=1$ 附近，系统经过某一角度时速度极小，这就是慢区。穿过慢区的时间满足

$$
T\sim\int\frac{d\theta}{\Omega-\sin\theta},
$$

并在临界附近变得很长。这个图像会在 SNIC 分岔里再次出现。

## 2. 二维线性系统：迹、行列式和相图分类

二维线性系统写成

$$
\dot{\mathbf x}=A\mathbf x,
\qquad
A=
\begin{pmatrix}
a&b\\
c&d
\end{pmatrix}.
$$

特征方程为

$$
\lambda^2-\tau\lambda+\Delta=0,
\qquad
\tau=a+d,
\quad
\Delta=ad-bc.
$$

因此所有局部类型都由迹 $\tau$ 和行列式 $\Delta$ 决定。

![二维线性系统分类：迹-行列式平面](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_04.jpg)

### 2.1 分类从哪里来

如果 $\Delta<0$，两个特征值一正一负，轨道沿一个方向进、另一个方向出，是鞍点。

如果 $\Delta>0$ 且 $\tau<0$，两个特征值实部都为负，是稳定结点或稳定焦点。

如果 $\Delta>0$ 且 $\tau>0$，两个特征值实部都为正，是不稳定结点或不稳定焦点。

区分结点和焦点看判别式：

$$
\tau^2-4\Delta.
$$

若它为正，特征值为实数，是结点；若为负，特征值为共轭复数，是焦点；若 $\tau=0$ 且 $\Delta>0$，特征值为纯虚数，是中心或 Hopf 临界的线性部分。

### 2.2 例题：为什么 Hopf 在二维里写成 $\tau=0,\Delta>0$

二维特征值可写成

$$
\lambda_\pm=\frac\tau2\pm\frac12\sqrt{\tau^2-4\Delta}.
$$

Hopf 要求一对复特征值穿过虚轴，因此在临界点：

$$
\operatorname{Re}\lambda_\pm=\frac\tau2=0.
$$

同时要是复数而不是两个实数，所以

$$
\Delta>0.
$$

再加上穿越条件：

$$
\frac{d\tau}{d\mu}\ne0.
$$

但这只说明焦点稳定性改变，不能说明出现稳定环还是不稳定环。后者要看非线性项。

## 3. 二维非线性系统：零解线、线性化与相平面

二维非线性系统写成

$$
\dot x=f(x,y),
\qquad
\dot y=g(x,y).
$$

不动点由

$$
f(x,y)=0,
\qquad
g(x,y)=0
$$

共同确定。两条曲线分别叫 $x$ 零解线和 $y$ 零解线，它们的交点就是不动点。

在不动点 $(x^*,y^*)$ 附近线性化：

$$
\begin{pmatrix}\dot\xi\\\dot\eta\end{pmatrix}
=
J
\begin{pmatrix}\xi\\\eta\end{pmatrix},
\qquad
J=
\begin{pmatrix}
f_x&f_y\\
g_x&g_y
\end{pmatrix}_{(x^*,y^*)}.
$$

局部稳定性由 $J$ 的特征值决定。

### 3.1 相平面操作顺序

分析一个二维非线性模型，按下面顺序最稳：

1. 画或求 $f=0$、$g=0$ 两条零解线。
2. 找交点。
3. 在交点处算 Jacobian。
4. 用 $\tau,\Delta$ 判断局部类型。
5. 再看全局约束：是否存在闭轨、轨道是否被困在有界区域、是否存在势函数或 Dulac 函数。

### 3.2 例题：一个带参数的二维分岔系统

设

$$
\dot x=-x+2y+x^2,
$$

$$
\dot y=(2-\alpha)x-y-3x^2+\frac32xy.
$$

从第一式零解线得

$$
y=\frac{x-x^2}2.
$$

代入第二式，得到分支关系

$$
x\left(-\alpha+\frac32-\frac74x-\frac34x^2\right)=0.
$$

所以原点一直存在，非零分支满足

$$
\alpha=\frac32-\frac74x-\frac34x^2.
$$

原点处

$$
J_0=
\begin{pmatrix}
-1&2\\
2-\alpha&-1
\end{pmatrix},
\qquad
\Delta_0=2\alpha-3.
$$

因此 $\alpha=3/2$ 是零特征值分岔点。

非零分支上的鞍结来自分支曲线相切：

$$
\frac{d\alpha}{dx}=-\frac74-\frac32x=0,
\qquad
x=-\frac76.
$$

代回得到

$$
\alpha=\frac{121}{48}.
$$

非零分支上的 Hopf 来自迹为零。Jacobian 的迹是

$$
\tau=-2+\frac72x.
$$

令 $\tau=0$ 得

$$
x=\frac47,
\qquad
\alpha=\frac{25}{98}.
$$

这个例子把“零解线、分支、鞍结、Hopf”放在同一个模型里，适合反复练。

![参数分岔例子：分支、稳定性与临界点](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_05.jpg)

## 4. 势、梯度系统、Dulac 与指数：闭轨能不能存在

线性化只能告诉我们不动点附近发生什么。要判断系统有没有极限环，需要全局工具。

### 4.1 梯度系统为什么没有稳定极限环

若系统能写成

$$
\dot{\mathbf x}=-\nabla V(\mathbf x),
$$

则

$$
\frac{dV}{dt}
=\nabla V\cdot\dot{\mathbf x}
=-|\nabla V|^2\le0.
$$

沿轨道势函数单调下降，除非到达不动点，否则不能回到原来的 $V$ 值。因此非平凡周期轨不存在。稳定极限环不是梯度系统的产物。

二维向量场 $\mathbf F=(P,Q)$ 若要来自势函数，常用交叉偏导检查：

$$
\frac{\partial P}{\partial y}
=
\frac{\partial Q}{\partial x}
$$

或在负梯度约定下相差一个整体符号。

### 4.2 Dulac 判据

在单连通区域 $R$ 内，若存在函数 $B(x,y)$ 使

$$
\frac{\partial (Bf)}{\partial x}
+\frac{\partial (Bg)}{\partial y}
$$

不变号且不恒为零，则该区域内没有闭轨。

直觉来自 Green 定理：如果存在闭轨，向量场沿闭轨切向流动，法向通量为零；但散度在内部积分若严格同号，就会给出非零通量，矛盾。

### 4.3 Poincare-Bendixson 与指数

Poincare-Bendixson 定理说：二维自治系统中，若一条轨道被困在不含不动点的有界闭区域内，则它的极限集是闭轨。它常用来证明极限环存在。

指数理论则限制闭轨内部的不动点配置。一条简单闭轨的指标为 $+1$。稳定结点、源、焦点、中心的指标都是 $+1$；鞍点指标是 $-1$。因此闭轨内部孤立不动点的指标和必须为

$$
+1.
$$

例如，一个极限环内部不能只有一个鞍点，因为指标为 $-1$；可以有一个焦点，也可以有两个结点加一个鞍点。

![Poincare 映射与全局分岔：从闭轨到截面](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_06.jpg)

## 5. 极限环与自激振荡：Van der Pol、Lienard、可激发系统

极限环是一条孤立闭轨：

$$
\mathbf x(t+T)=\mathbf x(t).
$$

如果附近轨道都趋向它，就是稳定极限环，对应自激振荡。

### 5.1 Lienard 与 Van der Pol：小振幅供能，大振幅耗能

Lienard 方程常写成

$$
x''+f(x)x'+g(x)=0.
$$

Van der Pol 方程是最典型的例子：

$$
x''-\mu(1-x^2)x'+x=0,
\qquad
\mu>0.
$$

把阻尼项看成

$$
-\mu(1-x^2)x'.
$$

当 $|x|<1$，等效阻尼为负，系统从外界吸收能量；当 $|x|>1$，等效阻尼为正，系统耗散能量。于是小振幅被放大，大振幅被压回，最终形成稳定极限环。

![Van der Pol 振子：相平面中的稳定极限环](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_07.jpg)

### 5.2 可激发系统：稳定点也能产生大响应

可激发系统不是自振荡系统。单个局部系统通常只有一个稳定静息态：

1. 小扰动回到静息态。
2. 超过阈值后出现一次大幅响应。
3. 响应后进入恢复期，再回到静息态。

FitzHugh-Nagumo 型快慢系统写成

$$
\dot u=F(u,v),
\qquad
\dot v=\epsilon G(u,v),
\qquad
0<\epsilon\ll1.
$$

$u$ 是快变量，负责快速激发；$v$ 是慢变量，负责恢复。加上扩散后，一个点的激发可以触发邻近点，这就是触发波和螺旋波的基础。

![可激发系统：阈值、大响应与恢复期](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_08.jpg)

### 5.3 Oregonator：化学振荡中的 Hopf 与可激发性

化学振荡模型里常出现快慢结构。例如某个 Oregonator 形式可抽象为

$$
\epsilon\dot x=F(x,z;f,q),
\qquad
\dot z=x-z.
$$

稳态先由 $z=x$ 给出，再代入 $F=0$。若

$$
F(x,z)=x-x^2-fz\frac{x-q}{x+q},
$$

非零稳态满足

$$
f=\frac{(1-x)(x+q)}{x-q}.
$$

Jacobian 可写成

$$
J=
\begin{pmatrix}
F_x/\epsilon&F_z/\epsilon\\
1&-1
\end{pmatrix}.
$$

Hopf 临界来自

$$
\operatorname{tr}J=0,
\qquad
F_x=\epsilon.
$$

代入稳态关系，就可以用一个变量确定 Hopf 点。

![Oregonator 模型中的 Hopf 临界](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_09.jpg)

## 6. Hopf 分岔：焦点失稳后，轨道去哪了

Hopf 分岔描述的是：稳定焦点变成不稳定焦点时，附近产生小振幅周期运动。

线性层面，特征值为

$$
\lambda_\pm=\alpha(\mu)\pm i\omega(\mu).
$$

当

$$
\alpha(0)=0,
\qquad
\omega(0)\ne0,
\qquad
\alpha'(0)\ne0,
$$

焦点稳定性穿过临界。

### 6.1 Hopf 的真正机制

线性分析只说明“轨道向内螺旋”变成“轨道向外螺旋”。它没有回答：向外螺旋的轨道最后在哪里停住。

把临界二维变量合成

$$
z=x+iy.
$$

Hopf 点附近的正则形为

$$
\dot z=(\mu+i\omega)z+\ell z|z|^2+O(|z|^4).
$$

令 $z=re^{i\theta}$：

$$
\dot r=\mu r+a r^3+\cdots,
\qquad
\dot\theta=\omega+\cdots,
$$

其中 $a=\operatorname{Re}\ell$。角向方程说明系统在转；径向方程决定振幅长大还是饱和。

![Hopf 机制：焦点失稳后由非线性项决定振幅](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_10.jpg)

### 6.2 超临界与亚临界

超临界 Hopf：

$$
\dot r=\mu r-r^3.
$$

当 $\mu>0$，出现稳定小环

$$
r=\sqrt\mu.
$$

振幅从零连续长大，起振温和。

亚临界 Hopf 常写成

$$
\dot r=\mu r+r^3-r^5.
$$

小的不稳定环与远处稳定大环共同存在。参数穿过临界后，原点失稳，轨道可能突然跳到大振幅吸引子，并伴随滞后。

![超临界 Hopf 与亚临界 Hopf 的分支图](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_11.jpg)

### 6.3 例题：Hopf 周期为什么有限

Hopf 新生环很小，但角速度接近 $\omega$，因此周期近似为

$$
T\approx\frac{2\pi}\omega.
$$

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

![同宿分岔：极限环撞上鞍点](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_12.jpg)

为什么周期发散？轨道经过鞍点附近时速度很小。若离鞍点距离为 $\delta$，沿不稳定方向离开的时间近似为

$$
T_{\rm slow}\sim\frac1{\lambda_u}\ln\frac1\delta.
$$

而 $\delta$ 与参数距离成正比，因此

$$
T\sim-\frac1{\lambda_u}\ln|\mu-\mu_c|.
$$

同宿分岔的标志是对数发散。

### 7.2 SNIC / 无限周期：环上的鞍结慢区

SNIC 是 Saddle-Node on an Invariant Circle，即不变环上的鞍结分岔。它也常叫无限周期分岔。

临界前，系统沿环运动；接近临界时，环上某段速度越来越小；临界时环上出现鞍结点，轨道到了那里就停住，绕一圈时间趋于无穷；临界后环断开，系统停在稳定结点。

![SNIC 分岔：极限环撞上环上的鞍结点](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_13.jpg)

局部正则形为

$$
\dot x=\mu+x^2.
$$

穿过慢区的时间为

$$
T\sim\int\frac{dx}{\mu+x^2}
=\frac\pi{\sqrt\mu}.
$$

因此 SNIC 的周期是幂律发散：

$$
T\sim\frac1{\sqrt{\mu-\mu_c}}.
$$

这也解释了神经元 Type I 兴奋性：振荡频率可以从零连续升起，因为周期可以变成无穷大。

### 7.3 倍周期：绕两圈才回到原处

取 Poincare 截面，周期轨道变成映射的不动点：

$$
s_{n+1}=P(s_n).
$$

稳定性由乘子 $P'(s^*)$ 决定。若

$$
P'(s^*)=-1,
$$

截面上的扰动每绕一圈翻到不动点另一侧，第二圈再翻回来，于是出现“绕两圈才闭合”的新周期轨道。这就是倍周期分岔。

连续倍周期可形成

$$
1\to2\to4\to8\to\cdots
$$

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

$$
\dot{\boldsymbol\eta}=J\boldsymbol\eta.
$$

特征值实部为负的方向快速衰减；实部为正的方向快速离开；真正决定局部分岔的是实部为零的临界方向。由这些临界方向张成的不变曲面就是中心流形。

中心流形维度等于临界特征值的个数：

| 分岔 | 临界特征值 | 中心流形维度 |
|---|---|---:|
| 鞍结、跨临界、叉形 | 一个零特征值 | 1 |
| Hopf | 一对纯虚特征值 $\pm i\omega$ | 2 |

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

$$
\dot x=\sigma(y-x),
$$

$$
\dot y=rx-y-xz,
$$

$$
\dot z=xy-bz.
$$

![Lorenz 吸引子：三维自治系统中的折叠与拉伸](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_14.jpg)

不动点由 $y=x$ 和 $z=x^2/b$ 推出。一个解是原点；当 $r>1$，还有

$$
C_\pm=
\left(
\pm\sqrt{b(r-1)},
\pm\sqrt{b(r-1)},
r-1
\right).
$$

标准参数 $\sigma=10$、$b=8/3$ 下，非零平衡点在

$$
r_H=
\frac{\sigma(\sigma+b+3)}{\sigma-b-1}
\approx24.74
$$

附近发生 Hopf 失稳。经典混沌图像常取 $r=28$。

Lorenz 系统是耗散的，因为

$$
\nabla\cdot\mathbf F=-\sigma-1-b<0.
$$

相空间体积收缩，但轨道又不断被拉伸和折叠，于是形成奇异吸引子。

## 9. 延迟系统：过去状态怎样制造振荡

延迟方程的当前变化率依赖过去状态，例如

$$
\frac{dy}{dt}=ay(t)+by(t-\tau).
$$

只知道 $y(t)$ 不足以预测未来，还需要知道整段历史 $y(s)$，$s\in[t-\tau,t]$。因此延迟系统等价于无限维系统。

### 9.1 特征方程为什么是超越方程

代入指数试探

$$
y(t)=e^{\lambda t},
\qquad
y(t-\tau)=e^{\lambda(t-\tau)}=e^{\lambda t}e^{-\lambda\tau}.
$$

得到

$$
\lambda=a+be^{-\lambda\tau}.
$$

这不是有限阶多项式，因为含有 $e^{-\lambda\tau}$。

Hopf 临界令

$$
\lambda=i\omega.
$$

分离实部和虚部：

$$
0=a+b\cos(\omega\tau),
$$

$$
\omega=-b\sin(\omega\tau).
$$

因此

$$
\omega^2=b^2-a^2.
$$

要有 Hopf，需要 $b^2>a^2$。临界延迟满足

$$
\omega\tau_n=\arccos\left(-\frac ab\right)+2\pi n,
$$

并结合虚部符号选取对应分支。

![延迟负反馈导致 Hopf：超越特征方程的临界根](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_15.jpg)

### 9.2 例题：自抑制基因为什么会振荡

基因负反馈可抽象为

$$
\dot x=\frac{\alpha}{1+x(t-\tau)^n}-dx.
$$

稳态 $x^*$ 满足

$$
dx^*=\frac{\alpha}{1+(x^*)^n}.
$$

令 $x=x^*+u$，线性化得

$$
u'(t)=-du(t)+cu(t-\tau),
$$

其中

$$
c=
-\frac{\alpha n(x^*)^{n-1}}{(1+(x^*)^n)^2}<0.
$$

这就是延迟负反馈：当前偏高不会立刻被纠正，而是过一段时间才被压低，容易压过头；偏低时也会补过头，于是产生振荡。延迟越大、反馈越强，越容易 Hopf。

## 10. 反应扩散与 Turing：扩散怎样制造空间结构

前面的系统没有空间变量。反应扩散系统把局部反应和空间扩散合在一起：

$$
\frac{\partial\mathbf C}{\partial t}
=\mathbf F_R(\mathbf C)+D\nabla^2\mathbf C.
$$

两变量形式为

$$
\frac{\partial x}{\partial t}=f(x,y)+D_x\nabla^2x,
$$

$$
\frac{\partial y}{\partial t}=g(x,y)+D_y\nabla^2y.
$$

Turing 斑图的问题是：为什么没有空间结构的均匀稳态，会对某个非零波数的扰动失稳，从而长出静止空间斑图？

![Turing 斑图：条纹与空间波长的自发选择](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_16.jpg)

### 10.1 均匀态先要稳定

均匀稳态满足

$$
f(x_s,y_s)=0,
\qquad
g(x_s,y_s)=0.
$$

局部反应的 Jacobian 为

$$
A=
\begin{pmatrix}
a_{11}&a_{12}\\
a_{21}&a_{22}
\end{pmatrix}
=
\begin{pmatrix}
f_x&f_y\\
g_x&g_y
\end{pmatrix}_{(x_s,y_s)}.
$$

没有扩散时，均匀态稳定要求

$$
\tau_0=a_{11}+a_{22}<0,
\qquad
\Delta_0=a_{11}a_{22}-a_{12}a_{21}>0.
$$

### 10.2 Fourier 模式与 $J_k$

线性化反应扩散方程：

$$
\frac{\partial}{\partial t}
\begin{pmatrix}\xi\\\eta\end{pmatrix}
=
A\begin{pmatrix}\xi\\\eta\end{pmatrix}
+
\begin{pmatrix}
D_x&0\\
0&D_y
\end{pmatrix}
\nabla^2
\begin{pmatrix}\xi\\\eta\end{pmatrix}.
$$

对 Fourier 模式

$$
\begin{pmatrix}\xi\\\eta\end{pmatrix}
=\mathbf u_k e^{\lambda t+i\mathbf k\cdot\mathbf r},
$$

有

$$
\nabla^2\mapsto-k^2,
$$

所以

$$
\lambda\mathbf u_k=(A-k^2D)\mathbf u_k.
$$

记

$$
A_k=A-k^2D.
$$

每个 $k$ 都是一个二维线性稳定性问题。

### 10.3 Turing 判据

对 $A_k$，

$$
\tau_k=\tau_0-(D_x+D_y)k^2.
$$

若 $\tau_0<0$ 且扩散系数为正，则 $\tau_k$ 对 $k>0$ 更负。失稳只能来自行列式：

$$
\Delta_k
=\Delta_0-(D_ya_{11}+D_xa_{22})k^2+D_xD_yk^4.
$$

令 $q=k^2$，得到开口向上的抛物线

$$
\Delta(q)=\Delta_0-(D_ya_{11}+D_xa_{22})q+D_xD_yq^2.
$$

存在 $q>0$ 使 $\Delta(q)<0$，需要：

$$
D_ya_{11}+D_xa_{22}>0,
$$

并且最低点低于零：

$$
(D_ya_{11}+D_xa_{22})^2-4D_xD_y\Delta_0>0.
$$

合在一起，标准 Turing 条件为

$$
\boxed{
\begin{aligned}
a_{11}+a_{22}&<0,\\
a_{11}a_{22}-a_{12}a_{21}&>0,\\
D_ya_{11}+D_xa_{22}&>0,\\
(D_ya_{11}+D_xa_{22})^2
-4D_xD_y(a_{11}a_{22}-a_{12}a_{21})&>0.
\end{aligned}}
$$

如果 $D_x=D_y=D$，

$$
A_k=A-Dk^2I,
$$

特征值只是

$$
\lambda_i(k)=\lambda_i(0)-Dk^2.
$$

均匀态若稳定，非零模式更稳定。因此标准两变量对角扩散系统中，相同扩散不能产生 Turing 失稳。

### 10.4 最危险波数与斑图类型

临界时 $\Delta(q)$ 的最低点刚好碰到零。由

$$
\frac{d\Delta}{dq}=0
$$

得

$$
k_c^2=q_c
=\frac{D_ya_{11}+D_xa_{22}}{2D_xD_y}.
$$

临界波长是

$$
\lambda_c=\frac{2\pi}{k_c}.
$$

线性理论选出最先增长的波数；非线性振幅方程决定最终是条纹、六角形还是混合态。临界附近常写

$$
\dot A=mA-g|A|^2A.
$$

若 $g>0$，振幅饱和：

$$
|A|=\sqrt{\frac m g}.
$$

二维中，多组临界波矢之间的共振会选择六角形、条纹等结构。

![Turing 斑图模拟：从随机小扰动到稳定空间结构](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_17.jpg)

### 10.5 CIMA 实验的直觉

Turing 机制通常要求抑制子比激活子扩散更快。CIMA 实验中，加入淀粉会让碘离子与大分子形成复合物，降低激活子的有效扩散：

$$
D_{\rm activator,eff}\downarrow.
$$

这样更容易满足“快扩散抑制 + 慢扩散激活”的条件，从而观察到条纹、点阵、六角形等斑图。

## 11. Brusselator：把 Turing 判据完整算一遍

Brusselator 是最适合练反应扩散计算的模型。无量纲形式为

$$
\frac{\partial x}{\partial t}
=a-(1+b)x+x^2y+\nabla^2x,
$$

$$
\frac{\partial y}{\partial t}
=bx-x^2y+d\nabla^2y.
$$

### 11.1 从反应式到方程

典型反应链为

$$
A\to X,
\qquad
2X+Y\to3X,
\qquad
B+X\to Y+D,
\qquad
X\to E.
$$

按质量作用律，自催化反应 $2X+Y\to3X$ 的速率为 $k_2X^2Y$，对 $X$ 的净贡献是 $+1$ 个 $X$，对 $Y$ 的贡献是 $-1$ 个 $Y$。因此有量纲方程为

$$
\frac{\partial X}{\partial t}
=k_1A+k_2X^2Y-k_3BX-k_4X+D_X\nabla^2X,
$$

$$
\frac{\partial Y}{\partial t}
=k_3BX-k_2X^2Y+D_Y\nabla^2Y.
$$

无量纲化会把若干常数吸收入 $a,b$，并把 $X$ 的扩散系数化为 $1$，于是 $Y$ 的扩散系数变成相对扩散比 $d$。

### 11.2 均匀解与 Jacobian

均匀态下扩散项为零：

$$
a-(1+b)x+x^2y=0,
$$

$$
bx-x^2y=0.
$$

因为 $a>0$，$x=0$ 不可能，所以 $xy=b$。代回得

$$
x^*=a,
\qquad
y^*=\frac ba.
$$

反应项

$$
f=a-(1+b)x+x^2y,
\qquad
g=bx-x^2y.
$$

偏导为

$$
f_x=-(1+b)+2xy,
\quad
f_y=x^2,
$$

$$
g_x=b-2xy,
\quad
g_y=-x^2.
$$

在稳态处：

$$
J=
\begin{pmatrix}
b-1&a^2\\
-b&-a^2
\end{pmatrix}.
$$

### 11.3 均匀 Hopf

无扩散时

$$
\tau_0=b-1-a^2,
\qquad
\Delta_0=a^2>0.
$$

Hopf 临界由 $\tau_0=0$ 得

$$
b_H=1+a^2.
$$

在临界点特征值为

$$
\lambda_\pm=\pm ia.
$$

### 11.4 Turing 临界

扩散矩阵为

$$
D=
\begin{pmatrix}
1&0\\
0&d
\end{pmatrix}.
$$

因此

$$
J_k=
\begin{pmatrix}
b-1-k^2&a^2\\
-b&-a^2-dk^2
\end{pmatrix}.
$$

迹为

$$
\tau_k=b-1-a^2-(1+d)k^2.
$$

若均匀反应稳定，即 $b<1+a^2$，则 $\tau_k$ 不负责失稳。关键看

$$
\Delta_k
=a^2+[a^2-d(b-1)]k^2+dk^4.
$$

令 $q=k^2$：

$$
\Delta(q)=a^2+[a^2-d(b-1)]q+dq^2.
$$

Turing 临界要求最低点碰零：

$$
\Delta(q_c)=0,
\qquad
\Delta'(q_c)=0.
$$

由导数

$$
q_c=\frac{d(b-1)-a^2}{2d}.
$$

判别式为零：

$$
[a^2-d(b-1)]^2-4da^2=0.
$$

取使 $q_c>0$ 的分支：

$$
d(b-1)-a^2=2a\sqrt d.
$$

所以

$$
b_T=1+\frac{a^2}d+\frac{2a}{\sqrt d},
$$

并且

$$
k_c^2=q_c=\frac a{\sqrt d}.
$$

![Brusselator 的 Hopf 临界、Turing 临界与最危险波数](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_18.jpg)

Brusselator 的速查表是：

$$
\boxed{
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
$$

要真正出现扩散诱导斑图，需要 Turing 临界先于均匀 Hopf 临界：

$$
b_T<b_H.
$$

这通常要求 $d$ 足够大，也就是 $y$ 比 $x$ 扩散快得多。

## 12. 行波：PDE 怎样变成 ODE，波速从哪里来

Turing 斑图是静止空间结构。接下来讨论会动的空间结构：触发波、行波、波列、螺旋波。

### 12.1 可激发介质中的触发波

加扩散的 FitzHugh-Nagumo 型系统可写成

$$
\frac{\partial u}{\partial t}
=F(u,v)+D_u\nabla^2u,
$$

$$
\frac{\partial v}{\partial t}
=\epsilon G(u,v)+D_v\nabla^2v.
$$

局部系统有稳定静息态和阈值。超过阈值的点发生大响应，并通过扩散把激发传给邻近点，于是形成触发波。

![FitzHugh-Nagumo 介质中的波前与螺旋几何](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_19.jpg)

### 12.2 行波变换

一维行波形状不变、整体平移。设

$$
z=x-ct,
\qquad
u(x,t)=U(z),
\qquad
v(x,t)=V(z).
$$

则

$$
\frac{\partial u}{\partial t}=-cU',
\qquad
\frac{\partial^2u}{\partial x^2}=U''.
$$

PDE 变为 ODE：

$$
-cU'=F(U,V)+D_uU'',
$$

$$
-cV'=\epsilon G(U,V)+D_vV''.
$$

这里波速 $c$ 不是随便给的，而是和波形一起由边界条件选出来的本征值。

### 12.3 面积判据与 Luther 关系

对双稳前沿

$$
DU''+cU'+f(U)=0,
$$

乘以 $U'$ 并积分：

$$
c\int_{-\infty}^\infty (U')^2dz
+
\int_{U(-\infty)}^{U(\infty)} f(U)dU=0.
$$

因此

$$
c=
-\frac{\int_{U(-\infty)}^{U(\infty)} f(U)dU}
{\int_{-\infty}^\infty (U')^2dz}.
$$

分母为正，波速方向由反应项曲线下的有符号面积决定。

Luther 关系给出速度量级：

$$
c\sim\sqrt{D\cdot\text{reaction rate}}.
$$

扩散决定激发传播距离，反应速率决定前方被点燃的快慢。

### 12.4 波列色散关系

周期性刺激产生波列。刺激周期太短时，介质还没恢复，下一波传播会变慢甚至失败；刺激周期足够长时，波速接近孤立脉冲速度。因此可写

$$
c=c(T).
$$

这和 Turing 的 $\lambda(k)$ 不同。Turing 色散关系描述空间模式增长率；这里描述波速随刺激周期或波列波数的变化。

## 13. 程函关系与螺旋波

二维波前的速度会受曲率影响。取波前法向坐标 $n$ 和切向坐标 $s$，Laplacian 近似为

$$
\nabla^2\approx
\frac{\partial^2}{\partial n^2}
+\kappa\frac\partial{\partial n}
+\cdots.
$$

曲率项会修正一维平面波速度，得到程函关系：

$$
\boxed{c_n=c_0-D_{\rm eff}\kappa}.
$$

其中 $c_n$ 是法向速度，$c_0$ 是平面波速度，$\kappa$ 是曲率，$D_{\rm eff}>0$ 是有效扩散系数。

![程函关系：曲率如何修正波前法向速度](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_20.jpg)

### 13.1 为什么行波通常稳定

若波前出现局部凸起，曲率较大，程函关系使它传播变慢；凹陷处相对更快。于是凸起被拖住，凹陷追上，波前趋于平坦。这就是平面行波对横向扰动通常稳定的几何原因。

如果某些系统中有效曲率系数符号反过来，凸起更快、凹陷更慢，扰动会放大，出现横向不稳定和迷宫状前沿。

### 13.2 螺旋波如何诞生

在可激发介质中，完整波前会向前传播。如果波前被切断，断端成为自由端。波前中段仍向前走，自由端因为没有完整邻近约束而绕转，最终形成螺旋。

![螺旋波诞生：断裂波前产生自由端](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_21.jpg)

成熟螺旋波的中心是相位奇点：绕核心走一圈，相位累计变化 $2\pi$，但核心点本身无法定义普通相位。

![成熟螺旋波：相位奇点与旋转波臂](https://raw.githubusercontent.com/qingshungLI/Markdown4Zhihu/master/Data/nonlinear_zhihu_images/fig_22.jpg)

相位可写成

$$
\Phi=m\theta+\Omega t+\psi(r).
$$

等相位线 $\Phi=\text{constant}$ 就是螺旋臂。远离核心时，螺旋局部像平面波；近核心处曲率很大，必须由程函关系约束。

### 13.3 哪些介质容易产生螺旋波

可激发介质最典型：阈值、恢复期和断裂波前共同提供旋转自由端。

振荡介质也能产生螺旋波：局部系统 Hopf 后有极限环，每个空间点都有相位；相位奇点会组织出螺旋波。近 Hopf 时，慢振幅常由复 Ginzburg-Landau 方程描述：

$$
\frac{\partial A}{\partial t}
=\mu A+(1+i\alpha)\nabla^2A-(1+i\beta)|A|^2A.
$$

平面波解可写成

$$
A=R e^{i(\mathbf q\cdot\mathbf r-\Omega t)}.
$$

不同波数的稳定性会出现 Eckhaus、Benjamin-Feir、对流不稳定、绝对不稳定等现象；在图像上表现为稳定螺旋、漂移螺旋、螺旋破碎与湍动。

## 14. 双稳前沿、Ising-Bloch 与 Faraday 斑图

双稳系统有两个稳定均匀态，前沿连接二者：

$$
\text{state 1}
\longleftrightarrow
\text{state 2}.
$$

前沿速度由两侧状态的势差或面积差决定。二维中曲率仍会修正速度。对称前沿常称 Ising front；运动前沿常称 Bloch front；两者之间的转变叫 Ising-Bloch transition。在非对称情形下，这种转变可以呈现鞍结样结构。

### 14.1 Faraday 斑图是什么

Faraday 斑图来自周期外驱动：竖直方向周期性振动液体，当驱动超过阈值，液面出现驻波斑图，例如条纹、方格、六角形。

它和 Turing、Hopf 的区别是：

$$
\text{Hopf: 自治系统的时间振荡}
$$

$$
\text{Turing: 自治反应扩散系统的静止空间斑图}
$$

$$
\text{Faraday: 周期外驱动系统中的驻波斑图}
$$

### 14.2 为什么是鞍结样失稳

对平液面态做线性稳定性分析，扰动写成

$$
\delta A\sim e^{\lambda t+i\mathbf k\cdot\mathbf r}.
$$

黏性耗散会压低振荡型复根的实部，因此失稳通常不是一对复特征值穿过虚轴的普通 Hopf。临界时更像某个实特征值过零，新的驻波解出现，因此常称为鞍结样分岔。

Faraday 和 Turing 相似之处在于：两者都会选择一个临界波数 $k_c$，最终形成空间图案。不同之处在于：Turing 是扩散诱导的自治失稳，Faraday 是周期外驱动下的参数激发。

## 15. 从模型到判断：把全书连成一套工作流

面对一个新的非线性模型，可以按下面的顺序读：

1. **没有空间、没有延迟**：先找不动点，算 Jacobian。
2. **一维系统**：看 $f=0$ 的根如何随参数改变，判断鞍结、跨临界、叉形。
3. **二维局部问题**：用 $\tau,\Delta$ 分类；$\tau=0,\Delta>0$ 是 Hopf 的入口。
4. **二维全局问题**：用 Poincare-Bendixson、Dulac、势函数、指数判断闭轨。
5. **已有周期运动**：用 Poincare 映射和 Floquet 乘子判断倍周期、环面分岔或极限环鞍结。
6. **周期变得很长**：问轨道撞上的是鞍点还是鞍结慢区。同宿给对数发散，SNIC 给 $1/\sqrt{}$ 发散。
7. **高维系统**：用中心流形降到临界方向；三维以上可能有混沌。
8. **延迟系统**：代入 $e^{\lambda t}$，得到含 $e^{-\lambda\tau}$ 的特征方程。
9. **反应扩散系统**：找均匀态，算 $J-k^2D$，比较 Hopf、Turing、wave instability。
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
| SNIC | 环上发生鞍结，周期按 $1/\sqrt{}$ 发散 |
| 倍周期 | Floquet 乘子穿过 $-1$，绕两圈闭合 |
| 中心流形 | 临界慢方向构成的低维不变曲面 |
| 奇异吸引子 | 吸引但混沌、常带分形结构的集合 |
| Turing | 均匀态稳定，但某个 $k\ne0$ 模式被扩散放大 |
| 程函关系 | 曲率修正波前法向速度 |
| 螺旋波 | 波前自由端或相位奇点组织出的旋转波 |

### 15.2 最后一页：不要背孤立公式

非线性物理最有用的不是某个孤立公式，而是公式背后的入口问题：

$$
f=0 \Rightarrow \text{不动点},
\qquad
f_x=0 \Rightarrow \text{根结构可能改变},
$$

$$
\tau=0,\Delta>0 \Rightarrow \text{Hopf 入口},
\qquad
J-k^2D \Rightarrow \text{空间模式稳定性},
$$

$$
e^{\lambda t} \Rightarrow \text{线性增长率},
\qquad
e^{-\lambda\tau} \Rightarrow \text{延迟系统},
$$

$$
c_n=c_0-D_{\rm eff}\kappa \Rightarrow \text{曲率调速},
\qquad
\Phi=m\theta+\Omega t+\psi(r) \Rightarrow \text{螺旋相位}.
$$

把这些入口串起来，就能从零开始读懂非线性物理：先看相空间，再看分岔；先看局部稳定性，再看全局结构；先看均匀态，再看空间模式；先看平面波，再看弯曲波前和螺旋波。
