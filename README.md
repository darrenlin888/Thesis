# 2023_LinJunYing

||content|
|:--:|:--:|
|**論文題目**|新型微發光二極體顯示器子像素渲染算法之研究|
|**English Title**|Study of the Subpixel Rendering Algorithm for Advanced Micro LED Display|
|**研究生**|林峻潁|
|**畢業年分**|2023|

## Introduction

利用子像素渲染演算法使低解析度面板上的圖像儘可能趨近高解析度面板所能呈現的圖像，並建立人眼視面板的模型，再利用評估指標進行人眼特徵
比較找出最佳演算法。

- - -
## Code structure

```
# 3x3、5x5、7x7、9x9為使用不同Interpolation kernel size
📁root
  ├─ 📁SPR
  |    ├─SPR_3x3.py  # Compute SPR img
  |    ├─SPR_5x5.py
  |    ├─SPR_7x7.py
  |    └─SPR_9x9.py
  |
  ├─ 📁Adaptive_filter
  |    └─Adaptive_filter.py
  |
  └─ 📁Simulation   
       └─NYCU_sim.py      
  
  

```
## Main files:
```

  ├─ SPR_sim.py 
  ├─ SPR_adaptive.py                                       
  └─ SPR.py 
                                            
```

- - -
## Requirements  

* Setup environment.

```
virtualenv [name] --python=3.8
.\[name]\Scripts\activate.bat
```

* Setup packages via each subfolder

```
cd [subfoler_dir]
pip install -r requirements.txt
```

- - -

## 使用流程:

### 1.算出SPR img

流程如下:

1. img_og_path:選擇高解析度圖像
2. 選擇H的size
3. r、b channe interpolation kernel 參數，如: a、b、c、d、e
4. g channel interpolation kernel 參數，如: a1、b1、c1 
5. save_name:輸入保存的圖像名稱選擇高解析度圖像
6. DIR_OUT:保存img的路徑
7. DIR_OUT_mat_H:輸入保存mat_H的路徑

```
python SPR_5x5.py 
```

### 2.使用Adaptive filter 

1. image_path:選擇高解析度圖像
2. mat_H_np_1:選擇使用的H
3. mat_H_np_2:選擇使用的H
4. save_name:輸入保存的圖像名稱
5. DIR_OUT:保存img的路徑
6. DIR_OUT_mat_H:輸入保存mat_H的路徑
7. 判斷範圍(block大小，通常為H大小，但H只有中間部分有比較大的值，當H太大時，判斷區域太大會容易判斷錯誤)

```
python SPR_adaptive.py 
```

### 3.模擬人眼所見

1. mask_path:選擇panel排列方式
2. DIR_OUT:存檔的地方
3. save_name:檔名

```
python SPR_sim.py
```
