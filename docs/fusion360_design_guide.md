# QRコード名刺 - Fusion 360設計ガイド（改訂版）

## 🎯 Fusion 360での高品質設計

### なぜFusion 360を選択？
- **CAD品質の精度**: ±0.1mm の寸法精度
- **確実なSTLエクスポート**: 3Dプリント最適化
- **プロフェッショナル**: 面談での技術力証明
- **拡張性**: 将来のクリップ一体型対応

## 📐 設計仕様（確定版）

### 基本構造
```
全体: 60mm × 60mm × 2.0mm
├── ベース層: 60mm × 60mm × 1.0mm (白PLA)
└── QR層: 50mm × 50mm × 1.0mm (黒PLA)
    ├── QRコード領域: 中央配置
    └── マージン: 各5mm
```

## 🛠️ Fusion 360設計手順

### Step 1: 新規プロジェクト作成
1. **Fusion 360起動**
2. **新規デザイン作成**
3. **単位設定**: mm（ミリメートル）
4. **プロジェクト名**: "QRコード名刺"

### Step 2: ベースプレート設計
```
1. Create → Sketch → XY平面選択
2. Rectangle → 中心点指定
3. 寸法: 60mm × 60mm
4. Finish Sketch
5. Create → Extrude
   - 距離: 1.0mm
   - 名前: "Base_White"
```

### Step 3: QRコードSVGインポート
```
1. Insert → Insert SVG
2. ファイル選択: github_qr.svg
3. 配置: ベース中央
4. スケール: 50mm × 50mm
5. Sketch平面: ベース上面選択
```

### Step 4: QRコード3D化
```
1. インポートしたSVGスケッチを選択
2. Create → Extrude
   - 距離: +1.0mm (ベースから上に)
   - 操作: Join
   - 名前: "QR_Pattern"
```

### Step 5: 品質確認
```
1. Inspect → Measure
   - 全体寸法: 60 × 60 × 2mm確認
   - QR領域: 50 × 50mm確認
2. Visual Style → Shaded with Edges
3. 詳細確認
```

### Step 6: STLエクスポート
```
1. File → Export
2. 形式: STL (.stl)
3. 設定:
   - Refinement: High
   - Surface Deviation: 0.01mm
   - Normal Deviation: 5°
   - Maximum Edge Length: 0.1mm
4. 保存先: 3d_models/qr_card_fusion360.stl
```

## 🎨 マルチカラー印刷対応設計

### レイヤー分割方法
```
1. ベース部分のみエクスポート
   - Component選択: "Base_White"のみ
   - STL出力: qr_base_white.stl

2. QRパターン部分のみエクスポート
   - Component選択: "QR_Pattern"のみ
   - STL出力: qr_pattern_black.stl

3. 統合版もエクスポート
   - 全体選択
   - STL出力: qr_card_complete.stl
```

### Cura設定対応
- **レイヤー高さ**: 0.2mm
- **Layer 1-5**: 白PLA (1.0mm)
- **Layer 6**: Pause at Layer設定
- **Layer 7-10**: 黒PLA (1.0mm)

## 📁 ファイル管理

### 作業ファイル
- `qr_assets/github_qr.svg` - SVG元データ（要作成）
- `3d_models/QRコード名刺.f3d` - Fusion 360ファイル
- `3d_models/qr_card_fusion360.stl` - 統合STL
- `3d_models/qr_base_white.stl` - 白ベース部分
- `3d_models/qr_pattern_black.stl` - 黒パターン部分

### バックアップ戦略
- Fusion 360クラウド同期
- ローカルファイルコピー
- 複数解像度STL保存

## 🚀 次期バージョン対応

### クリップ一体型設計準備
```
1. 現在の名刺部分をComponent化
2. クリップ部分を別Component設計
3. Assembly機能で統合
4. Motion Study でクリップ動作確認
```

### パラメトリック設計
- QRコードサイズ: パラメータ化
- 厚み: 調整可能
- マージン: 可変設定

## 💡 品質向上のコツ

### 寸法精度
- スケッチ拘束を完全に
- 寸法駆動設計
- Feature履歴管理

### 3Dプリント最適化
- フィレット: R0.2mm以上
- 最小厚み: 0.4mm以上
- オーバーハング: 45度以下

### 面談プレゼン用
- レンダリング作成
- 断面図表示
- アニメーション作成

---
**作成**: 2025-07-21
**対象**: Fusion 360 + Neptune 4 Pro
**品質**: CADプロフェッショナル仕様
