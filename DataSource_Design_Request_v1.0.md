# FAQ Agent 向け データソースの置き方のお願い(v1.0 / 2026-11-24)

SharePoint と OneNote の資料を整理するチーム向けの資料です。
FAQ Agent(利用者の質問に、社内の資料をもとに答える AI)が資料を正しく読めるように、置き方のお願いと、その理由・制限・懸念点をまとめました。フォルダやセクションの名前は仮です。

## 特にお願いしたい 3 点

1. Agent に読ませる場所(SharePoint の「公開」フォルダ、OneNote の Agent 用ノートブック)には、利用者に見せてよい最新の内容だけを置く。
2. ファイル名・見出し・ページのタイトルに、利用者が質問で使う言葉を入れる。
3. 業務フォルダとセクションの名前を変える・増やすときは、事前に連絡する。

---

## 1. Agent の読み方

Agent は、資料を全部読んで覚えているわけではありません。質問のたびに探しに行き、見つかった部分だけをもとに答えます。見つからなければ「記載がありません」と答えます。そのため、置き方と名前の付け方が、答えの質を決めます。

| | SharePoint | OneNote |
|---|---|---|
| 読み方 | 登録したフォルダの中を検索し、質問に近い上位の一部だけを読む | セクションの名前で場所を決め、ページのタイトルで読むページを選ぶ |
| 手がかり | 本文、ファイル名、見出しの言葉 | セクションの名前、ページのタイトル |
| 言い方の違い | 意味の近さでも探せるので、ある程度は吸収される | タイトルの言葉が合わないと見つからない |
| 答えに付く出典 | 資料へのリンク | ページのタイトルとリンク |

---

## 2. SharePoint

### 2.1 構成(仮)

```
ナレッジ統合/
├─ ServiceNow KBA/
│   ├─ 公開/      … Agent が読む
│   └─ 非公開/    … Agent は読まない
├─ 事前相談/
│   ├─ 公開/      … この下のサブフォルダは自由(何階層でもよい)
│   └─ 非公開/
├─ 利用申請/
│   ├─ 公開/
│   └─ 非公開/
└─ コスト請求/
    ├─ 公開/
    └─ 非公開/
```

| 設計 | 理由 |
|---|---|
| 業務ごとにフォルダを分ける | Agent には、業務ごとに1件ずつ登録し、それぞれに説明文を付ける。Agent は説明文を見て、どの業務の資料を探すかを決める |
| 「公開」と「非公開」に分ける | 「公開」の下は、全部が検索の対象になる。読ませるものと読ませないものは、フォルダで分けるのが確実 |
| 「公開」の下は自由 | サブフォルダは、何階層でも検索される。整理しやすい形でよい |

### 2.2 お願いと理由

