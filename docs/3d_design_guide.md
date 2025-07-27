# QRコード名刺 - 3D設計ガイド

## 📐 設計仕様

### 基本構造
```
全体: 60mm × 60mm × 2.0mm
├── ベース層: 60mm × 60mm × 1.0mm (白PLA - Layer 1-5)
└── QR層: 50mm × 50mm × 1.0mm (黒PLA - Layer 7-10)
    ├── QRコード部分: 中央配置
    └── マージン: 各5mm
```

### レイヤー構成
- **Layer 1-5**: 白PLA ベース (1.0mm)
- **Layer 6**: フィラメント交換ポイント (Pause at Layer)
- **Layer 7-10**: 黒PLA QRコード (1.0mm)

## 🛠️ Method 1: Fusion 360での設計

### Step 1: ベースプレート
1. **新規デザイン開始**
2. **Sketch → Rectangle**
   - 中心: 原点(0,0)
   - サイズ: 60mm × 60mm
3. **Extrude**
   - 距離: 1.0mm
   - 名前: "Base_White"

### Step 2: QRコードインポート
1. **QRコードSVG準備** (`qr_assets/`に保存)
2. **Insert → Insert SVG**
3. **配置**: ベース中央
4. **スケール**: 50mm × 50mm

### Step 3: QRコード3D化
1. **QRコード黒部分選択**
2. **Extrude** 
   - 距離: +1.0mm (ベースから上に)
   - 名前: "QR_Black"

### Step 4: STL出力
1. **File → Export → STL**
2. **設定**: 
   - Resolution: High
   - Units: mm
3. **保存先**: `3d_models/qr_card.stl`

## 🛠️ Method 2: Blender代替手法

### Manual STL作成
1. **オンラインSTL生成ツール使用**
2. **QRコードをHeightmap変換**
3. **STL Editor**で厚み調整

### Tinkercad使用
1. **QRコード画像 → SVG → Tinkercad**
2. **ベースプレート作成**
3. **QRパターン追加**
4. **STL Export**

## 🎨 印刷設定 (Neptune 4 Pro)

### Cura設定
```
Layer Height: 0.2mm
Infill: 100%
Print Speed: 30-40mm/s
Nozzle Temp: 210-215°C (PLA)
Bed Temp: 60°C
Support: No
```

### マルチカラー設定
```
Post Processing → Modify G-Code
→ Pause at height: 1.0mm (Layer 6)
→ Manual filament change: White → Black
```

### 品質向上設定
- **Linear Advance**: 有効
- **Retraction**: 6mm (PLA標準)
- **Travel Speed**: 150mm/s
- **First Layer**: 低速 (20mm/s)

## 📁 ファイル管理

### 作業ファイル
- `qr_assets/github_qr.svg` - QRコード元データ
- `3d_models/qr_card_base.stl` - ベース部分
- `3d_models/qr_card_complete.stl` - 完成版
- `print_settings/qr_card_cura.curaprofile` - 印刷設定

### バックアップ
- Fusion 360: `.f3d`ファイル保存
- Blender: `.blend`ファイル保存
- STL: 複数解像度で保存

## 🚀 次期バージョン: クリップ一体型

### 設計拡張
```
全体: 150mm × 80mm × 2mm
├── QRカード部: 60mm × 40mm (切り取り線)
├── クリップ部: 90mm × 20mm (バネ機構)
└── ランナー: 2mm幅接続部
```

### 技術チャレンジ
- 一体成型バネ機構
- 切り取り線最適化 (0.2mm溝)
- 5-10枚書類対応強度

---
**作成**: 2025-07-21
**対象**: Neptune 4 Pro + PLA
**更新予定**: 3Dモデル完成時
