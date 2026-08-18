# shared_core

Petit Works apps 共通の Flutter ウィジェット/モデル集です。
[kokugo-kore](https://github.com/org-zka32101/kokugo-kore)、`social_quiz_app`、
および今後増える他アプリから、各アプリの `pubspec.yaml` に git dependency として
参照されることを想定しています。

## 含まれるもの

- `lib/models/` — 共通データモデル（ユーザープロフィール、クエスト、バッジ、アバター、キャラクターなど）
- `lib/providers/` — Riverpod ベースの状態管理プロバイダー
- `lib/widgets/` — 共通UIウィジェット（クイズ、デイリーボーナス、コインショップなど）
- `lib/services/` — Firebase連携などの共通サービス
- `lib/theme/` — アプリ共通のベーステーマ
- `lib/assets/` — バッジアイコン、アバター、UI素材などの共通アセット

エントリポイントは `lib/shared_core.dart`（バレルファイル）です。

## 利用方法

利用側アプリの `pubspec.yaml` に以下のように追加します。

```yaml
dependencies:
  shared_core:
    git:
      url: https://github.com/org-zka32101/shared_core.git
      ref: main
```

```dart
import 'package:shared_core/shared_core.dart';
```

## 注意事項

- 元の `kokugo-kore` モノレポ内では `shared_core` が姉妹パッケージ
  `cross_promo_kit`（クロスプロモーション機能）を relative path 依存で
  再エクスポートしていましたが、`cross_promo_kit` はまだ独立した git
  リポジトリとして切り出されていないため、このリポジトリでは当該の
  依存・再エクスポートを一旦コメントアウトしています
  （`lib/shared_core.dart` 参照）。`cross_promo_kit` が独立リポジトリ化
  され次第、git dependency として追加し復活させてください。
