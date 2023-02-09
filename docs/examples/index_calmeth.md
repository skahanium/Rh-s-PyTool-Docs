## index_calmeth.non_dimension

index_calmeth.non_dimension是一个对数据进行预处理的模块，主要用于进行正向化和无量纲化。

导入必要的模块与函数，（随意）创建一个待转换数据组。假设每一列代表一个指标的观测值，而现在需要对第2、4个数据进行正向化，或者对所有数据进行无量纲化：

```python
>>>from index_calmeth.non_dimension import tiny_convert, middle_convert, moderate_convert, toone
>>>import numpy as np

>>>test_array = np.array([[25.3, 79.2, 21, 41.04, 177.395], 
                          [65.65, 57.24, 23.5, 45.5, 45.5], 
                          [0.175, 51.24, 711, 6.28, 65.23], 
                          [0.175, 51.24, 711, 6.28, 65.23], 
                          [186.4, 357.3, 227, 1.54, 5]])
```

### tiny_convert

假设第2、4个指标为负向指标，现将其转化为正向指标，接口说明参照[api](../api/index_calmeth.md#tiny_convert)。

```python
>>>print(tiny_convert(test_array, mode='0', change_list=[1, 3]))

[[2.53000000e+01 1.26262626e-02 2.10000000e+01 2.43664717e-02 1.77395000e+02]
 [6.56500000e+01 1.74703005e-02 2.35000000e+01 2.19780220e-02 4.55000000e+01]
 [1.75000000e-01 1.95160031e-02 7.11000000e+02 1.59235669e-01 6.52300000e+01]
 [1.75000000e-01 1.95160031e-02 7.11000000e+02 1.59235669e-01 6.52300000e+01]
 [1.86400000e+02 2.79876854e-03 2.27000000e+02 6.49350649e-01 5.00000000e+00]]
```

---
### middle_convert

假设第2、4个指标为中间型指标，现将其转化为正向指标，接口说明参照[api](../api/index_calmeth.md#middle_convert)。

```python
>>>print(middle_convert(test_array, change_list=[1, 3], best_value=[88, 20]))

[[2.53000000e+01 9.67322688e-01 2.10000000e+01 1.74901961e-01 1.77395000e+02]
 [6.56500000e+01 8.85777943e-01 2.35000000e+01 0.00000000e+00 4.55000000e+01]
 [1.75000000e-01 8.63497958e-01 7.11000000e+02 4.61960784e-01 6.52300000e+01]
 [1.75000000e-01 8.63497958e-01 7.11000000e+02 4.61960784e-01 6.52300000e+01]
 [1.86400000e+02 0.00000000e+00 2.27000000e+02 2.76078431e-01 5.00000000e+00]]
```

---
### moderate_convert

假设第2、4个指标为适度型指标，现将其转化为正向指标，接口说明参照[api](../api/index_calmeth.md#moderate_convert)。

```python
>>>print(moderate_convert(test_array, change_list=[1, 3], low_limit=[60, 12.5], high_limit=[71.2, 19.63]))

[[2.53000000e+01 9.72037749e-01 2.10000000e+01 1.72400464e-01 1.77395000e+02]
 [6.56500000e+01 9.90353023e-01 2.35000000e+01 0.00000000e+00 4.55000000e+01]
 [1.75000000e-01 9.69381335e-01 7.11000000e+02 7.59567066e-01 6.52300000e+01]
 [1.75000000e-01 9.69381335e-01 7.11000000e+02 7.59567066e-01 6.52300000e+01]
 [1.86400000e+02 0.00000000e+00 2.27000000e+02 5.76343255e-01 5.00000000e+00]]
```

---
### toone

对所有数据进行无量纲化（模式”1“代表均值归一化），接口说明参照[api](../api/index_calmeth.md#toone)。

```python
>>>print(toone(test_array, mode='1'))

[[-0.16238421 -0.13083709 -0.46043478  0.47570519  0.61326605]
 [ 0.05428917 -0.20258773 -0.45681159  0.57716106 -0.15180835]
 [-0.29730165 -0.22219173  0.53956522 -0.31501365 -0.03736187]
 [-0.29730165 -0.22219173  0.53956522 -0.31501365 -0.03736187]
 [ 0.70269835  0.77780827 -0.16188406 -0.42283894 -0.38673395]]
```

---

---
## index_calmeth.weights

index_calmeth.weights是一个客观赋权的模块，可以用于计算不同指标的权重。

导入必要的模块与函数，（随意）创建一个待转换数据组。以该数据组的每一列作为一个评价指标，计算每个指标的权重：

```python
>>>from index_calmeth.weights import critic, ewm, stddev, expert
>>>import numpy as np

>>>test_array = np.array([[25.3, 79.2, 21, 41.04, 177.395], 
                          [65.65, 57.24, 23.5, 45.5, 45.5], 
                          [0.175, 51.24, 711, 6.28, 65.23], 
                          [0.175, 51.24, 711, 6.28, 65.23], 
                          [186.4, 357.3, 227, 1.54, 5]])
```

### critic

利用critic赋权法计算指标权重，接口说明参照[api](../api/index_calmeth.md#critic)。

```python
>>>print(critic(test_array))

[0.16765873, 0.17370798, 0.27164073, 0.22001484, 0.16697772]
```

---
### ewm

利用熵权法计算指标权重，接口说明参照[api](../api/index_calmeth.md#ewm)。

```python
>>>print(ewm(test_array))

[0.19189057 0.1316655  0.21496771 0.21786722 0.243609]
```

---
### stddev

利用标准离差法计算指标权重，接口说明参照[api](../api/index_calmeth.md#stddev)。

```python
>>>print(stddev(test_array))

[0.18866013 0.19684011 0.22877436 0.21825414 0.16747126]
```

---

### gini

利用基尼系数法计算指标权重，接口说明参照[api](../api/index_calmeth.md#gini)。

```python
>>>print(gini(test_array))

[0.12055066, 0.17619928, 0.56913512, 0.03377098, 0.10034396]
```

---

---
## index_calmeth.evaluation

index_calmeth.evaluation是一个综合评价的模块，可以利用其为多指标数据进行总体评分。

导入必要的模块与函数，（随意）创建一个待转换数据组。以该数据组的每一列作为一个评价指标，且假设都已经过正向化：

```python
>>>from index_calmeth.evaluation import rsr, ni_rsr, topsis
>>>from index_calmeth.weights import critic
>>>import numpy as np

>>>test_array = np.random.rand(7, 6)
```

### rsr

利用整次秩和比方法打分，接口说明参照[api](../api/index_calmeth.md#rsr)。

```python
>>>print(rsr(test_array, critic(test_array)))

[[0.47298203],
 [0.59557394],
 [0.20102693],
 [0.5231342 ],
 [0.55658626],
 [0.39855278],
 [0.25214386]]
```

---
### ni_rsr

利用非整次秩和比方法打分，接口说明参照[api](../api/index_calmeth.md#ni_rsr)。

```python
>>>print(ni_rsr(test_array, critic(test_array)))

[[0.76082196],
 [0.7836682 ],
 [0.36186168],
 [0.64729533],
 [0.68807074],
 [0.6014031 ],
 [0.48593302]]
```

---
### topsis

利用优劣解距离方法打分，接口说明参照[api](../api/index_calmeth.md#topsis)。

```python
>>>print(topsis(test_array, critic(test_array)))

[[0.74850458],
 [0.41476565],
 [0.07367268],
 [0.54296688],
 [0.48512108],
 [0.45568626],
 [0.39804066]]
```