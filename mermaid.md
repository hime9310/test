SharePoint のフォルダ構成に関わる制限を、4項目で整理しました。

**前提**：公式の制限ページは、対象を「standard harness agents and classic chatbots」としています。New UI（GitHub Copilot ハーネス）に同じ数値が適用されるか、違いがあるかは、現時点で不明です。下の数値は公式に載っているもので、New UI への適用は MS に確認が必要です。

### 1. URL 数

- **制限内容**：SharePoint の URL は、1 Agent あたり 25 件まで。数えるのは登録した URL の数で、配下のファイル数ではありません。
- **補足（公式記載）**：
  - "Each agent can have a maximum of 25 SharePoint site URLs when the agent is using generative orchestration."
  - "The agent searches only the folder or site URL you register, and its subfolders. It never accesses parent folders, sibling folders, or other sites unless you register them separately."
- **公式URL**：[Quotas and limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas) / [Add SharePoint as a knowledge source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint)
- **対処方法**：登録は業務カテゴリ単位にして、サブフォルダは個別に登録しない（配下は自動で対象）。「公開／非公開」を分ける場合も、カテゴリごとに「公開」1件だけを登録する。カテゴリ数は 25 未満に収める。

### 2. ナレッジ数

- **制限内容**：ナレッジは、全種類の合計で 1 Agent あたり 500 件まで。フォルダ1つの登録は1件と数えます。
- **補足（公式記載）**："Knowledge sources per agent: 500 across all types"
  - SharePoint の 25 件がこの 500 件の内数かどうかは、明記されていません。
- **公式URL**：[Quotas and limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas)
- **対処方法**：フォルダ単位で登録する限り、数件〜十数件なので対処は不要。ファイルを1つずつ個別に登録する運用だけ避ける。

### 3. ファイルサイズ

- **制限内容**：7MB 未満。Agent の作成者が同じテナントの M365 Copilot ライセンスを持ち、テナント グラフ グラウンディングが ON なら 200MB まで。
- **補足（公式記載）**：
  - "For makers without the Microsoft 365 Copilot license in the same tenant as their agent, due to memory limitations, generative answers can only use SharePoint files that are under 7 MB. If a file is larger than 7 MB, consider splitting it into multiple smaller files."
  - "For better search results from SharePoint and support of files up to 200 MB in size, use a Microsoft 365 Copilot license in the same tenant as your agent, and turn on tenant graph grounding with semantic search."
  - 別のページには "SharePoint and Microsoft Copilot connectors support files up to 512 MB if they have PDF, PPTX, or DOCX extensions." とあり、200MB の記載と数値が合いません。
- **公式URL**：[Quotas and limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas) / [Knowledge sources summary](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio)
- **対処方法**：棚卸しでファイルサイズも拾い、7MB 超のものに印を付ける。7MB 超のファイルで実機テストをして、New UI で制限がかかるか確かめる。かかる場合は、ファイルを分割するか画像を圧縮する。

### 4. ファイルタイプ

- **制限内容**：読めるのは Word・PowerPoint・PDF と、モダン SharePoint ページ。Excel・OneNote・HTML・Markdown・画像ファイルは一覧にありません。
- **補足（公式記載）**：
  - "SharePoint sites containing the following file types can be used as knowledge sources: Word documents (DOC/DOCX), PowerPoint (PPT/PPTX), PDF files"
  - "Only modern SharePoint pages are supported. However, modern pages containing SPFx components aren't supported."
- **公式URL**：[Quotas and limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas)
- **対処方法**：
  - OneNote はツール（ワークフロー）で読む。
  - 手順や FAQ が Excel にあるものは、Word か PDF に書き直す。
  - HTML・Markdown は PDF に変換する。
  - 画像だけの内容は、文章を補う。
  - 対象外の形式は「公開」フォルダに置かない。

**公式に記載が無いもの**：フォルダ配下のファイル数と、階層の深さの上限です。この2点と New UI への適用可否は、MS への問い合わせに加えるのがよいと思います。