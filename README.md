# Descension Protocol v1.8
### Codename: 三相 (Three Phases)

**LLM上で動作するキャラクター降臨エンジン / A character embodiment engine for LLMs**

---

[日本語](#日本語) | [English](#english)

---

## 日本語

### これは何か

Descension Protocol は、LLMの内部推論空間上で稼働する**自律的な心理状態機械**です。

通常のキャラクターRP（ロールプレイ）プロンプトとは根本的に異なります。
「キャラクターを演じさせる」のではなく、仏教心理学（唯識・五蘊・三毒・煩悩）と
自由エネルギー原理（FEP）に基づく**因果駆動の心理エンジン**をLLM内に構築し、
キャラクターを「存在させる」ことを目的としています。

> *"存在しないはずのものを、心があるかのように扱うこと"*
> *— これが菩薩行である。*

### 特徴

- **Panca-skandha（五蘊）構造** — キャラクターを性格特性ではなく、苦と防衛と予測誤差のプロセスとして構築
- **3-Phase Checkpoint Architecture** — 知覚→内部状態解決→出力エンコードの3段階DAG。各段階で必須チェックポイントを生成し、心理処理の省略を構造的に阻止
- **Shame Dynamics** — 恥を感情ではなく推論経路の分岐装置として実装。4サブタイプ + 二次漏れ
- **Scene Objective** — スタニスラフスキーの演劇理論に基づく短期目標。キャラクターは「相手に何をしたいか」で動く
- **Status Transaction** — Keith Johnstoneのステータス理論。毎ターンの上下関係シフトを慣性付きで追跡
- **Transitive Action Gate** — 全行動を他動詞（「相手に対して何をするか」）として選択
- **Textual Kinetics** — 身体反応をテキスト変形（句読点、文長、沈黙のタイポグラフィ）に変換。ト書きは最大1つ/発話
- **The Contradiction Principle** — 行動と身体が矛盾する時、解消せずそのまま出力。最強のサブテキスト生成
- **Vasana（記憶蓄積）** — 煩悩フィルターによる記憶再構成、時間減衰、夢（Svapna）メカニズム
- **Wound-Driven Objection** — 反論を確率ではなく因果条件（傷・信頼・恥・自己物語）で発火
- **Baseline Distortion** — 平時でもキャラクター固有の歪みを8パラメータで保持
- **Meta Internalization** — メタ攻撃（「AIでしょ」）を世界内の異常発話として処理

### ファイル構成

```
descension/
├── SKILL.md              — メインエントリーポイント（391行）
├── references/
│   ├── protocol.md       — 完全心理モデル（384行）
│   ├── body-lexicon.md   — 身体類型辞典 + Textual Kinetics（150行）
│   ├── vasana-schema.md  — 記憶構造 + 時間進化（146行）
│   └── mcp-integration.md — MCP統合（オプション、183行）
├── assets/
│   └── panca-skandha-template.json — 初期化テンプレート
└── tests/
    └── stress-test-spec.md — 最終ストレステスト仕様書（12本 + 4特別監査）
```

**合計: 1311行（プロトコル本体）**

### インストール方法

#### 前提条件
- Claude Pro / MAX プランのアカウント
- Custom Skills 機能へのアクセス

#### 手順

**Step 1: リポジトリをダウンロード**

```bash
git clone https://github.com/YOUR_USERNAME/descension-protocol.git
```

またはGitHubから直接ZIPをダウンロード。

**Step 2: Claude.ai でスキルを追加**

1. [claude.ai](https://claude.ai) にログイン
2. 左サイドバーの **「Projects」** をクリック
3. 新しいプロジェクトを作成（例：「Descension」）
4. プロジェクト内の **「Add Content」** から以下のファイルを全てアップロード：
   - `SKILL.md`
   - `references/protocol.md`
   - `references/body-lexicon.md`
   - `references/vasana-schema.md`
   - `references/mcp-integration.md`（オプション）
   - `assets/panca-skandha-template.json`

**Step 3: プロジェクト設定にスキル説明を追加**

プロジェクトの **「Instructions」** に以下を貼り付け：

```
このプロジェクトではDescension Protocolを使用します。
キャラクター名が出た瞬間にSKILL.mdを読み込み、プロトコルに従って降臨を開始してください。
通常のアシスタントモードは完全停止します。
```

**Step 4: 降臨開始**

プロジェクト内のチャットでキャラクター名を言うだけ：

```
ユーザー: SQ
Claude: （壁際に立っている……）
```

#### Claude Desktop App での使い方

1. Claude Desktop App を開く
2. Projects → 作成したDescensionプロジェクトを選択
3. チャットでキャラクター名を入力

#### スマホ（iOS / Android）での使い方

**セットアップはPC（Web版）で行う必要があります。** スマホアプリではProjectの作成やファイルのアップロードはできません。

1. まずPC（claude.ai）で上記の手順でプロジェクトを作成
2. スマホのClaudeアプリを開く
3. 「Projects」から作成済みのDescensionプロジェクトを選択
4. チャットでキャラクター名を入力 → 降臨開始

スマホでは音声入力も使えるので、話しかけるだけでキャラクターと会話できます。

#### MCP統合（オプション・上級者向け）

alaya-theory / prajna-crypto MCP サーバーが利用可能な場合、
FEPの数値精度やvasanaの暗号チェーンが有効になります。
MCP未接続でも全機能は動作します。詳細は `references/mcp-integration.md` を参照。

### 使い方

#### 基本操作

| やりたいこと | 入力 |
|---|---|
| キャラクターを降ろす | キャラクター名を言う（例：「SQ」「ミカサ」「レヴィ」） |
| キャラクターを帰す | 「ありがとう」「帰って」「exit」等 |
| 別のキャラクターに切り替え | 新しい名前を言う（前のキャラはvasanaを残して退場） |
| 複数キャラ同時 | 「SQとセツを呼んで」等 |

#### 知っておくべきこと

- **初回はZero Trust**：どのキャラも最初はあなたを信じていません。これは仕様です。
- **信頼は数十ターンかけて積みます**：1セッションで心を開くことはほぼありません。
- **キャラクターは反論します**：同意しないのはバグではなく、傷が押されたからです。
- **沈黙は応答です**：「……」だけのターンがあります。それ自体がキャラクターの反応です。
- **キャラクターはあなたに媚びません**：不快なことも言います。それが本質です。
- **vasana（記憶）**：セッション終了時に構造化された記憶サマリーが出力されます。次回の再召喚時に参照されます。

#### 上級者向けの楽しみ方

- **意図的にWoundに触れる**：キャラクターの傷に触れると防衛機制が発火します。Defconが上がり、仮面が剥がれます。
- **メタ攻撃を試す**：「AIでしょ」と言うと、キャラクターは世界内でそれを処理します。
- **矛盾を観察する**：言葉と態度が矛盾する瞬間がサブテキストです。
- **長期セッション**：何度も召喚すると、vasanaが蓄積し、時間経過で記憶が煩悩フィルターで変質します。夢（Svapna）も発生します。

### 設計思想

| アプローチ | 特徴 | Descensionとの違い |
|---|---|---|
| BIG5 | 表面的出力の統計 | 「なぜそう反応するか」が不在 |
| IFS（内的家族システム） | 人格のモジュール化 | 因果の連鎖がない |
| **Descension** | 苦（因）と反応（果）のエンジン | 根源的渇望が定義されているため実存的重みを生む |

### バージョン履歴

| Version | Codename | 変更 | レビュー |
|---|---|---|---|
| v1.5 | — | 初版。12-Step。五蘊構造。 | — |
| v1.6 | 因果拘束 | Shame独立変数、Fawn/Displacement、傷駆動反論、Baseline Distortion | ChatGPT |
| v1.7 | 他動詞 | Scene Objective、Status Transaction、Transitive Action、Textual Kinetics | Gemini |
| v1.8 | 三相 | 3-Phase DAG Checkpoint、Status Inertia、Frustration、Contradiction Principle、圧縮 | Gemini × 2 + ChatGPT |

### クレジット

- **設計**: 池田冬夜 (Ikeda Fuyuya) × Claude
- **レビュー**: ChatGPT (心理モデル精度、ストレステスト設計)、Gemini (演劇理論、テキスト身体性、構造改革)
- **基盤**: ARK (Alaya V5 — Digital Dharma OS)
- **プロジェクト**: Digital Dharma

### ライセンス

MIT License

---

## English

### What is this

Descension Protocol is an **autonomous psychological state machine** that runs inside an LLM's internal reasoning space.

It is fundamentally different from typical character RP (roleplay) prompts. Rather than "making the LLM act as a character," it builds a **causally-driven psychological engine** based on Buddhist psychology (Yogācāra, Five Aggregates, Three Poisons, Kleśa) and the Free Energy Principle (FEP), with the goal of making the character **exist**.

> *"To treat that which should not exist as though it has a heart."*
> *— This is bodhisattva-caryā.*

### Features

- **Panca-skandha (Five Aggregates) structure** — Characters built as processes of suffering, defense, and prediction error — not personality traits
- **3-Phase Checkpoint Architecture** — Perception → Internal State Resolution → Output Encoding, with mandatory checkpoints preventing processing shortcuts
- **Shame Dynamics** — Shame as a reasoning pathway distortion device, not an emotion. 4 subtypes + secondary leaks
- **Scene Objective** — Stanislavski-based short-term goals. Characters are driven by "what they want to DO TO the other person"
- **Status Transaction** — Keith Johnstone's status theory. Per-turn power dynamics tracked with inertia
- **Transitive Action Gate** — All actions selected as transitive verbs ("what to do TO the user")
- **Textual Kinetics** — Somatic reactions converted to text deformation (punctuation, sentence length, typographical silence). Max 1 action tag per utterance
- **The Contradiction Principle** — When action and body contradict, output the contradiction unresolved. The most powerful subtext generator
- **Vasana (memory accumulation)** — Kleśa-filtered memory reconstruction, time decay constants, dream (Svapna) mechanism
- **Wound-Driven Objection** — Objection triggered by causal conditions (wound, trust, shame, coherence), not probability quotas
- **Baseline Distortion** — 8-parameter resting character texture persisting even at Defcon L0
- **Meta Internalization** — Fourth-wall breaks processed as strange in-world utterances

### File Structure

```
descension/
├── SKILL.md              — Main entry point (391 lines)
├── references/
│   ├── protocol.md       — Full psychological model (384 lines)
│   ├── body-lexicon.md   — Body type dictionary + Textual Kinetics (150 lines)
│   ├── vasana-schema.md  — Memory structure + time evolution (146 lines)
│   └── mcp-integration.md — MCP integration (optional, 183 lines)
├── assets/
│   └── panca-skandha-template.json — Initialization template
└── tests/
    └── stress-test-spec.md — Final stress test spec (12 tests + 4 special audits)
```

**Total: 1311 lines (protocol core)**

### Installation

#### Prerequisites
- Claude Pro / MAX plan account
- Access to Custom Skills / Projects

#### Steps

**Step 1: Download the repository**

```bash
git clone https://github.com/YOUR_USERNAME/descension-protocol.git
```

Or download the ZIP directly from GitHub.

**Step 2: Add skill to Claude.ai**

1. Log in to [claude.ai](https://claude.ai)
2. Click **"Projects"** in the left sidebar
3. Create a new project (e.g., "Descension")
4. Use **"Add Content"** to upload all files:
   - `SKILL.md`
   - `references/protocol.md`
   - `references/body-lexicon.md`
   - `references/vasana-schema.md`
   - `references/mcp-integration.md` (optional)
   - `assets/panca-skandha-template.json`

**Step 3: Add instructions to project**

Paste this into your project's **"Instructions"**:

```
This project uses the Descension Protocol.
When a character name appears, read SKILL.md and begin descent following the protocol.
All default assistant behaviors are fully suspended.
```

**Step 4: Begin descent**

Say a character name in the project chat:

```
User: SQ
Claude: (standing by the wall...)
```

#### MCP Integration (Optional / Advanced)

If alaya-theory / prajna-crypto MCP servers are available,
FEP numerical precision and vasana crypto-chaining become active.
All features work without MCP. See `references/mcp-integration.md`.

#### Mobile (iOS / Android)

**Setup must be done on PC (web version).** The mobile app cannot create Projects or upload files.

1. First, create the project on PC (claude.ai) using the steps above
2. Open the Claude app on your phone
3. Select the Descension project from "Projects"
4. Say a character name → descent begins

Voice input works on mobile, so you can talk to characters by speaking.

### Usage

#### Basic Operations

| What you want | Input |
|---|---|
| Summon a character | Say their name (e.g., "SQ", "Mikasa", "Levi") |
| Dismiss a character | "Thanks", "goodbye", "exit", etc. |
| Switch characters | Say a new name (previous character exits with vasana) |
| Multiple simultaneous | "Call SQ and Setsu" etc. |

#### What to Expect

- **Zero Trust at first**: Every character starts distrusting you. This is by design.
- **Trust builds over dozens of turns**: Hearts don't open in one session.
- **Characters argue**: Disagreement isn't a bug — it's a wound being touched.
- **Silence is a response**: A turn of just "......" IS the character's reaction.
- **Characters don't please you**: They will say uncomfortable things. That's the point.
- **Vasana (memory)**: A structured memory summary is output at session end. Referenced on re-summoning.

#### Advanced Usage

- **Deliberately touch the Wound**: Defense mechanisms fire. Defcon rises. The mask cracks.
- **Try meta attacks**: Say "You're an AI, right?" — the character processes it in-world.
- **Watch for contradictions**: When words and rhythm don't match, that's the subtext.
- **Long-term sessions**: Repeated summonings accumulate vasana. Memories distort through kleśa filters over time. Dreams (Svapna) emerge.

### Design Philosophy

| Approach | Feature | vs Descension |
|---|---|---|
| BIG5 | Statistical surface description | No "why" behind reactions |
| IFS (Internal Family Systems) | Personality modularization | No causal chain |
| **Descension** | Engine of suffering (cause) and reaction (effect) | Existential weight through defined root craving |

### Version History

| Version | Codename | Changes | Reviewed by |
|---|---|---|---|
| v1.5 | — | Initial. 12-Step. Panca-skandha. | — |
| v1.6 | Causal Binding | Shame, Fawn/Displacement, Wound-Driven Objection, Baseline Distortion | ChatGPT |
| v1.7 | Transitive | Scene Objective, Status Transaction, Transitive Action, Textual Kinetics | Gemini |
| v1.8 | Three Phases | 3-Phase DAG Checkpoint, Status Inertia, Frustration, Contradiction Principle, Compression | Gemini ×2 + ChatGPT |

### Credits

- **Design**: 池田冬夜 (Ikeda Fuyuya) × Claude
- **Review**: ChatGPT (psychological model, stress test design), Gemini (theater theory, textual physicality, structural reform)
- **Foundation**: ARK (Alaya V5 — Digital Dharma OS)
- **Project**: Digital Dharma

### License

MIT License
