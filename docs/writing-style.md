# 技術ブログ執筆スタイルガイド

## 1. 記事の種類と構造

### 1.1 記事の種類
1. 詳細な技術解説
   - フレームワークやライブラリの使用方法
   - アーキテクチャ設計の解説
   - 実装パターンの説明

2. インストール・設定ガイド
   - ソフトウェアのインストール手順
   - 環境構築手順
   - 設定変更の手順

3. クイックリファレンス
   - 短いコマンドや設定例
   - トラブルシューティングのヒント
   - よく使う操作の備忘録

4. セキュリティ実装
   - 認証・認可の実装
   - セキュリティ設定
   - 証明書管理

### 1.2 メタデータ
```yaml
---
title: 具体的で技術的な内容を反映したタイトル
tags: ["主要技術1", "主要技術2", "関連ツール", "プラットフォーム"]
categories: ["主要カテゴリ", "サブカテゴリ"]
---
```

### 1.3 記事構成
1. 導入部
   - 記事の目的と達成目標を明確に説明
   - 必要な前提条件や環境を明示
   - 長い記事の場合は目次を含める（`<!-- toc -->`）
   - 関連する過記事への参照（ある場合）

2. 本文（記事の種類に応じて）
   a. 詳細な技術解説の場合:
      - 技術の概要説明
      - 実装手順の詳細
      - コード例と説明
      - エッジケースの考慮

   b. インストール・設定ガイドの場合:
      - スクリーンショットによる手順説明
      - 設定値の説明
      - 確認手順
      - トラブルシューティング

   c. クイックリファレンスの場合:
      - 簡潔な問題提起
      - 直接的な解決方法
      - 検証方法

   d. セキュリティ実装の場合:
      - セキュリティ上の考慮事項
      - 実装の詳細手順
      - 検証方法
      - 運用上の注意点

3. まとめ
   - 実装結果の確認方法
   - クリーンアップ手順（必要な場合）
   - 運用上の注意点

## 2. 執筆スタイル

### 2.1 技術的特徴
- 実践的で再現可能な手順を重視
- コマンドとその実行結果を併記
- バージョン情報を明確に記載
- エッジケースや注意点を明示
- 依存関係の明確化
- 代替実装の提示（可能な場合）

### 2.2 説明スタイル
- 簡潔で直接的な文体
- 技術的な正確性を重視
- 実務での使用経験に基づく実践的なヒントを提供
- 必要に応じて図表やスクリーンショットを活用
- 一貫した用語の使用
- 段階的な複雑さの導入

### 2.3 視覚的な説明
- UI操作の場合は必ずスクリーンショット
- 画面遷移の順序を明確に
- 重要な設定項目の強調
- アーキテクチャ図の活用
- 一貫した画像サイズ（width="1024"）

### 2.4 セキュリティ配慮
- 機密情報の適切なマスキング
- セキュリティ上の注意点の明示
- 本番環境での運用考慮
- 認証情報の取り扱い注意

## 3. フォーマット規則

### 3.1 コードブロック
```
# コマンド実行
command arg1 arg2

# 実行結果
result line 1
result line 2
```

- 言語指定を必ず含める（bash, java, yaml等）
- 実行コマンドと出力は別々のブロックで表示
- 長いコマンドは可読性のため適切に改行
- コメントで説明を追加

### 3.2 設定ファイル
```yaml
# 設定例
key1: value1
key2: value2
```

- フォーマットに応じた言語指定
- インデントの統一
- コメントによる説明
- デフォルト値の明示

### 3.3 注釈とヒント
> [!NOTE]
> 重要な注意点の記載

> [!TIP]
> 実践的なヒントの提供

> [!WARNING]
> 特に注意が必要な点

### 3.4 視覚的要素
- スクリーンショットの統一
  ```html
  <img width="1024" alt="説明的なalt text" src="..." />
  ```
- アーキテクチャ図の活用
- シーケンス図（必要な場合）
- 画面遷移の順序を明確に

### 3.5 エラーハンドリング
- エラーメッセージの例示
- 対処方法の明示
- よくあるトラブルの解決方法
- デバッグ方法の説明

## 4. 相互参照と検証

### 4.1 内部参照
- 関連する自身の記事への参照
  ```markdown
  [前回の記事](/entries/XXX)
  ```
- 前提知識となる記事への参照
- 応用・発展的な記事への参照
- 代替実装への参照

