椭圆曲线密码学论文实验复现

论文名称《Paring-free certificateless security authentication scheme for WSN based on ECC》。

由于能力有限，只复现ECC的加密原理部分。

ECC 1.0 版本

根据搜集代码，基本实现ECC加密过程，但是仅限于数字加密，暂时不能为字符串、文字或者哈希值。

ECC加密加密解密基本步骤：

1、B选择一个椭圆曲线Ep(a,b)，并且在Fp域上找出椭圆曲线上的一点G作为基点，计算椭圆曲线上的阶n，选择一个d(<n)作为自己的私钥，然后计算Q=dG；

2、B将Ep(a,b),n,Q最为公钥传给A

3、A收到B的公钥加密明文m，A随机选择一个数k(<n)，计算

    (x1,y1) = kG
    (x2,y2) = kQ
    c = m * x2

4、A将密文{(x1,y1),c}传给B

5、B解密，(x2,y2) = d(x1.y1)，解出明文 m = c * ((x2)^-1)


____

ECC 2.0 版本

支持对字符串类型数据加密；