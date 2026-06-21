# Arnoll Rhythmboard 1

[English](README.md) | 繁體中文  
> 內容使用 Google AI Studio 上的 gemma-4-26b-a4b-it 進行翻譯以提高開發效率  
> 中文內容可能為非最新版本，請以英文版本為準

一款適用於大多數電腦節奏遊戲、易於自定義的控制器。

支援多款遊戲，包括：

| | | | |
| - | - | - | - |
| osu! | DJMAX RESPECT V | Quaver | vivid/stasis |
| Milthm | Rhythm Doctor | Sparebeat | Polylylyrhythm |
| Estella | In Falsus (理論上) | 更多 | |

整體佈局與預設按鍵配置已針對 DJMAX RESPECT V 與個人按鍵配置進行優化，但也支援任何類似款式的遊戲。您只需要在 [ZMK Studio](https://zmk.studio/) 中編輯按鍵配置，即可輕鬆針對您正在玩的遊戲或個人偏好的按鍵綁定進行優化。

<!-- TODO: 圖片與照片 -->

## 目錄

- [Arnoll Rhythmboard 1](#arnoll-rhythmboard-1)
  - [目錄](#目錄)
  - [快速上手](#快速上手)
    - [安裝韌體](#安裝韌體)
    - [從硬體開始組裝](#從硬體開始組裝)
      - [物料清單 (BOM)](#物料清單-bom)
      - [1. 準備並列印 PCB](#1-準備並列印-pcb)
      - [2. 焊接所有組件](#2-焊接所有組件)
      - [3. 組裝](#3-組裝)
      - [4. 安裝 ZMK 韌體](#4-安裝-zmk-韌體)
  - [預設按鍵配置](#預設按鍵配置)
    - [自定您的按鍵配置](#自定您的按鍵配置)
  - [待辦事項](#待辦事項)

## 快速上手

[安裝韌體](#install-firmware)  
[從硬體開始組裝您的 Rhythmboard](#build-from-hardware)  
[物料清單 (BOM)](#bom)

### 安裝韌體
<details>

<summary>如果您熟悉 RP2040 微控制器或 Raspberry Pi Pico 的開發，請點擊此處查看簡短說明。</summary>

1. 前往 `Actions` 分頁。
2. 點擊最新的 workflow 執行紀錄。
3. 找到 `Artifacts` 區塊，找到 `firmware`，並點擊右側的下載圖示來下載 `firmware.zip`。
   **如果您找不到 `Artifacts` 區塊**，請點擊 [這裡](https://github.com/theArnoll/RhythmBoard/actions/runs/27726159548/artifacts/7710387346)。
4. 將您的板子以 BOOTSEL 模式連接到電腦（按住 BOOT 鍵的同時插入 RP2040-Zero）。
5. 解壓縮剛下載的 `firmware.zip` 並找到裡面的 `.uf2` 檔案。
6. 將 `.uf2` 檔案拖放至 RP2040-Zero 的 USB 磁碟機中（名稱通常為 `RPI-RP2`），即可完成。

---

</details>

1. 前往 `Actions` 分頁。
2. 點擊最新的 workflow 執行紀錄。
3. 找到 `Artifacts` 區塊，找到 `firmware`，並點擊右側的下載圖示來下載 `firmware.zip`。
   **如果您找不到 `Artifacts` 區塊**，請點擊 [這裡](https://github.com/theArnoll/RhythmBoard/actions/runs/27726159548/artifacts/7710387346)。
4. 按住 RP2040-Zero 上的 `BOOT` 按鈕。**在將 RP2040-Zero 插入電腦之前請勿放開**。插入後再放開按鈕。您應該會在電腦上看到一個新的 USB 裝置出現，名稱通常為 `RPI-RP2`。
5. 解壓縮剛下載的 `firmware.zip`，在解壓縮後的資料夾中找到 `.uf2` 檔案，並將其拖入或複製到上一步出現的 USB 磁碟機中。
6. 複製完成後，USB 磁碟機會自動斷開連接，RP2040-Zero 將會重新啟動。您的 Rhythmboard 現在已可以使用最新的功能。

### 從硬體開始組裝

#### 物料清單 (BOM)

- RP2040-Zero x 1
- 針型排針 (Machined Pin Header) (共 23 Pin：9 Pin x 2 + 5 Pin)
- 針型排母 (Machined Female Header) (共 23 Pin：9 Pin x 2 + 5 Pin)
- MX profile 機械軸熱插拔底座 (hotswap socket) x 17
- 1N4148W 二極體 (SOD-123 封裝) x 17

- MX profile 機械軸 x 17
- 鍵帽
  - 1u x 12
  - 1.25u x 1
  - 1.5u x 2
  - 2.25u x 2
- 2u PCB 固定式平衡桿 (stabilizers) x 2

#### 1. 準備並列印 PCB

1. 在[這裡](/PCB/RhythmGameControllerKiCad/production/Gerber.zip)找到 Gerber `.zip` 檔案。
2. 找一家 PCB 製造商來製作您的 PCB。
   我個人使用的是 [JLCPCB](https://jlcpcb.com/) 並經過測試。提供的檔案支援 PCB 組件加工 (PCBA)，但其他製造商可能不支援。如果您偏好其他製造商並希望使用 PCBA 服務，請自行配置必要的檔案。
   *本專案並非贊助內容，但歡迎任何人的贊助 (不限於 JLCPCB 喔 LOL)。*
   > 若需 JLCPCB PCBA 所需的檔案：BOM 檔案位於 [/PCB/RhythmGameControllerKiCad/production/bom.csv](/PCB/RhythmGameControllerKiCad/production/bom.csv)，元件位置 (CPL) 檔案位於 [/PCB/RhythmGameControllerKiCad/production/positions.csv](/PCB/RhythmGameControllerKiCad/production/positions.csv)。
3. 下單並等待您的 PCB 送達。

#### 2. 焊接所有組件

雖然我使用了 PCBA 服務來處理 SMD (表面黏著) 零件，但如果您是手動焊接，建議先焊接二極體，接著再焊接軸座。

對於 THT (通孔) 零件，我選擇的工作流程是先將針型排針焊接在 RP2040-Zero 上。接著，利用 RP2040-Zero 來確認並調整角度，然後再將針型排母焊接在 PCB 上。

#### 3. 組裝

1. 安裝平衡桿。
2. 安裝 RP2040-Zero。
3. 安裝軸體。
4. 安裝鍵帽。 <!-- 註：待上傳後需在此添加定位板與外殼安裝說明 -->

#### 4. 安裝 ZMK 韌體

請依照[這裡](#安裝韌體)所寫的步驟將韌體安裝到您的 RP2040-Zero。

## 預設按鍵配置

[here](https://gist.github.com/theArnoll/bf225b66670c3d527fa65544731ffbb3#file-layout-notes-md) 有更好的視覺效果的版本

層次 0 (預設)
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">ZMK<br>Studio</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">Alt+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">W</td>
    <td align="center">E</td>
    <td align="center">R</td>
    <td align="center">T</td>
    <td align="center">U</td>
    <td align="center">I</td>
    <td align="center">O</td>
    <td align="center">P</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">G</td>
    <td align="center">J</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">G</td>
    <td colspan="2" align="center">J</td>
  </tr>
</table>

層次 1
<table>
  <tr>
    <td width="12.5%" align="center">1</td>
    <td width="12.5%" align="center">ZMK<br>Studio</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">to 3</td>
    <td width="12.5%" align="center">2</td>
  </tr>
  <tr>
    <td align="center">F10</td>
    <td align="center">L⇧</td>
    <td align="center">↑</td>
    <td align="center">↓</td>
    <td align="center">←</td>
    <td align="center">→</td>
    <td align="center">R⇧</td>
    <td align="center">F11</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">A</td>
    <td align="center">↹</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">␣</td>
    <td colspan="2" align="center">↵</td>
  </tr>
</table>

<details>
<summary> 層次 2 (層次切換) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">to 0</td>
    <td width="12.5%" align="center">to 1</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">to 0</td>
    <td width="12.5%" align="center">to 0</td>
  </tr>
  <tr>
    <td align="center">to 3</td>
    <td align="center">to 4</td>
    <td align="center">to 5</td>
    <td align="center">to 6</td>
    <td align="center">to 7</td>
    <td align="center">to 8</td>
    <td align="center">to 9</td>
    <td align="center">to 10</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">none</td>
    <td align="center">none</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 0</td>
    <td></td>
    <td colspan="2" align="center">none</td>
    <td colspan="2" align="center">none</td>
  </tr>
</table>
</details>

<details>
<summary> 層次 3 (QWERTY DFJK 預設佈局，多數遊戲的標準配置) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">none</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">ALT+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">A</td>
    <td align="center">S</td>
    <td align="center">D</td>
    <td align="center">F</td>
    <td align="center">J</td>
    <td align="center">K</td>
    <td align="center">L</td>
    <td align="center">;</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">V</td>
    <td align="center">N</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">V</td>
    <td colspan="2" align="center">N</td>
  </tr>
</table>
</details>

<details>
<summary> 層次 4 (快捷鍵墊) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">none</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">ALT+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">A</td>
    <td align="center">X</td>
    <td align="center">C</td>
    <td align="center">V</td>
    <td align="center">Z</td>
    <td align="center">N</td>
    <td align="center">HOME</td>
    <td align="center">END</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">LALT</td>
    <td align="center">LGUI</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 2</td>
    <td></td>
    <td colspan="2" align="center">LCTRL</td>
    <td colspan="2" align="center">LSHIFT</td>
  </tr>
</table>
</details>

<details>
<summary> 層次 5~10 (使用者定義) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">none</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">ALT+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">W</td>
    <td align="center">E</td>
    <td align="center">R</td>
    <td align="center">T</td>
    <td align="center">U</td>
    <td align="center">I</td>
    <td align="center">O</td>
    <td align="center">P</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">G</td>
    <td align="center">J</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">G</td>
    <td colspan="2" align="center">J</td>
  </tr>
</table>
</details>

### 自定您的按鍵配置

1. 按下「ZMK Studio」鍵。
2. 前往 [ZMK Studio](https://zmk.studio/)。
3. 您的瀏覽器可能會顯示 COM 埠連接彈出視窗（至少基於 Chromium 的瀏覽器會顯示）。請選擇您的 Rhythmboard 所連接的 COM 埠。（在 Windows 上通常不會是 COM1 或 COM2）。
4. 依照您的需求，在 ZMK Studio 上自定義按鍵綁定、按鍵配置與層次。
   > ⚠️ 注意：目前不支援無線相關選項。

## 待辦事項
<!-- TODO: -->
- 上傳定位板檔案
- 設計外殼 <!-- 註：檔案上傳後需修改 #### 3. 組裝 部分 -->

---

基於 [theArnoll/ZMK-4x3-Keyboard](https://github.com/theArnoll/ZMK-4x3-Keyboard) 開發。