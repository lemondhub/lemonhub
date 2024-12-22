# [Lemonhub ComfyUI](index-comfyUI.md) 創建你的第一張 AI 圖片

## 安裝 ComfyUI

### 安裝 ComfyUI 基本需求

1. **安裝 Python**  
   下載 Python：https://www.python.org/downloads/release/python-3131/

2. **安裝 Git**  
   下載 Git：https://git-scm.com/

3. **建議安裝 Conda**  
   下載 Conda：https://docs.anaconda.com/miniconda/

### 安裝 ComfyUI 具體步驟

1. **啟動終端機 (Terminal)**

2. **如果使用 Conda**  
   輸入以下指令來建立新環境 (conda environment)：

   ```bash
   conda create -n comfyui_env python=3.10
   ```

   - `comfyui_env` 是環境名稱，可自行定義。
   - `python=3.10` 是給 ComfyUI 使用的 Python 版本。

   切換到新建立的環境：

   ```bash
   conda activate comfyui_env
   ```

3. **如果沒使用 Conda**  
   跳過 Conda 部分，從此步驟開始。

4. **安裝 PyTorch**  
   根據顯示卡的 CUDA 版本安裝對應的 PyTorch，若不確定，建議詢問 ChatGPT：

   ```bash
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
   ```

5. **使用 Git 下載 ComfyUI**  
   輸入以下指令下載 ComfyUI：

   ```bash
   git clone https://github.com/comfyanonymous/ComfyUI.git
   ```

## 啟動 ComfyUI

1. 在終端機中切換到 ComfyUI 目錄：

   ```bash
   cd ComfyUI
   ```

   如果已經更改過路徑，請確保已進入 ComfyUI 資料夾。

2. 運行 ComfyUI 伺服器：

   ```bash
   python main.py
   ```

3. 打開瀏覽器（Chrome、Safari 等），在地址欄輸入：

   ```
   http://127.0.0.1:8188
   ```

   這樣就可以啟動 ComfyUI。

## 初次運行 ComfyUI

1. ComfyUI 會顯示範例預設設定，點選 **Queue** 開始運行。

2. 如果直接運行會出現錯誤，這是因為新安裝的 ComfyUI 沒有任何模型需要手動處理。

3. ComfyUI 範例預設的 checkpoint 名為 `v1-5-pruned-emaonly.ckpt`，可以在 [Hugging Face](https://huggingface.co/) 下載需要的模型。

   下載連結：[v1-5-pruned-emaonly.ckpt](https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5/blob/main/v1-5-pruned-emaonly.ckpt)

4. 下載後，將 `v1-5-pruned-emaonly.ckpt` 文件放置在 ComfyUI 資料夾中的以下路徑：

   ```
   comfyUI/models/checkpoints/
   ```

5. 放置好模型後，重新啟動 ComfyUI。在終端機中按下 `Ctrl + C` 關閉正在運行的 ComfyUI，然後再次輸入以下指令啟動 ComfyUI：

   ```bash
   python main.py
   ```

6. 在checkpoint中的model選取剛剛下載的`v1-5-pruned-emaonly.ckpt`

7. 最後點選 **Queue**，這時就能生成第一張圖片了。

## 再次啟動 ComfyUI

如果有使用 Conda，重新開啟終端機 (Terminal) 時，請記得確認是否啟用正確的 Conda 環境。

```
conda activate comfyui_env
cd ComfyUI
python main.py
```

這樣就完成了 ComfyUI 的安裝與使用流程！
