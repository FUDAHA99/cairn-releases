# Privacy Policy · Cairn

**Effective date: 2026-07-02**
**Last updated: 2026-09-06**

---

## English

### 1. Who we are
Cairn ("we", "us") is a mobile app for learning academic English (the Academic Word List). This policy explains what data the app collects, why, where it goes, and how you can control it.

Cairn has **no accounts**. You never give us your name, email, phone number, or any login.

### 2. Data we collect

**Data stored only on your device** (not sent to us):
- Your onboarding choices (goal, level, daily minutes, interests, optional display name)
- Vocabulary study progress (which words you know / are unsure about / don't know)
- Quiz answers and mistake notebook
- Listening / reading / grammar answer history and study plan
- AI chat conversation history within the app
- Speaking-practice recordings (the "read-aloud" module; held only in the app's local cache, never uploaded)
- Audio the app has synthesized for you (cached locally so it is not downloaded twice)

**Anonymous usage analytics** (sent automatically on every cold start, no action needed):
- We use **PostHog** (US region) to count how the app is used. Events are relayed through our own Cloudflare Worker; the app never talks to PostHog directly.
- Exactly five event types are reported: `app_open`, `onboarding_done`, `unit_selected`, `module_start`, `module_complete`.
- Each event carries a few properties (module name, unit number, correct / total answers, whether a study plan exists, onboarding goal / level / minutes / number of interests) plus the **app version** and an **anonymous install ID**.
- The anonymous install ID is a random string generated locally on first launch. It is **not** a hardware ID, advertising ID, or account. Deleting local data (Section 5) discards it and a new one is generated.
- Nothing you type — no display name, no chat text, no free text — is included in analytics.

**Update check** (once per cold start, no action needed): the app asks our Cloudflare Worker for the latest version number and a download link, so it can show an "update available" notice on the home screen. The request carries only the anonymous install ID and the request-signing headers (no body); the Worker keeps no record of it beyond the short-lived request logs described in Section 5.

**Data sent to our backend when you use specific features:**
- **AI Speaking Coach — text**: The messages you type (or that were transcribed from your voice) and the conversation history for the current topic are sent to our Cloudflare Worker, which generates the reply with **Cloudflare Workers AI** (Qwen3-30B-A3B, running on Cloudflare's network). The request carries the anonymous install ID (used for rate limiting) but no display name or other identifier. Nothing is sent to any other AI vendor.
- **AI Speaking Coach — voice input**: If you tap the microphone in the AI coach, your recording is uploaded to our Cloudflare Worker and transcribed by **Cloudflare Workers AI (Whisper)**. The recording is discarded after transcription; only the resulting text continues into the chat flow above. The app shows a one-time notice and asks for your consent before the first upload.
- **Text-to-speech**: Vocabulary pronunciations, listening passages and the reference sentences in speaking practice are all **bundled MP3 files that play offline** — no network request, nothing sent to us. Only AI-coach replies are read aloud by **Cloudflare Workers AI (Deepgram Aura-1)**, and only when you tap the speaker on a reply (or switch on *Profile → Auto-read AI replies*): the reply text is sent to our Worker and the returned audio is cached on your device.

**Data we do NOT collect**:
- Your name, email, phone number, or any account information
- Advertising identifiers, hardware IDs, or device fingerprints
- Location
- Contacts, calendar, photos, or other files
- Crash reports or diagnostics (no crash-reporting SDK is integrated)

### 3. Permissions
- **Microphone (RECORD_AUDIO)**: Used by the speaking-practice module (recording stays on device) and by voice input in the AI coach (recording is uploaded for transcription, with your consent, see Section 2).
- **Network**: Used for analytics, the update check, the AI coach, voice transcription, and cloud text-to-speech. Vocabulary study, quizzes, reading, and grammar work offline.

### 4. Children under 13
Cairn is not directed at children under 13. We do not knowingly collect data from children under 13.

### 5. Data retention and deletion
- **On your device**: Local data stays until you tap **Profile → "Clear all local data"** (deletes study progress, mistake notebook, chat history, and the anonymous install ID) or uninstall the app.
- **On our backend**: We keep no account data. Our Worker holds request data only for as long as needed to serve the request. Cloudflare Workers Logs is enabled and records error messages and request metadata (timestamp, route, status code, IP address); it **does not log chat text or audio**. Logs are retained for 3–7 days depending on the Cloudflare plan.
- **Analytics**: PostHog events are keyed only by the anonymous install ID. Once you clear local data, nothing links new events to old ones. To request deletion of events tied to a specific ID, email us (Section 10).

### 6. Security
All traffic between the app and our backend uses HTTPS/TLS. The app holds no AI provider API keys; all upstream calls are made by our Worker, which applies request signing, per-device rate limits, and daily quotas to limit abuse.

### 7. International data transfer
Our backend and the services below run outside mainland China (Cloudflare's global network and PostHog in the United States). By using the analytics, AI coach, voice, and cloud text-to-speech features, you consent to your data being processed in those locations.

### 8. Third-party services
- **Cloudflare** (Workers hosting; Workers AI for the AI coach's replies, speech-to-text and text-to-speech; Workers Logs) — https://www.cloudflare.com/privacypolicy/

  Every AI feature now runs on Cloudflare. (This changed on the server side on 2026-09-04 and applies to all app versions immediately.) The backend can be configured to use an external OpenAI-compatible provider instead; if we ever do that, this section will be updated first.
- **PostHog** (anonymous product analytics, US region) — https://posthog.com/privacy

Fonts are bundled with the app; no font or other asset is fetched from Google or any other network service.

### 9. Changes to this policy
We will update the "Last updated" date above and, for material changes, prompt you inside the app.

### 10. Contact
Email: cairn.app.support@gmail.com

---

## 简体中文

### 1. 我们是谁
Cairn（下称"我们"）是一款学术英语（AWL 学术词表）学习 App。本政策说明本应用会收集哪些数据、为什么收集、数据去了哪里，以及你如何控制。

Cairn **没有账号系统**。你无需提供姓名、邮箱、手机号或任何登录信息。

### 2. 我们收集的数据

**仅存储在你设备上的数据**（不会发送给我们）：
- 引导流程中你的选择（备考目标、水平、每日时长、兴趣场景、可选的昵称）
- 单词学习进度（哪些词你已认识 / 模糊 / 不认识）
- 测验答题记录与错题本
- 听力 / 阅读 / 语法的答题历史与学习计划
- App 内 AI 对话历史
- 口语跟读模块的录音（只存在 App 本地缓存，不上传）
- App 为你合成过的朗读音频（缓存在本机，避免重复下载）

**匿名使用统计**（每次冷启动自动上报，无需你操作）：
- 我们使用 **PostHog**（美国区）统计 App 的使用情况。事件经我们自己的 Cloudflare Worker 转发，App 不直接连接 PostHog。
- 只上报 5 种事件：`app_open`、`onboarding_done`、`unit_selected`、`module_start`、`module_complete`。
- 每个事件附带少量属性（模块名、单元号、答对数 / 总题数、是否有学习计划、引导时选的目标 / 水平 / 时长 / 兴趣数量），以及 **App 版本号** 和一个 **匿名安装 ID**。
- 匿名安装 ID 是首次启动时在本地随机生成的字符串，**不是**硬件 ID、广告 ID 或账号。清除本地数据（第 5 节）会一并删除它，下次启动重新生成。
- 你输入的任何内容——昵称、对话文字、自由文本——都不会进入统计。

**更新检查**（每次冷启动自动进行一次，无需你操作）：App 向我们的 Cloudflare Worker 询问最新版本号和下载链接，以便在首页提示「有新版本」。这个请求只带匿名安装 ID 和请求签名头（没有请求体）；Worker 除第 5 节所述的短期请求日志外不保留任何记录。

**使用特定功能时发送到我们后端的数据：**
- **AI 口语陪练 · 文字**：你输入（或由语音转写得到）的文字，连同当前话题的对话历史，发送到我们的 Cloudflare Worker，由 **Cloudflare Workers AI**（跑在 Cloudflare 网络上的 Qwen3-30B-A3B 模型）生成回复。请求附带匿名安装 ID（用于限流），不附带昵称或其他标识。不会发送给任何其他 AI 厂商。
- **AI 口语陪练 · 语音输入**：在 AI 陪练里点击麦克风时，你的录音会上传到我们的 Cloudflare Worker，由 **Cloudflare Workers AI（Whisper）** 转写成文字。转写完成后不保留录音，只有转写出的文字进入上面的对话流程。首次上传前 App 会弹窗告知并征得你的同意。
- **朗读**：词汇发音、听力原文、跟读标准句都是**打包在 App 里的 MP3，离线播放** —— 不联网，也不会有任何内容发给我们。只有 AI 陪练的回复由 **Cloudflare Workers AI（Deepgram Aura-1）** 朗读，且仅在你点了回复旁的喇叭（或在「我的 → 自动朗读 AI 回复」里打开开关）时才会发生：回复文本发送到我们的 Worker，返回的音频缓存在你的设备上。

**我们不会收集的数据**：
- 你的姓名、邮箱、电话或任何账号信息
- 广告 ID、硬件 ID 或设备指纹
- 位置信息
- 通讯录、日历、照片或任何其他文件
- 崩溃报告或诊断数据（未集成任何崩溃收集 SDK）

### 3. 权限说明
- **麦克风（RECORD_AUDIO）**：用于口语跟读模块（录音只在本地）和 AI 陪练的语音输入（录音在你同意后上传转写，见第 2 节）。
- **网络**：用于使用统计、更新检查、AI 陪练、语音转写和云端朗读。单词学习、测验、阅读、语法可离线使用。

### 4. 13 岁以下儿童
Cairn 不面向 13 岁以下儿童，且不会明知故意地收集儿童数据。

### 5. 数据保留与删除
- **你的设备上**：本地数据一直保留，直到你点击 **我的 → 「清除全部本地数据」**（删除学习进度、错题本、对话记录和匿名安装 ID）或卸载 App。
- **我们的后端**：不保存任何账号数据。Worker 只在处理请求期间持有请求数据。我们开启了 Cloudflare Workers Logs，记录错误信息与请求元数据（时间、路由、状态码、IP 地址），**不记录对话正文与音频**；日志保留期按 Cloudflare 计划为 3–7 天。
- **统计数据**：PostHog 事件只以匿名安装 ID 关联。清除本地数据后，新事件与旧事件之间不再有任何关联。如需删除与某个 ID 关联的事件，请通过第 10 节的邮箱联系我们。

### 6. 安全
App 与后端之间的所有通信使用 HTTPS/TLS。App 内不持有任何 AI 服务商的 API 密钥，所有上游调用由我们的 Worker 发起，并通过请求签名、按设备限流和每日配额限制滥用。

### 7. 跨境传输
我们的后端及下列服务均位于中国大陆境外（Cloudflare 全球网络、PostHog 美国）。使用统计、AI 陪练、语音和云端朗读功能即表示你同意数据在上述地点处理。

### 8. 第三方服务
- **Cloudflare**（Workers 托管；Workers AI 负责 AI 陪练的回复生成、语音识别与语音合成；Workers Logs）— https://www.cloudflare.com/privacypolicy/

  全部 AI 能力现在都跑在 Cloudflare 上。（2026-09-04 在服务端切换，对所有版本的 App 立即生效。）后端也可以配置成使用外部的 OpenAI 兼容服务商；若将来这么做，会先更新本节。
- **PostHog**（匿名产品统计，美国区）— https://posthog.com/privacy

字体随 App 打包，不从 Google 或其他网络服务加载任何字体或资源。

### 9. 政策更新
我们会更新顶部"最后更新"日期；如涉及重大变更，会在 App 内提示。

### 10. 联系我们
邮箱：cairn.app.support@gmail.com
