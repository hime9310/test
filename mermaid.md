整理する前に、訂正が1点あります。公式の制限ページを確認し直したところ、対象範囲が「標準ハーネスの Agent とクラシック チャットボット」と書かれており、New UI（GitHub Copilot ハーネス）で同じ数値が適用されるかは明記されていません。これまで New UI にも当てはまる前提でお伝えしていましたが、そこは未確認です。下の表は公式に載っている数値で、New UI への適用は MS に確認が必要です。

**ご質問への回答**

- **25 件**：SharePoint の URL で登録するナレッジだけにかかる上限です。
- **500 件**：ファイルのアップロードなど、他の種類も含めたナレッジ全体の合計の上限です（公式の表記は「全種類の合計で 500」）。
- **両者の関係**：SharePoint の 25 件が 500 件の内数かどうかは、公式に明記がありません。表記からは「SharePoint の URL も含めて合計 500」と読むのが自然です。今回の構成はどちらの読み方でも収まります。

**制限の整理**

| 項目 | 制限事項 | 補足 | 公式URL |
|---|---|---|---|
| SharePoint の URL 数 | 1 Agent あたり 25 件まで | 生成オーケストレーション使用時。数えるのは登録した URL の数で、配下のファイル数ではない | [Quotas and limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas) |
| ナレッジ全体の数 | 1 Agent あたり 500 件まで（全種類の合計） | フォルダ1つの登録は1件と数える | 同上 |
| 検索される範囲 | 登録した URL とそのサブフォルダすべて | 親フォルダ・隣のフォルダ・他のサイトは、別途登録しない限り読まれない | [Add SharePoint as a knowledge source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint) |
| 読める形式（SharePoint） | Word（DOC/DOCX）、PowerPoint（PPT/PPTX）、PDF、モダンページ | OneNote・HTML・Markdown は対象外 | [Quotas and limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas) |
| ファイルサイズ（SharePoint） | 7MB 未満。条件を満たせば 200MB まで | 200MB の条件は、同じテナントの M365 Copilot ライセンスと、テナント グラフ グラウンディングの ON | 同上 |
| 配下のファイル数・階層の深さ | 公式に記載なし | 上限が無いとも書かれていない | 同上 |
| ファイルのアップロード（サイズ） | 1ファイル 512MB まで | SharePoint を経由せず、Copilot Studio に直接アップロードする方式 | 同上 |
| ファイルのアップロード（数） | 500 ファイルまで | 公式ページの表示は「5001」。500 に脚注番号の 1 が付いたものと読める | 同上 |
| アクセス権 | 利用者本人が読める内容だけを返す | SharePoint サイトに最低でも「閲覧」の権限が必要 | [Add SharePoint as a knowledge source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint) |
| 文書内のリンク | リンク先は読まれない | リンク先も使うなら、別途ナレッジとして登録する | 同上 |

**MS への問い合わせに足したい項目**

1. 上記の制限（特に 25 件と 500 件）は、New UI の Agent にもそのまま適用されるか。
2. SharePoint の URL 25 件は、ナレッジ全体 500 件の内数か。
3. フォルダ配下のファイル数や階層の深さに、上限や推奨値はあるか。