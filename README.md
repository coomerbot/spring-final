# 計算機概論 期末專題：Wasserstein GAN 理論與實作
在 Google Colab 環境中直接貼上程式碼即可運行模型，建議使用 Colab 內建的 GPU 運行。預設訓練集是整個 MNIST dataset，因此模型會隨機生成數字 0~9 的圖像。  
  
## 備注
將程式碼中的這一行：
```py
train_images = [img.numpy().reshape(-1) for img, _ in train_data]
```
修改成：
```py
train_images = [img.numpy().reshape(-1) for img, label in train_data if label == 8]
```
能讓模型只學習生成數據集中的特定數字。  
  
將程式碼中的這一行：
```py
train_data = datasets.MNIST(root='./data', train=True, download=True,
                                    transform=transforms.ToTensor())
```
修改成：
```py
train_data = datasets.FashionMNIST(root='./data', train=True, download=True,
                                    transform=transforms.ToTensor())
```
能更換訓練集至 Fashion MNIST dataset（服裝圖像）。  
  
修改成：
```py
train_data = datasets.KMNIST(root='./data', train=True, download=True,
                                    transform=transforms.ToTensor())
```
能更換訓練集至 KMNIST dataset（日文草寫圖像）。

