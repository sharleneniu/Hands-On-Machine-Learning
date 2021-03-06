# Chapter 1: 机器学习概览

## 机器学习分类

机器学习可以根据不同的标准分为不同的种类，在这里介绍下书中所提及到的集中分类

1. 根据训练中是否接受监督以及接受监督的数量和类型进行分类：

- **监督式学习**\
监督式学习其实就是指用于机器学习的数据集(dataset)有进行人为的“识别分类”，即添加标签(label)。比如，一个很常见的例子，现在有100W张照片作为训练数据，如果我们有对这些照片进行标记（label），标记好每张照片是关于什么的，并将这些label也一并作为训练数据提供给算法。那么这种机器学习方式称为监督式学习。

- **无监督式学习**\
无监督式学习就是指dataset中没有添加标签，系统在不知道所有数据的分类，特征等情况下通过分析dataset进行自我学习。常见的无监督是学习算法包括，聚类算法（Cluster like K-Means),可视化和降维(PCA),关联规则学习(Apriori)

- **半监督式学习**\
半监督学习指所有dataset中有少量的标记数据和大量的未标记数据，半监督式学习算法可以根据已经标记的数据，对未标记的数据添加label

- **强化学习（Reinforcement learning, RL）**\
  强化学习算法会根据环境作出选择，执行操作，得到reward，并根据reward不断update算法来获得最好的policy，从而获得最大的reward。example：AlphaGo

2.根据是否可以动态的进行增量学习进行分类：

- **批量学习**\
批量学习指系统必须使用所有可用的数据进行训练，而不能进行增量学习。由于批量学习必须使用所有可用数据进行训练，往往需要大量的时间和计算资源，所以一般情况下都是**离线学习**。在离线学习过程中训练系统，结束后停止学习并且投入生产环境。\
如果需要学习新的dataset，则需要在旧dataset和新datset的基础上训练新的版本，训练结束后重新投入生产环境。\
缺点：
  - 每次需要训练新dataset时，都需要更新dataset，并且重新训练新版本
  - 由于每次训练都要使用完整数据集，所以需要耗费大量的计算资源以及时间
  - 已经训练过的旧数据需要在训练新数据时，会重复训练
- **增量学习**\
在线学习指系统可以根据线上新数据集实时快速的进行模型训练，在线学习一般都是**增量学习**，而增量学习不一定是在线学习。

3.根据算法的泛化能力进行分类：

- **基于实例的学习**\
系统完全记住学习实例(example)，通过相似度计算，泛化到新的实例

- **基于模型的学习**\
系统根据已有的实例构建模型，然后使用模型进行预测

## 机器学习的主要挑战

1. 训练数据不足:\
   训练数据数量不够大时，模型的精准度较低\
   ***how to solve*** 增加训练数据量
2. 训练数据不具有代表性:\
   当选取的训练数据不能代表整体数据集时，模型不能作出足够准确的预估（泛化能力弱）\
   ***how to solve*** 训练数据不具有代表可能是由于采样方式过于特殊，选取了过于特殊的训练数据，可尝试使用其他采样方式，以获取更加具有代表性的训练数据
3. 训练数据质量差:\
   当训练数据中包含过多噪声，错误和异常值时，模型也不能作出准确的预估\
   ***how to solve*** 清理训练数据，可以直接丢弃异常数据
4. 训练数据包含过多无关特征\
   训练数据本身未包含很多有用的特征或者是在特征工程中，未获取到有用的特征\
   ***how to solve*** 方法之一，可以通过使用PCA等降维算法，对于原油特征进行提取，产生更有用的特征，或者通过收集新数据，选取新的特征
   > 在从得到原始数据到模型训练的过程中，必不可少的一步就是特征提取，书中对这里介绍很简略，然而实际上，这里非常值得仔细学习，[参考](https://www.zhihu.com/question/29316149)以及[后续学习笔记](TBA)
5. 训练数据过度拟合(**overfitting**)
   过度拟合表示模型在训练数据上表现非常好，但泛化能力非常差\
   ***how to solve*** 可通过正则化(**[regularization](https://zh.wikipedia.org/wiki/%E6%AD%A3%E5%88%99%E5%8C%96_(%E6%95%B0%E5%AD%A6))**)进行限制模型的自由度(**[degree of freedom](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E5%BA%A6_(%E7%BB%9F%E8%AE%A1%E5%AD%A6))**)来降低模型过拟合的风险
   >正则化：应用正则化的程度可以通过超参数(**hyperparameter**)进行控制。超参数不受算法本身影响，须在训练之前设置好，并且在训练过程中保持不变。
6. 训练数据拟合不足\
   训练数据拟合不足与过拟合正好相反，一般是由于模型过于简单或者正则化超参数过大导致
  
## 测试与验证

一般将数据分为训练集，测试集，也可分为训练数集，测试集和验证集。具体的验证方式学习见[常见验证方式学习](TBD)