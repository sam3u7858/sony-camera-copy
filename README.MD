# Sony Camera Auto Fast Copy Script

## 功能說明

這個腳本專為 Sony 相機用戶設計，能夠自動偵測相機存儲卡並快速複製檔案到指定目錄結構。

### 主要功能

- 🔍 自動偵測 H: 磁碟機（JPEG/影片）和 I: 磁碟機（RAW 檔案）
- ⚡ 使用高速多執行緒複製技術（robocopy）
- 📊 即時顯示複製進度和檔案資訊
- 📁 自動建立以日期命名的整理資料夾
- 🛡️ 完整的錯誤處理和重試機制

### 複製路徑對應

- `H:\DCIM\` → `Z:\Vod_Eggs\a7r5 US\{yyyymmdd-標題}\JPG\`
- `H:\M4ROOT\CLIP\` → `Z:\Vod_Eggs\a7r5 US\{yyyymmdd-標題}\MP4\`
- `I:\DCIM\` → `Z:\Vod_Eggs\a7r5 US\{yyyymmdd-標題}\RAW\`

## 安裝步驟

### 1. 安裝 Python 依賴套件

```bash
pip install -r requirements.txt
```

### 2. 確認目標目錄存在

確保 `Z:\Vod_Eggs\a7r5 US\` 目錄存在且可寫入。

## 使用方法

### 1. 連接相機存儲卡

將 Sony 相機的存儲卡連接到電腦，確保：

- JPEG/影片卡被識別為 H: 磁碟機
- RAW 檔案卡被識別為 I: 磁碟機

### 2. 執行腳本

```bash
python sony_camera_auto_fastcopy.py
```

### 3. 輸入拍攝標題

腳本會提示您輸入標題，最終資料夾名稱格式為：`yyyymmdd-標題`

### 4. 等待複製完成

腳本會顯示詳細的進度資訊：

- 檔案數量和總大小
- 即時複製進度條
- 複製速度和剩餘時間
- 最終複製結果

## 進度顯示範例

```
=== Sony Camera Auto Fast Copy Script ===
檢查相機存儲卡...
H: drive exists: True
I: drive exists: True

當前日期: 20231215
請輸入標題 (將建立為 {日期-標題} 格式): 聖誕節拍攝

建立目標資料夾: 20231215-聖誕節拍攝

--- 開始複製 H: 磁碟機內容 ---
正在分析來源資料夾: H:\DCIM
找到 127 個檔案，總大小: 2.3GB
開始複製JPEG照片: H:\DCIM → Z:\Vod_Eggs\a7r5 US\20231215-聖誕節拍攝\JPG
複製JPEG照片: 100%|████████████| 100/100% [02:34<00:00]
✓ 成功複製JPEG照片

正在分析來源資料夾: H:\M4ROOT\CLIP
找到 15 個檔案，總大小: 4.7GB
開始複製MP4影片: H:\M4ROOT\CLIP → Z:\Vod_Eggs\a7r5 US\20231215-聖誕節拍攝\MP4
複製MP4影片: 100%|████████████| 100/100% [05:21<00:00]
✓ 成功複製MP4影片

--- 開始複製 I: 磁碟機內容 ---
正在分析來源資料夾: I:\DCIM
找到 127 個檔案，總大小: 6.1GB
開始複製RAW檔案: I:\DCIM → Z:\Vod_Eggs\a7r5 US\20231215-聖誕節拍攝\RAW
複製RAW檔案: 100%|████████████| 100/100% [08:15<00:00]
✓ 成功複製RAW檔案

=== 複製完成總結 ===
H: DCIM → JPG: ✓ 成功
H: M4ROOT/CLIP → MP4: ✓ 成功
I: DCIM → RAW: ✓ 成功

整體結果: ✓ 全部成功
```

## 系統需求

- Windows 10/11
- Python 3.7+
- 至少 8GB 可用磁碟空間（建議）
- robocopy（Windows 內建）

## 注意事項

- 確保目標磁碟機有足夠空間
- 複製過程中請勿移除存儲卡
- 可隨時按 Ctrl+C 取消操作
- 腳本會自動跳過已存在的檔案（避免重複複製）

## 故障排除

### 磁碟機未偵測到

- 檢查存儲卡是否正確插入
- 確認磁碟機代號是否為 H: 和 I:
- 嘗試重新插拔存儲卡

### 複製失敗

- 檢查目標目錄是否有寫入權限
- 確認磁碟空間是否充足
- 查看詳細錯誤訊息進行診斷

### 進度顯示異常

- 確認已安裝 tqdm 套件
- 重新安裝依賴套件：`pip install -r requirements.txt`
