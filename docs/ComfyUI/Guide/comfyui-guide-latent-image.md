# [Lemonhub ComfyUI](../index-comfyUI.md) 潛像素圖 (Latent Image) 節點教程

# 潛在圖像的意義

潛在圖像是生成式模型中的一個重要概念，尤其是在像 **Stable Diffusion** 這樣的圖像生成模型中。它是生成過程中的中間表示，並不直接是人眼可見的圖像，而是經過壓縮和轉換後的低維空間表示。

## 1. 壓縮表示
潛在圖像代表的是圖像的壓縮版本，處於一個低維空間（潛在空間）。在這個空間中，圖像的關鍵特徵（如形狀、顏色、紋理等）被提取出來並編碼。這樣的表示比原始高維像素空間更容易處理。

## 2. 生成過程的中間階段
在像 **Stable Diffusion** 的模型中，潛在圖像是圖像生成的中間結果。首先，模型從一個隨機噪聲開始，然後逐步將這個隨機噪聲轉換為潛在圖像。這個過程依賴於模型的學習，最終調整潛在圖像使其接近目標圖像。

## 3. 去噪過程
在基於擴散（diffusion）的生成模型中，潛在圖像的生成過程涉及去噪。模型將噪聲引入潛在圖像，然後進行反向擴散（去噪）操作，最終得到清晰的潛在圖像。這些潛在圖像會被解碼為最終的可視圖像。

## 4. 模型計算效率
使用潛在圖像而不是直接操作原始圖像，有助於提高計算效率。潛在空間的維度較低，處理潛在圖像比處理原始圖像要簡單，這使得模型能更高效地進行圖像生成。

## 具體示例：Stable Diffusion 模型中的潛在圖像

在 **Stable Diffusion** 中，潛在圖像的生成過程可以分為以下幾個步驟：

1. **開始於隨機噪聲**  
   生成過程從隨機噪聲圖像開始，這個圖像本身並不包含有意義的信息。

2. **生成潛在圖像**  
   通過反向擴散過程，模型逐步調整這個隨機噪聲，使其符合文本提示（如「一隻貓」）的特徵，得到潛在圖像。

3. **解碼潛在圖像**  
   最終生成的潛在圖像需要通過解碼過程（通常由 VAE 實現），將其轉換回高維度的圖像，即人眼可見的最終生成圖像。

## 潛在圖像 vs. 生成圖像

- **潛在圖像**：是生成過程中的中間表示，通常不直接可見，因為它位於低維空間，包含的是抽象的、混合的特徵。
- **生成圖像**：是解碼後的結果，是經過潛在圖像處理後，最終呈現的可視圖像。

## 總結
潛在圖像是一種簡化且抽象的圖像表示，它在生成過程中扮演著關鍵角色，幫助模型在更高效的空間中生成圖像，最終生成出符合要求的視覺效果。