### 4.2 外部リソース
- 公式ドキュメント
- GitHub リポジトリ
- 関連ツールのウェブサイト
- 仕様書やRFC

### 4.3 実装の検証
- 動作確認手順
- テストコード
- 期待される出力
- エラー時の挙動

### 4.4 環境依存の注意点
- OS固有の違い
- バージョンによる差異
- 必要なリソース
- 互換性の考慮

## 5. 技術的焦点

### 5.1 主要な技術分野
- クラウドネイティブ技術
  - Kubernetes/コンテナ
  - クラウドサービス
  - マイクロサービス
- インフラストラクチャ
  - 自動化
  - IaC
  - CI/CD
- アプリケーション開発
  - Spring Framework
  - セキュリティ
  - データベース
- オブザーバビリティ
  - モニタリング
  - ロギング
  - トレーシング

### 5.2 実装アプローチ
- ベストプラクティスの適用
- スケーラビリティの考慮
- セキュリティ対策
- 運用性の向上

### 5.3 環境考慮
- ローカル開発環境
- CI/CD環境
- ステージング環境
- 本番環境

### 5.4 品質確保
- テスト戦略
- パフォーマンス最適化
- セキュリティ対策
- 運用監視

## 6. 記事テンプレート

### 6.1 詳細な技術解説
```markdown
---
title: 技術名とユースケースを含むタイトル
tags: ["主要技術", "フレームワーク", "ツール"]
categories: ["Dev", "主要カテゴリ"]
---

技術の概要と記事の目的を説明。

**目次**
<!-- toc -->

### 技術概要
基本的な説明と使用シーン

### 実装例
```java
// コード例
```

### 実装の詳細
実装手順と注意点

### まとめ
実装のポイントと応用方法
```

### 6.2 インストール・設定ガイド
```markdown
---
title: ソフトウェア名のインストール・設定メモ
tags: ["ソフトウェア", "環境", "ツール"]
categories: ["Dev", "カテゴリ"]
---

インストール目的と前提条件。

### 環境準備
必要な環境とツール

### インストール手順
スクリーンショットと手順

### 設定
設定項目と説明

### 動作確認
確認手順と期待される結果
```

### 6.3 クイックリファレンス
```markdown
---
title: 特定の操作や設定に関する簡潔なタイトル
tags: ["関連技術"]
categories: ["カテゴリ"]
---

問題提起と解決方法を簡潔に説明。

```bash
# 解決コマンド
command arg1 arg2
```

必要に応じて補足説明。
```

## 7. バージョン情報の扱い

### 7.1 バージョン明記
- 使用するソフトウェアのバージョンを明記
- 依存関係のバージョンを明示
- バージョン固有の注意点を記載

### 7.2 バージョン依存の記述
- バージョンによる差異の説明
- 互換性情報の提供
- アップグレード時の注意点

### 7.3 バージョン管理
- 記事の更新履歴
- 古いバージョンの情報の扱い
- 最新バージョンへの対応状況

## 8. スクリーンショットガイドライン

### 8.1 基本ルール
- 幅は1024pxに統一
```html
<img width="1024" alt="Kubernetes Dashboard showing pod status" src="..." />
```
- 適切なalt textの設定
```html
<!-- 良い例 -->
<img alt="Error message showing connection timeout" src="..." />
<!-- 悪い例 -->
<img alt="image" src="..." />
```
- 機密情報のマスク
```html
<!-- APIキーの例 -->
<img alt="API Key page with sensitive information masked" src="..." />
```
- 必要な部分のみをキャプチャ
```html
<!-- エラーメッセージに焦点を当てた例 -->
<img width="1024" alt="Error dialog showing connection refused" src="..." />
```

### 8.2 キャプチャ対象
- UI設定画面
- コマンド実行結果
- エラーメッセージ
- 設定項目の確認

### 8.3 注意点
- 個人情報の非表示
- APIキーなどの認証情報の隠蔽
- 環境固有の情報のマスク
- 画像サイズの最適化

## 9. バージョン情報の例示

### 9.1 ソフトウェアバージョン
```
$ java -version
openjdk version "21.0.1" 2023-10-17
OpenJDK Runtime Environment (build 21.0.1+12-29)
OpenJDK 64-Bit Server VM (build 21.0.1+12-29, mixed mode, sharing)
```

