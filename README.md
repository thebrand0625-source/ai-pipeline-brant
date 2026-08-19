# video-pipeline-marketplace

這是 `video-pipeline` plugin 的 marketplace 倉庫。透過 marketplace 安裝,之後也方便在同一個倉庫底下擴充更多 plugin。

## 安裝方式

在 Claude Code 中新增這個 marketplace(以本機路徑或 git remote 為例):

```
/plugin marketplace add /path/to/video-pipeline
```

或使用已發布的 git 位址:

```
/plugin marketplace add <git-url>
```

新增後,安裝其中的 plugin:

```
/plugin install video-pipeline@video-pipeline-marketplace
```

## 目錄結構

```
video-pipeline/                        # marketplace 倉庫根目錄
├── .claude-plugin/
│   └── marketplace.json               # marketplace 清單
├── plugins/
│   └── video-pipeline/                # plugin 本體
│       ├── .claude-plugin/plugin.json
│       ├── skills/
│       ├── reference/
│       └── README.md                  # plugin 說明(原本的 README)
├── scripts/                           # 實際製作產出(非 plugin 內容)
└── CLAUDE.md                          # 專案說明
```

Plugin 本身的用法與四階段流程說明,請見 `plugins/video-pipeline/README.md`。
