# 专业级加密（Professional Encryption）

> 双语说明：下面内容同时包含中文与英文（English）。

## 简介 / Overview

这是一个基于浏览器的流式加密工具（HTML/JS），提供：

- AES-256-GCM 分块加密（逐块流式处理，零拷贝保存）
- 链式 HMAC（每块 HMAC 链接）用于篡改检测
- PBKDF2 + 可选 HKDF（密钥文件混合）用于密钥派生，分离加密与认证子密钥
- 可选 Gzip 压缩（兼容性降级）
- 支持文本与文件的加密/解密 UI，支持 .enc 文件上传用于文本解密

This is a browser-based streaming encryption demo (HTML/JS) implementing:

- AES-256-GCM chunked encryption with streaming (zero-copy saving when supported)
- Chained HMAC per-chunk for tamper detection
- PBKDF2 + optional HKDF (key-file mixing) with separate keys for encryption and MAC
- Optional Gzip compression with graceful fallback
- Text and file encrypt/decrypt UI; supports uploading `.enc` for text decryption


## 使用 / Usage

1. 打开 `index.html`（例如本地用静态服务器或直接在浏览器中打开）。
2. 在“主密码”中输入密码（不要在不受信环境输入真实密码）。
3. 可选：加载密钥文件（加密与解密必须使用相同密钥文件）。
4. 选择迭代次数（PBKDF2），可以点击测速按钮获得推荐值。
5. 文本加密/解密：在文本页内操作，或上传 `.enc` 文件到文本解密面板（小文件推荐，超过 2MB 建议使用文件解密页）。
6. 文件加密/解密：使用文件标签拖拽或选择文件，支持 showSaveFilePicker 的浏览器会进行流式保存。

1. Open `index.html` (serve with a static server or open directly).
2. Enter a master password (do not use real secrets in untrusted environments).
3. Optionally load a key-file (must use the same file for encrypt & decrypt if used).
4. Select PBKDF2 iterations; use the benchmark button to get a recommended value.
5. For text, use the Text tab (you may upload a small `.enc` to auto-fill Base64—use File tab for large files).
6. For files, use the File tab; browsers that support `showSaveFilePicker` will save without copying to memory.


## 安全说明 / Security Notes

- 请勿在公共或不受信的环境输入真实主密码或上传敏感密钥文件。
- 密钥派生已分离为加密键与认证键（安全设计），但请确保密码强度及迭代次数足够。
- 日志系统默认关闭，启用日志将显示运行信息（避免在公开环境启用）。
- 该示例以教育和演示为主，部署到生产前请让专业安全人员进行审计。

- Do not enter real secrets in public/untrusted environments.
- Keys are derived into separate encryption and MAC keys; ensure a strong password and sufficient PBKDF2 iterations.
- Logging is off by default; enabling logs may expose sensitive runtime info—avoid in public contexts.
- This project/demo is educational. Have a security audit before production use.


## 文件 / Files of interest

- `index.html` - 主界面与全部实现（单文件演示）。

- `index.html` - Main single-file demo and implementation.


## 许可 / License

本项目采用 GNU Affero General Public License v3.0（AGPL-3.0）。详见仓库 LICENSE 文件。

This project is licensed under the GNU Affero General Public License v3.0 (AGPL-3.0). See LICENSE in the repository.

---

**许可恢复 / License restoration (audit note)**

- 中文：由于未知原因，仓库 LICENSE 的部分内容曾被意外翻译成中文。现已恢复为官方 GNU Affero General Public License v3（英文原文），以便审计。恢复提交 SHA：6423369237acd72744b86af9cf085e397f8cf296。
- English: For auditability, part of the repository LICENSE was accidentally translated into Chinese; it has now been restored to the official GNU Affero General Public License v3 (English). Restore commit SHA: 6423369237acd72744b86af9cf085e397f8cf296.


## 贡献 / Contributing

欢迎提交 issue 或 PR。请在提出安全相关问题时使用私密渠道（不要在 issue 中泄露敏感密钥或密码）。

Contributions welcome via issues or pull requests. For security-sensitive reports, contact the repository owner privately—do not post secrets in issues.


## 联系 / Contact

仓库维护者：mcsc2009

Maintainer: mcsc2009
