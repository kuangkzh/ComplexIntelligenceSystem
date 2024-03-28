# 构建智能——对齐：提供优化方向


前文提到，智能系统不符合预期的根本原因在于工具目标和实际目标间存在gap，因而导致目标传导失真。
每当我们在选定一个对象作为工具时，实际也就确定了工具的目标状态分布，这是每件事物的基本属性。
对于工具而言它只会遵守自身发展规律，朝着设定好的目标不断前进，而永远也无法完全得知使用者的实际目标，因此工具和使用者总存在着gap。
有什么样通用的构造技巧可以用于对齐二者的目标，是本节将要探讨的问题。


## 采样

自由演化一定是对齐目标和实际目标的最佳方案，因为演化从整个空间中随机采样，
只要采样方案足够随机，目标就不会偏向状态空间中的某个局部，因此演化算法通常具有很强的鲁棒性。
这也是为什么自由经济中诞生的经济实体会比计划经济的更具竞争力，因为前者围绕着生存这一最终目的运转，
后者围绕计划的目标运转，而计划和最终目标间还存在着gap，至少在过去的50年里，计划带来的高效率还不能弥补目标差异引入的泛化性风险。

但通常演化方法不适用于大多数系统，全局采样的前提是我们能负担这样高成本系统的运转，
在自由经济中采样也并不是完全随机的，个体更类似于在随机的初始化点中通过退火达到稳定。
深度学习里我们在假设空间中进行采样，通常是在一个高斯分布的空间中随机采样，再将采样点编码成文本或图像的数据，
或者在某个已知样本周围，通过一些先验性质进行数据增广。
但如果采样方法是有偏的，通过采样学习到的智能会有更大的偏差风险。


## 池化

池化是一种对数据进行降采样的特征提取方法，通过计算区间某种统计值作为区间特征代替原有数据。
池化除了降低模型计算负担和参数量以外，还可避免模型过拟合。
池化之所以有效，是因为真实数据普遍具有一种性质：
在大尺度上数据的整体的低频的统计特征通常没有什么差异性，具有的信息量很少；
在小尺度上数据的高频特征，通常受各种噪声波动影响，具有的信息较为嘈杂。
因此在一个中等尺度上对细节进行一定的统计聚合，既可以获取真正有用的信息，又不容易受噪声影响，同时还能减少所需的运算量。

人体中存在各种各样的池化机制，听觉上高响度的声音会遮蔽低响度的，
视觉上人眼看到的颜色实际是不同波长光线在三色细胞上激发总值的组合。
在人类社会中，最典型的池化例子是投票制度。
在考虑所有人的需求时，显然一个一个地调查每个人的想法是不可能的事情，人群的声音总是非常嘈杂的，
因而我们会进行投票，将群体中最突出的特征筛选出来。
更复杂的投票系统是多级的，每一级选出他们中最突出的想法作为代表，参与下一级的投票。
如果只进行一次大型全民投票，那在人非常多的时候，那些细小且有价值的声音就很容易被掩盖。


## 扁平化

残差连接作为一种基础模块，已经成为现代深度学习不可动摇的根基。
扁平化管理也成为现代大型企业追求的管理模式，通过减少管理层次并且增加越级管理增加管理效率。
这意味着在一个大型智能系统的内部，系统自身的目标失真也会成为影响系统性能的主要因素。
在一个多层级的智能系统中，顶层的系统实际上在以底层系统为工具发挥作用，那么工具和顶层的实际目标就存在着新的gap，
层级越多这样的目标偏差越大。
即使是在神经网络这样的目标传导能力极强的强耦合系统中，一层层的目标偏差累积也会使得深度网络无法训练。
因此在多层级系统中一定需要某种连接上下层的机制，使得目标至少在系统内部是对齐的。


## 对比学习

在现实世界中，我们通常不感兴趣，也很难了解一件事物的所有细节，而更关心的是它表现出的某些属性和其他事物的关联。
更重要的是同一类事物往往具有很多相同的属性，大多数属性对我们的最终目的都是不重要的，而只有那些具有差异的部分才是至关重要的。
因此在同一类事物间挖掘关联进行对比往往有助于关注到真正的目标。

大多数的预训练任务都是在试图完全记住一个样本，这在模型初始化的早期通常是有用的，
因为预训练大量的数据有助于模型对同类数据的共性进行学习。
但是当模型需要对特定任务进行针对性训练时，如果还使用预训练任务，
就像让学生在学习做数学题时背答案一样，显然是非常低效的学习方式，要么学生只能学成看上去会做题的表象，要么就需要背上千题才会一种题型。
许多学生在数学上学习成果不佳的主要原因，就是一直试图在背正确答案，
并期望从答案中找到某些关键词和模板，套用到新的同类型的题目上，这与SFT过拟合的LLM一模一样。

健康的学习方式应当尽量剔除目标中无关的演化方向，例如在数学题的例子中，
如果学生不断对比正确解法和自己的错误解法的分歧点，就能慢慢掌握正确的做题思路。
题目中的其他内容，例如语法和语气词等，都是无关重要的东西，可以通过对比去除。


## 强化学习

