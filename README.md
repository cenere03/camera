# camera

```
1  import cv2
2  import matplotlib.pyplot as plt
3 
4  # 初期化
5  i = 0
6  x = []
7  yb = []
8  yg = []
9  yr = []
10 plt.ion()
11
12 # MATPLOTLIB コンフィグ
13 plt.title('Luminance') ## グラフタイトル
14 plt.xlabel('x') ## x軸ラベル
15 plt.ylabel('y') ## y軸ラベル
16 plt.xlim(0,100) ## x軸範囲固定
17 plt.grid() ## グリッド線オン
18
19 # カメラのキャプチャを開始 --- (*1)
20 cam = cv2.VideoCapture(0)
21 while True:
22     # 画像を取得 --- (*2)
23     _, img = cam.read()
24     # ウィンドウに画像を表示 --- (*3)
25     cv2.imshow('PUSH ENTER KEY', img)
26 
27     b, g, r = cv2.split(img)  # 画像をチャンネルごとに分離する。
28     
29     i = i + 1
30    
31     ## 描画データ生成
32     x.append(i) ## x軸
33     yb.append(b.mean()) ##　y軸
34     yg.append(g.mean()) ##　y軸
35     yr.append(r.mean()) ##　y軸
36
37     plt.plot(x,yb,color='blue')
38     plt.plot(x,yg,color='green')
39     plt.plot(x,yr,color='red')
40
41     ## グラフ描画
42     plt.draw()
43    
44     ## 更新待機（秒）
45     plt.pause(0.1)
46     # Enterキーが押されたら終了する
47     if cv2.waitKey(1) == 13:
48         plt.close() ## グラフを閉じる
49         break
50
51 # 後始末
52 cam.release()
53 cv2.destroyAllWindows()
```

カメラ画像を取得し，毎フレームごとの輝度値を取得するコード．

# 依存ライブラリ，バージョン　
python3.7　openCV

# 実行の仕方
test.ipynbを実行すると，
カメラ画像と毎フレームごとの輝度値を表すグラフが表示されます．
Enterキーを押すとプログラムは終了します．

# 使用例

# 参考 引用

コード 19～25,51～53を次のサイトより引用
https://news.mynavi.jp/article/zeropython-35/

コード 4～17,29～46を次のサイトより一部引用，参考にした．
https://note.mu/pomta_trd/n/n15b1d992f5ca

