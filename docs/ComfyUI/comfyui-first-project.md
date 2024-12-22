# [Lemonhub ComfyUI](index-comfyUI.md) 看懂第一個專案開始

---

## 預讀資訊

以下指南將幫助你快速熟悉 **ComfyUI** 的核心功能與操作，適合初次接觸 ComfyUI 的使用者：

- **[ComfyUI 節點與功能概述](Guide/comfyui-guide-comfyui.md)**  
  詳細介紹各類節點的功能與用途，助你全面了解 ComfyUI 的運作原理。

- **[ComfyUI 節點基礎教學](Guide/comfyui-guide-node.md)**  
  通過基礎教學，了解如何創建與組合節點以構建圖像生成流程。

---

## 1. 使用節點 (Node) 詳細說明

以下是 **ComfyUI** 中常見節點的詳細說明，幫助你理解每個節點的功能與應用場景：

### **1. CLIPTextEncode 節點**
- **功能**：將文本轉換為條件向量，作為圖像生成的描述依據。
- **輸入**：
  - `CLIP`：CLIP 模型。
- **輸出**：
  - `CONDITIONING`：文本條件向量。

---

### **2. EmptyLatentImage 節點**
- **功能**：生成空的潛在圖像作為初始輸入。
- **輸入**：無。
- **輸出**：
  - `LATENT`：潛在圖像。

---

### **3. KSampler 節點**
- **功能**：執行擴散過程，基於條件生成潛在圖像。
- **輸入**：
  - `MODEL`：Stable Diffusion 模型。
  - `positive`：正面條件（文本描述）。
  - `negative`：負面條件（限制描述）。
  - `latent_image`：初始潛在圖像。
- **輸出**：
  - `LATENT`：生成的潛在圖像。

---

### **4. VAEDecode 節點**
- **功能**：將潛在圖像解碼為可視圖像。
- **輸入**：
  - `samples`：潛在圖像。
  - `vae`：VAE 模型。
- **輸出**：
  - `IMAGE`：最終圖像。

---

### **5. SaveImage 節點**
- **功能**：保存生成的圖像到指定位置。
- **輸入**：
  - `images`：生成的圖像。
- **輸出**：無。

---

### **6. CheckpointLoaderSimple 節點**
- **功能**：加載指定的模型檔案 (Checkpoints)。
- **輸出**：
  - `MODEL`：Stable Diffusion 模型。
  - `CLIP`：CLIP 模型。
  - `VAE`：VAE 模型。

---

## 2. 圖片生成流程

以下是使用 **ComfyUI** 進行圖像生成的基本流程：

### 流程步驟

1. **CheckpointLoaderSimple**
   - 加載模型 (Stable Diffusion、CLIP、VAE)。

2. **CLIPTextEncode**
   - 將文本編碼為條件化向量，分別生成正面與負面條件。

3. **EmptyLatentImage**
   - 創建空的潛在圖像，作為生成基礎。

4. **KSampler**
   - 基於條件向量與潛在圖像執行擴散過程，生成潛在圖像。

5. **VAEDecode**
   - 將潛在圖像解碼為可視的最終圖像。

6. **SaveImage**
   - 保存生成的圖像到指定路徑。

---

## 3. 補充資訊

- **[ComfyUI 潛像素圖 (Latent Image) 節點教程](Guide/comfyui-guide-latent-image.md)**  
  了解如何高效使用潛像素圖節點進行圖像處理。

- **[ComfyUI Clip 和 KSampler 的關係](Guide/comfyui-guide-clip-to-ksampler.md)**  
  深入理解 Clip 節點與 KSampler 的交互，優化生成結果。

---
