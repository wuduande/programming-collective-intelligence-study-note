# 本节内容有三：
1. 分级聚类算法
2. K-mean聚类算法
3. 高维聚类投影到二维，以可视化

# 概述
聚类算法的目标是将n维空间中的向量，根据相似度度量将相似的向量聚合为一类。
因此，要使用聚类算法聚类实体，首先需要将实体的特征提取为向量，其次是定义
向量之间的相似度函数。

# 分级聚类
伪代码如下：

 for point in point set:
    make all point be one cluster of single element.
    the position of this cluster is the same to it\'s only element.

 for all cluster:
    find a pair of cluster of min distance.
    merge the pair of cluster into one.
    the position of this new cluster is the mean position of it\'s all elements.
    
# K均值聚类
伪代码如下：

 init k random seed points among point set.
 delta = positive infinite
 
 while delta > eps
    merge every point in point set and it's closest seed point into one cluster.
    move every seed point to the mean position of it\'s cluster.
    delta = sum of distances that all seed points moved.
 end
 return all the clusters.
 
# 以二维形式展现高维聚类结果（多维缩放）
伪代码如下：
 Dis_n(i,j)=distance between point i and point j in original space.
 place all points on two dimensional space.
 Dis_2(i,j)=distance between point i and point j in 2-d space
 
 while delta > eps
    for all points:
        move point i: pos(i) = sum_j (norm(pos(j) - pos(i)) - Dis_n(i,j)) * (pos(j) - pos(i))
    end
    delta = sum of all movement
 end
    
 