| # | お願い | 理由 |
|---|---|---|
| 1 | 「公開」には、利用者に見せてよい最新の資料だけを置く。古い版、下書き、作業中のものは「非公開」に置く | 「公開」の下は、サブフォルダも含めて全部が検索の対象になる(5章 #10)。古い版が残っていると、古い内容を答えることがある |
| 2 | 形式は Word、PowerPoint、PDF にする | 対応している形式はこの3種類(5章 #2)。OneNote のファイル、HTML、Markdown は読まれない(テストで確認済み)。Excel は答えが安定しない(5章 #3) |
| 3 | 1ファイル1テーマにする。大きい資料は分けて、7 MB 未満にする | Agent が読むのは、検索で上位に来た一部だけ(5章 #5)。話題が混ざった大きい資料は、必要な部分が選ばれにくい。7 MB 以上は読まれないことがある(5章 #4) |
| 4 | ファイル名と見出しに、利用者が質問で使う言葉を入れる(例: `Firewall申請_手順と締め切り.docx`) | ファイル名と見出しは、検索の手がかりになる。「資料1」「最新版」のような名前では見つけにくい |
| 5 | 更新するときは、同じファイル名で上書きする。ファイル名に日付や版(v2、最新)を付けない | 版の違うファイルが並ぶと、どれが正しいかを Agent が選べない。上書きなら、出典のリンクも変わらない。前の版は、SharePoint のバージョン履歴から戻せる |
| 6 | 大事な内容は文字で書く。画面の写真だけの手順書や、文字を選択できない PDF にしない | 画像の中の文字は、読まれないものとして扱う |
| 7 | 資料の中のリンク先に答えがある場合は、リンク先の資料も「公開」に置く | リンク先は読まれない(5章 #9) |
| 8 | パスワード付きのファイル、暗号化される秘密度ラベルの付いたファイルを「公開」に置かない | 中身を読めず、答えに使われない。エラーも出ない(5章 #7) |
| 9 | 「公開」は、Agent を使う人全員が読める権限にする。人やファイルごとに権限を細かく変えない | Agent は、質問した人が読める資料だけを使う(5章 #6)。権限がばらばらだと、人によって答えが変わる |
| 10 | 「公開」とその上のフォルダの名前を変える・移す・増やすときは、事前に連絡する | Agent への登録は URL で行う。名前を変えると URL が変わり、登録のし直しが要る(5章 #8)。「公開」の下のサブフォルダは、自由に変えてよい |

### 2.3 懸念点

- **業務フォルダの数**: Agent に登録できる URL は 25 件までです(5章 #1)。業務フォルダは増やしすぎず、細かい分類は「公開」の下のサブフォルダで行ってください。
- **秘密度ラベル**: 社内の資料に付いているラベルによっては、読めない可能性があります。どのラベルなら読めるかは、こちらでテストします。「公開」に置く資料に付くラベルの種類を教えてください。
- **反映の遅れ**: 置いた直後や更新した直後は、検索に出るまで時間がかかることがあります。
- **内容の重複**: 同じ内容の資料が複数あると、答えがぶれます。1つにまとめてください。
- **ServiceNow KBA**: 記事を SharePoint に複製する方法は検討中です。置く場合は、1記事1ファイル、ファイル名に KB 番号とタイトルを入れる形(例: `KB0012345_Firewall申請の手順.pdf`)を想定しています。

---

## 3. OneNote

OneNote は、SharePoint の検索では読めません(テストで確認済み)。そのため Agent は、専用の仕組み(ツール)で OneNote を読みます。この仕組みは、セクションの名前とページのタイトルで読む場所を決めるので、名前の付け方が特に大事です。

### 3.1 構成(仮)

```
Agent 用のノートブック(1つ)
├─ 事前相談          … セクション。名前に業務の名前を入れる
│   ├─ ページ        … タイトルに、質問で使う言葉を入れる
│   └─ ページ
├─ 事前相談_FAQ      … 同じ業務に、セクションを複数作ってもよい
├─ 利用申請
└─ コスト請求
```

Agent の読み方は、次の順です。

```
ノートブックの全セクション
 → 名前に業務の名前を含むセクションだけ
   → そのページの一覧
     → タイトルに質問の言葉を含むページだけ、本文を読む
```

### 3.2 お願いと理由

| # | お願い | 理由 |
|---|---|---|
| 1 | Agent に読ませるページは、1つのノートブックにまとめる | ツールは、決めた1つのノートブックだけを読む |
| 2 | Agent に読ませたくない内容は、別のノートブックか、業務の名前を含まないセクション(例:「作業用」)に置く | OneNote には「公開」「非公開」の区別が無い。名前に業務の名前を含むセクションは、全部が読む対象になる |
| 3 | セクションの名前に、業務の名前(事前相談、利用申請、コスト請求)を入れる。SharePoint のフォルダ名と同じ言葉にする | ツールは、名前に業務の名前を含むセクションだけを読む。含まないセクションは読まれない |
| 4 | セクションは、ノートブックの直下に作る。セクション グループは使わない | グループの中のセクションは、読めない見込み(5章 #13) |
| 5 | ページのタイトルは、中身が分かる具体的な言葉にする。略語と正式な名前の両方を入れる(例:「FW(Firewall)申請の締め切り」)。「メモ」「その他」や、日付だけのタイトルにしない | ツールは、タイトルに質問の言葉を含むページだけを読む。タイトルに無い言葉では見つからない |
| 6 | サブページのタイトルも、それだけで中身が分かるようにする(親「Firewall」・子「申請手順」ではなく、子も「Firewall 申請手順」) | サブページも1つのページとして、タイトルで選ばれる。親のタイトルは見られない |
| 7 | 1ページ1テーマにし、長くしすぎない | 選ばれたページは、全文が Agent に渡る。長いと、遅くなり、費用が増え、答えがぼやける |
| 8 | 大事な内容は文字で書く。画像、手書き、添付ファイルの中身に頼らない | ツールが取り出すのは、ページの文字だけ |
| 9 | 1つのセクションは、500 ページ以内を目安にする。増えてきたら分ける | 読み込みに、時間の制限(5章 #11)と回数の制限(5章 #12)がある |
| 10 | セクションにパスワードを付けない | パスワード付きのセクションは、読めない可能性が高い(未確認) |
| 11 | ノートブックは、Agent を使う人全員が開ける権限にする | ツールは、質問した人の権限で読む。開けない人は、OneNote の内容をもとにした答えをもらえない |
| 12 | セクションの名前を変える・増やすときは、事前に連絡する | 名前から業務の名前が消えると、読まれなくなる |

### 3.3 懸念点

- **言い方の違いに弱い**: OneNote は、タイトルの言葉が合わないと見つかりません。よく聞かれる内容は、SharePoint に Word か PDF で置く方が見つかりやすくなります。
- **時間と費用**: OneNote は、読むたびに時間と費用がかかります(テストでは、20 ページを読むのに約 23 秒)。
- **ノートブックを新しく作る場合**: 保存先のファイル数が非常に多いと、読めないことがあります(5章 #14)。ファイル数の少ない場所に作り、作ったら連絡してください。こちらで読めるかをテストします。
- **既存のノートブックを使う場合**: 名前に業務の名前が入っていないセクションは読まれません。セクションの名前の付け直しが必要です。

---

## 4. 共通のお願い

- **業務の名前をそろえる**: SharePoint のフォルダ名、OneNote のセクション名、Agent の設定で、同じ言葉を使います。変える・増やすときは事前に連絡してください(Agent の設定も直すため)。
- **同じ内容を2か所に置かない**: SharePoint と OneNote の両方に同じ内容があると、片方だけ更新されて食い違います。どちらかに決めてください。
- **言葉をそろえる**: 同じものを指す言葉(Firewall、ファイアウォール、FW など)をそろえます。そろえられないときは、タイトルや見出しに両方を書いてください。
- **運用が始まった後**: Agent が答えられなかった質問は記録し、定期的に分析します。その結果をもとに、資料の追加やタイトルの見直しを相談することがあります。

どちらに置くかの目安

| 置くもの | 置き場所 |
|---|---|
| まとまった手順書、FAQ、よく聞かれる内容 | SharePoint(Word、PDF) |
| 日々書き足すメモ、ノウハウ | OneNote |
| 迷ったとき | SharePoint |

---

## 5. 制限の一覧(公式の記載)

| # | 項目 | 公式の記載(英語のまま) | URL |
|---|---|---|---|
| 1 | 登録できる SharePoint の URL の数 | Each agent can have a maximum of 25 SharePoint site URLs when the agent is using generative orchestration. | [1] |
| 2 | 対応している形式 | SharePoint sites containing the following file types can be used as knowledge sources: Word documents (DOC/DOCX), PowerPoint (PPT/PPTX), PDF files | [1] |
| 3 | Excel | While you can add structured files, such as XLSX files from SharePoint, agents can't write and run code. Responses to analytical questions might not be optimal. | [1] |
| 4 | ファイルのサイズ | For makers without the Microsoft 365 Copilot license in the same tenant as their agent, … generative answers can only use SharePoint files that are under 7 MB. | [1] |
| 5 | 読む量 | When Copilot Studio searches SharePoint, it uses only the top three search results to summarize and generate a response. | [2] |
| 6 | 権限 | At a minimum, a user must have read permissions on the relevant sites and files, or no search results are returned. | [2] |
| 7 | 暗号化、パスワード | the agent can't extract or ground on content whose protection encrypts the file. This limitation includes sensitivity labels that apply encryption, Double Key Encryption (DKE), and password-protected files. | [2] |
| 8 | フォルダ名の変更 | If you rename a SharePoint site or folder that an agent-level knowledge source uses, the existing source link can break and cause a permission gap. | [2] |
| 9 | 資料の中のリンク | Hyperlinks contained inside a registered document or page aren't crawled or followed. | [3] |
| 10 | 検索の範囲 | The agent searches only the folder or site URL you register, and its subfolders. | [3] |
| 11 | OneNote の読み込みの時間 | Respond to the agent within the 100-second action limit. | [4] |
| 12 | OneNote の読み込みの回数 | API calls per connection: 100 calls / Renewal period: 60 seconds | [5] |
| 13 | OneNote のセクション グループ | (アクションの一覧に、セクション グループを読む操作が無い) | [5] |
| 14 | OneNote の保存先 | One or more of the document libraries on the user or group's OneDrive contains more than 20,000 items and cannot be indexed for querying using the API. | [6] |

#1〜#10 は、Copilot Studio の従来の画面向けの公式ページの記載です。今使っている新しい画面(New experience)にも同じように当てはまるかは、Microsoft に確認中です。

- [1] https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas
- [2] https://learn.microsoft.com/en-us/troubleshoot/power-platform/copilot-studio/knowledge/sharepoint-no-response
- [3] https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint
- [4] https://learn.microsoft.com/en-us/microsoft-copilot-studio/workflows-experience/flow-agent
- [5] https://learn.microsoft.com/en-us/connectors/onenote/
- [6] https://learn.microsoft.com/en-us/graph/onenote-error-codes

---

## 6. 決まっていないこと

| 項目 | 状況 |
|---|---|
| フォルダとセクションの名前 | 仮。決まったら連絡してほしい |
| 使うノートブック | 既存のものを使うか、新しく作るか |
| ServiceNow KBA を SharePoint に複製する方法 | 検討中 |
| 秘密度ラベルの付いた資料 | どのラベルなら読めるかを、こちらでテストする |
| 制限が新しい画面にも当てはまるか | Microsoft に確認中 |

---

## 7. 資料を置く前のチェック

SharePoint

- [ ] Word、PowerPoint、PDF のどれかになっている
- [ ] 7 MB 未満になっている
- [ ] 1ファイル1テーマになっている
- [ ] ファイル名と見出しに、質問で使う言葉が入っている
- [ ] 同じ内容の古い版が「公開」に残っていない
- [ ] パスワードや暗号化が付いていない
- [ ] 利用者に見せてよい内容になっている

OneNote

- [ ] セクションの名前に、業務の名前が入っている
- [ ] ページのタイトルだけで、中身が分かる(サブページも)
- [ ] 大事な内容が、文字で書かれている
- [ ] 同じ内容が SharePoint に無い