强化学习是一种特殊的对比学习，它定义了某种奖励函数，并希望模型能够在这个最终的奖励上取得好的表现，这个奖励的大小就是强化学习关注的属性关系。
然而最终奖励是并不连续的，因此强化学习总需要采取某种方法，例如采样或者价值网络，将最终目标平滑对齐到模型每一步的目标上。
上文提到的学数学题就是这样一个过程，做题的最终奖励仅有对和错，
但是我们可以通过对比每一步的解题思路，慢慢找到正确的解题过程，这就是我们脑中的价值网络发挥作用的过程。

可以看出，强化学习的强大之处在于，当其他学习方法依赖于先验假设手工对齐目标的时候，强化学习旨在通过某种机制主动对齐目标。
这样的模型将自带一个价值层，该层与最终的奖励目标高度对齐，而价值层与动作层又是高度耦合的，因此可以将它的目标几乎无损的传下去。
也因此我们可以通过RLHF可以创建如此强大的人工智能，但OpenAI的对齐不止在RLHF，
从技术报告中可以看出ChatGPT的开发团队与标注团队保持对齐，标注团队的数据标注再与ChatGPT的目标对齐。
这中间的每一步本质上都是一种目标对齐的强化学习，使得模型对团队的最终目标保持了最高度的对齐。

但是对齐的本质在于提高耦合度和信息交互度，这是成本很高的一件事。
假设存在最终目标、价值层和动作层三层，前两层传递每单位信息的成本为a，后两层传递单位信息成本为b，
应当存在一种效益最高的对齐方式，我猜想前两层信息传递量应该为$\log_{ab}{b}$，后两层为$\log_{ab}{a}$ （该结论仅为猜想，没有任何推导过程，仅凭数学直觉提出）。

强化学习的风险依然在于目标失真。首先人为设定的奖励函数并不代表人的最终目标，而价值层与奖励函数和动作层都会存在gap。
在第一章的推论中，我们已经说明除了增加智能与工具的耦合度(信息交互、数据集)以外，目标的可见部分和不可见部分总是不可能同时得到优化的。



## 对抗学习

对抗学习是一种特殊的强化学习，它同样采用价值网络和动作网络的结构，只不过对抗学习的价值网络是在用逆否命题逼近的方法建立一个对齐目标的新目标，
然后再要求动作网络对齐到这个原本目标的逆否命题近似。
对抗学习之所以有效，是因为当目标是什么这个问题也足够复杂时，求解其逆否命题通常要比直接求解简单。
因为目标的逆否命题是一个判断目标是否达成的判别问题，命题本体常常是一个生成问题，他们之间就像P与NP的关系一样。

在图像生成中，GAN通过判断生成图像是不是与真实图像不可区分作为生成真实图像这一目标命题的近似，再令生成器生成足以混淆鉴别器的图片。
在现实社会中我们也会通过对抗构造系统，当我们想生产什么时，就会先构建相对应的质检制度。
像是食物、药品、手机、芯片，都有一套行业质检规则，对于生产产商而言，他们就在与这套规则进行对抗。
当我们在构建深度学习模型时，模型实际也在与我们的质检标准（验证集）对抗。

然而对抗学习的问题在于，逆否命题逼近之所以简单，是因为它的可行解空间大得多，
要完全覆盖解空间的求解难度和原始命题一样，因此鉴别器实际只实现了一个逆否命题的弱化解。
在这个不完全覆盖的解中，强大的生成器往往能找到shortcut逃逸出去，就像是逃避规则售卖伪劣产品的不良商家和产生幻觉的LLM一样。



## 多目标学习

传统观点认为，由于世界各部分普遍具有联系，因此为模型设立多个目标一起学习，有助于学习各种问题间的联系，使得对世界的认知可以在问题间共用。
利用本文理论解释，当智能体具有多个目标时，也就是当它与多个不同智能具有共生关系$P(s_{\phi,alive}^n | s_{\pi}^t s_{\phi}^t s_{\pi,alive}^n) \gt P(s_{\phi,alive}^n | s_{\pi}^t s_{\phi}^t)$时，
在各种目标的约束下，智能的目标不容易偏向于某一方而过拟合，它实现实际目标的概率就得到了提升，因此与它相关的各种任务也能够享受到这种提升。

当任务足够多时，智能体就能在多种目标的博弈中实现动态平衡，提升与世界的耦合度，同时实现偏差和方差的降低。
在第一章智能原理中，我们以人使用刀作为例子，讲述了智能与工具地位对等、互相利用的关系。
但敏锐的读者应该发现，人与刀在这个例子中的地位是极其不对等的，刀对人的筛选力度远小于人对刀的筛选力度，
这便是因为刀的目的来源于人的使用，而对人而言，使用刀只是他诸多目的之一。
我们还将在第三章中更深刻地讨论这种关系。

任何一种智能想要成为人们眼中“真正的智能”，都不得不经由多目标的约束，
否则就很容易被单个目标所劫持，在不知道哪里来的风险中走向衰亡。
一个社会必须由各种政府机构、公众团体相互制约，健康的市场必须由多方博弈稳定定价，否则就很容易走向某种权力的垄断，最终在单目标的引导下走向过拟合直至衰亡。



## 总结

本章内容主要是在第一章的基础上举例，目标是在为读者培养在新理论体系下的思考直觉。
经过这两章的分析举例，读者应该具有熟练分析一个智能系统的能力，
快速地指出一个系统的目标和预期目标，分析该系统在欠拟合和过拟合下的表现，
同时依据不可能三角理论，指出该系统不可两全的原因，并能够给出优化建议。