### 9.2 依存関係
```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.2.0</version>
</parent>
```

### 9.3 バージョン互換性
> [!NOTE]
> このガイドはSpring Boot 3.2.0以降を対象としています。
> 3.1.x以前では一部の機能が利用できない可能性があります。

## 7. 一般的なトピック構成

### 7.1 基本構成
1. 環境セットアップ
   ```bash
   # 必要なツールのバージョン
   $ java -version
   $ docker version
   ```

2. インストール手順
   ```bash
   # インストールコマンド例
   $ brew install example
   $ helm install example example/chart
   ```

3. 設定ファイルの説明
   ```yaml
   # 設定ファイル例
   apiVersion: v1
   kind: ConfigMap
   metadata:
     name: example-config
   ```

4. デプロイメント手順
   - 手順の説明
   - 確認コマンド
   - トラブルシューティング

5. 動作確認
   ```bash
   # 確認コマンド例
   $ curl http://localhost:8080/health
   {"status": "UP"}
   ```

### 7.2 補足情報
- トラブルシューティング
- よくあるエラーと対処法
- 運用上の注意点
- クリーンアップ手順

## 10. 記事のメンテナンス

### 10.1 更新方針
- 重要な変更は新しい記事として作成
  ```markdown
  > [!NOTE]
  > この記事は非推奨です。新しい実装方法については[こちらの記事](/entries/XXX)を参照してください。
  ```
- 軽微な修正は既存記事を更新
- 古い情報には注釈を追加

### 10.2 更新履歴
- 更新日時の記録
  ```markdown
  更新: 2024-01-20
  - Spring Boot 3.2.0対応
  - 新しい設定オプションの追加
  ```
- 変更内容の明記
- 影響範囲の説明

### 10.3 廃止された情報の扱い
- 非推奨の明示
  ```markdown
  > [!WARNING]
  > この機能は3.0.0で非推奨となり、4.0.0で削除される予定です。
  ```
- 代替手段の提示
  ```markdown
  ### 代替実装
  新しいバージョンでは次の方法を使用してください：
  ```
- 移行手順の説明
  ```markdown
  ### 移行手順
  1. 既存の設定のバックアップ
  2. 新しい実装への移行
  3. 動作確認
  ```

## 11. 品質基準

### 11.1 技術的品質
- すべての手順が再現可能であること
- バージョン情報が明確であること
- エッジケースへの対応が含まれていること
- クリーンアップ手順が提供されていること
- 実行結果の確認方法が明示されていること

### 11.2 ドキュメント品質
- スクリーンショットが適切に使用されていること
- 更新履歴が管理されていること
- コードブロックに言語指定があること
- 目次が適切に生成されていること
- 参照リンクが有効であること

### 11.3 セキュリティ品質
- 機密情報が適切にマスクされていること
- 認証情報が露出していないこと
- セキュリティ上の注意点が明記されていること
- 本番環境での運用考慮が含まれていること

### 11.4 メンテナンス品質
- バージョン互換性が明確であること
  ```markdown
  > [!NOTE]
  > Spring Boot 3.2.x / Java 21での動作を確認しています
  ```
- 非推奨機能の注意書きがあること
  ```markdown
  > [!WARNING]
  > この機能は次のバージョンで削除されます
  ```
- 代替手段が提示されていること
  ```markdown
  代替として次の方法を使用してください：
  ```
- トラブルシューティング情報が含まれていること
  ```markdown
  ### よくあるエラー
  - エラー1: 原因と対処方法
  - エラー2: 原因と対処方法
  ```

## 12. コード例のベストプラクティス

### 12.1 基本ルール
- 言語指定を含める
- インデントを統一
- コメントを適切に追加
- 実行可能な完全なコード

### 12.2 良い例
```java
// Spring Bootアプリケーションの例
@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

### 12.3 避けるべき例
```java
// 不完全なコード例
@RestController
class MyController {
    // メソッドの説明がない
    // パラメータの説明がない
    public String method() {
        return "result"; // 戻り値の説明がない
    }
}
```

## 13. まとめ

このスタイルガイドは以下を目指しています：

1. 再現可能な技術記事の作成
2. 読者にとって理解しやすい構成
3. 長期的なメンテナンス性
4. セキュリティへの配慮

記事を書く際は、このガイドラインに従いつつ、
必要に応じて柔軟に対応することで、
より良い技術ドキュメントを作成することができます。
