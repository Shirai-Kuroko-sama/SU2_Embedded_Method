# SU2_Embedded_Method
An Embedded FIML method based on SU2(an open source CFD application)
## SU2嵌入式FIML方法
一种基于开源CFD软件SU2的流场反演与机器学习方法(Field inversion and machine learning,FIML)
## Abstract(摘要)
In this project, we propose a new FIML method based on the open source CFD application called SU2. (originaly founded by Juan J. Alonso,etc, Stanford University，and constructed by global teams or individuals. Original details may visit the link below:)

在本项目中，我们在开源CFD软件SU2的基础上提出了一个新的FIML方法(SU2由斯坦福大学Alonso等团队创始，并由世界各地团队或个体共同开发。SU2相关的源代码请访问以下链接：)

    https://github.com/su2code

And professor J.Holland developed the SU2's FIML branch, initialized the frame of field inversion and machine learning method based on SU2, which is the main constuction and inspiration of this project. Original codes of FIML method in SU2 may visit the link below:

    https://github.com/jholland1/SU2

It's an all-known fact that nowadays RANS method have encountered many tackles, such like low accurancy, low confidence results,etc. But it is still a popular method used by many researchers with the benifit of lower demands of computer compared with DNS and LES. But with the Machine learning(ML) and AI technologies advancing, computers can easily abosorb quite quantities of data, train and predict the result precisely just like human beings neural network(as long as the model modified and trained well). As a result, with lots of high-confidence data and experiment results contained, RNAS problems can possibly be solved in assist of machine learning.

Back to SU2, sipecificaly, Prof.J.Holland pointed that it's possible to combine adjoint method(used in field inversion) with backpropagation method(used in machine learning when constructing a neural network) together in order to further improve the turbulence models' predict precision, which is the same opinion concluded and held by us(breifly, these two methods share the same mechanism mathematically). Hence, many researchers have been diving into looking for high efficiency, high accurancy and low cost FIML method.

Prof.J.Holland has developed Classic and Direct FIML methods based on SU2, and Embedded method is(or was?) on the way(updated 5 years ago...). whether it's developed or not, we inspired by his thought and developed a Embedded method of our own(if any similarities exist, many thanks to Prof.J.Holland's inspiration :) and we think the same). But there's one thing must be diffirent, that is we consider a new scalar as a input to neural network training, which is put forward recently, called Liutex scalar.

Why we select this variable? Because we find that current turbulence models (like S-A model, which is the origin model J.Holland aimed to fix, he called "SA_FIML".) have bad prediction where large separation flow exists.These regions tend to have a large number of vortex-like structures, and liutex method can precisely tell the rigid rotation part of vortex away from other parts, and the rigid rotation part which represents the essence of vortex is called Liutex tensor. But in order to get this tensor, two steps of coordinate rotation are inevitable, considering Galilean invariance, we select the liutex scalar which values its quantity, things like velocity directed, but speed doesn't.

Having said all that, this project propose a new FIML method, select S-A one-equation turbulence model,use design variables as a correction to the containing production term, 
##

