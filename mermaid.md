'''mermaid 
flowchart TB
  U["利用者 (CMS/CI)<br/>Teams"]
  OPS["ナレッジ運用チーム"]

  subgraph CS["Copilot Studio (New experience)"]
    FAQ["<b>FAQ Agent</b><br/>スキル: answer-format / inquiry-log"]
    IMP["<b>ナレッジ改善 Agent</b><br/>スキル: log-analysis"]
    T1["ツール<br/>OneNote_ページ取得"]
    T2["ツール<br/>問い合わせログ_記録"]
    T3["ツール<br/>問い合わせログ_取得"]
  end

  subgraph DATA["データソース"]
    SPO[("SharePoint ナレッジ公開<br/>事前相談 / 利用申請 / 共通 / Eng")]
    ON[("OneNote<br/>業務カテゴリ別セクション")]
    LOG[("SharePoint List<br/>問い合わせログ")]
  end

  U -->|"1. 質問"| FAQ
  FAQ -->|"5. 根拠リンク付きの回答"| U
  FAQ -->|"2. ナレッジ検索"| SPO
  FAQ -->|"3. 足りないときだけ"| T1
  T1 -->|"セクションを読む"| ON
  FAQ -->|"4. 回答ごとに1回"| T2
  T2 -->|"1行追加"| LOG

  OPS -->|"期間を指定"| IMP
  IMP --> T3
  T3 -->|"ログを読む"| LOG
  IMP -->|"改善の提案<br/>(不足 / 修正 / 重複)"| OPS
  OPS -.->|"人が確認して修正"| SPO
  OPS -.->|"人が確認して修正"| ON

  classDef agent fill:#e8f5e9,stroke:#2e7d32,color:#1b5e20;
  classDef tool fill:#e3f2fd,stroke:#1565c0,color:#0d47a1;
  classDef data fill:#fff8e1,stroke:#b8860b,color:#5d4200;
  classDef person fill:#f3e5f5,stroke:#6a1b9a,color:#4a148c;
  class FAQ,IMP agent;
  class T1,T2,T3 tool;
  class SPO,ON,LOG data;
  class U,OPS person;
'''