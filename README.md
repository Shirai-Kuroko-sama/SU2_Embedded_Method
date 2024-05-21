# SU2_Embedded_Method
An Embedded FIML method based on SU2(an open source CFD application)
## SU2嵌入式FIML方法
一种基于开源CFD软件SU2的流场反演与机器学习方法(Field inversion and machine learning,FIML)
## Abstract(摘要)
In this project, we propose a new FIML method based on the open source CFD application called SU2. (originaly founded by Juan J. Alonso,etc, Stanford University，and constructed by global teams or individuals. Original details may visit the link below:)

    https://github.com/su2code

And professor J.Holland developed the SU2's FIML branch, initialized the frame of field inversion and machine learning method based on SU2, which is the main constuction and inspiration of this project. Original codes of FIML method in SU2 may visit the link below:

    https://github.com/jholland1/SU2

It's an all-known fact that nowadays RANS method have encountered many tackles, such like low accuracy, low confidence results,etc. But it is still a popular method used by many researchers with the benifit of lower demands of computer compared with DNS and LES. But with the Machine learning(ML) and AI technologies advancing, computers can easily abosorb quite quantities of data, train and predict the result precisely just like human beings neural network(as long as the model modified and trained well). As a result, with lots of high-confidence data and experiment results contained, RNAS problems can possibly be better solved in assist of machine learning.

Back to SU2, sipecificaly, Prof.J.Holland pointed that it's possible to combine adjoint method(used in field inversion) with backpropagation method(used in machine learning when constructing a neural network) together in order to further improve the turbulence models' predict precision, which is the same opinion concluded and held by us(breifly, these two methods share the same mechanism mathematically). Hence, many researchers have been diving into looking for high efficiency, high accuracy and low cost FIML method.

Prof.J.Holland has developed Classic and Direct FIML methods based on SU2, and Embedded method is(or was?) on the way(updated 5 years ago...). whether it's developed or not, we inspired by his thought and developed a Embedded method of our own(if any similarities exist, many thanks to Prof.J.Holland's inspiration :) and we think the same). But there's one thing must be diffirent, that is we consider a new scalar as a input to neural network training, which is put forward recently, called Liutex scalar.

Why we select this variable? Because we find that current turbulence models (like S-A model, which is the origin model J.Holland aimed to fix, he called "SA_FIML".) have bad prediction where large separation flow exists.These regions tend to have a large number of vortex-like structures, and liutex method can precisely tell the rigid rotation part of vortex away from other parts, and the rigid rotation part which represents the essence of vortex is called Liutex tensor. But in order to get this tensor, two steps of coordinate rotation are inevitable, considering Galilean invariance, we select the liutex scalar which values its quantity, things like velocity directed, but speed doesn't.

Having said all that, this project propose a new FIML method, chose S-A one-equation turbulence model,use design variables as a correction to the containing production term, combine field inversion and machine learning together with selected variables as connections between, and the predicted beta(design variables) is used in the next interation of field inversion. So it is expected to have lower cost compared with Direct(which aims to find links directly between beta and neural network's weight, may lead to higher cost of computation) and higher accuracy compared with Classic(which has lowest accuracy among). And with Liutex scalar considerd, it is also expected to have better performance in large separation flow area.

At the same time, we seek to try best to introduce this project in double language, both in English and Chinese, aiming to bring SU2 for domestic reseachers with easier reading and comprehensing experience, inspiring fellows to be more creative with such open source CFD application.

Obviously, many further works need to bo done, and many problems may spring out due to poor personal capacity and limited research time. So we are open to any advice and critical comments, if time permit, further updates will be on the way!

Finally, many thanks to all SU2 developers and Prof.J.Holland, and so to my respected teacher Gao! It's my pleasure to have such a chance cooperating and working with your excellent researchers!

Sincere regards!

——Yuhang Li

在本项目中，我们在开源CFD软件SU2的基础上提出了一个新的FIML方法(SU2由斯坦福大学Alonso等团队创始，并由世界各地团队或个体共同开发。SU2相关的源代码请访问以下链接：)

        https://github.com/su2code

J.Holland教授研发了SU2的FIML方法分支，搭建了基于SU2的流场反演与机器学习方法的基本框架，这同时也是本项目的基本架构与灵感来源。基于SU2的FIML方法源代码请访问以下链接：

    https://github.com/jholland1/SU2

众所周知，如今RANS方法遇到了许多问题，例如准确性低，输出结果置信度低等。但它仍然是许多研究人员使用的一种流行方法，与DNS和LES相比，它的优势在于对计算机的要求较低。但随着机器学习（ML）和人工智能技术的进步，计算机可以很容易地吸收大量数据，像人类神经网络一样精确地训练和预测结果（只要模型修改和训练得好）。因此，由于包含大量高置信度数据和实验结果，湍流模拟中的RNAS问题可以在机器学习的帮助下得到更好的解决。

回到SU2中，J.Holland教授指出，为了进一步提高湍流模型的预测精度，可以将伴随方法（用于流场反演）与反向传播方法（用于构建神经网络时用于机器学习）结合起来，这个观点与我们得出的结论和持有的观点相同（简而言之，这两种方法在数学上具有相同的机制）。因此，许多研究人员也一直在寻找高效、高精度和低成本的 FIML 方法。

J.Holland教授已经开发了基于SU2的经典型和直接型两种FIML方法，而嵌入式方法正在（或曾经？）正在开发中（最近一次是在5年前更新...）无论开发与否，我们都受到他的思想的启发，并开发了我们自己的嵌入式方法（如果存在任何相似之处，非常感谢 J.Holland 教授的灵感:)我们想到一块去了）。但有一点一定是不相同的，那就是我们考虑将一个新的标量作为神经网络训练的输入，这是近些年来所提出的新的涡识别方法，称为 Liutex 标量。

为什么我们选择这个变量？因为我们发现，当前的湍流模型（如S-A模型，这是J.Holland旨在修复的原始模型，他称之为“SA_FIML”）在存在大分离流动现象的区域具有比较糟糕的预测能力。这些区域往往具有大量的涡旋状结构，liutex方法可以精确地将涡旋的刚性旋转部分与其他部分区分开来，而代表涡旋本质的刚性旋转部分称为Liutex张量。但是为了得到这个张量，坐标旋转的两步是不可避免的，考虑到伽利略不变性，我们选择了衡量其大小的 liutex 标量，就像速度矢量有方向，但速度大小没有。

综上所述，本项目提出了一种新的FIML方法，选择了S-A单方程湍流模型，使用设计变量作为对S-A模型所含生成项（production）的修正，将流场反演和机器学习结合在一起，并将选定的变量作为连接，并将预测的beta（设计变量）用于下一轮流场反演的迭代。因此，与Direct（旨在找到beta和神经网络权重之间的直接联系，可能导致更高的计算成本）相比，它的成本更低，与Classic（其中精度最低）相比，它的精度更高。又因为考虑到Liutex标量，预计这种方法在大分离流区域也具有更好的性能。

与此同时，我们将竭尽全力以中英文双语的形式介绍本项目，力求给读者们更简单轻松的阅读体验，从而将SU2介绍给国内的同行们，为大家介绍一个能充分发挥各位创造性的CFD开源软件。

显然，还有很多工作要做，由于个人能力不足和研究时间有限，可能会出现许多问题。因此，我们愿意接受任何建议和批评意见，如果时间允许，我们将进行进一步的更新！

最后，非常感谢所有SU2开发人员和J.Holland教授，也感谢我尊敬的高老师！我很高兴有这样的机会与你们优秀的研究人员合作和工作！

诚挚的问候！

——Yuhang Li
##

