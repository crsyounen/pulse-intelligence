# Pulse Intelligence 本地模型

[Pulse Relay](https://developers.crsyounen.com) 电脑端的 **Pulse 本地模型**：Qwen3-0.6B（Q4_K_M 量化）加两个 LoRA 微调，由 llama.cpp b12180 的 llama-server 运行。它在你自己的电脑上运行，为 iPhone 的灵动岛和锁屏写一句话摘要、补充快捷回复按钮，并判断一轮对话是「等你回复」还是「结束但有问题」。

- 只在本机运行。对话内容不会因为这个模型被发到任何服务器。
- 一般不需要手动下载：在 Pulse Relay 电脑端的设置里点「下载 Pulse 本地模型」，应用会自动下载这里的文件，并逐个校验 SHA256。
- 只有在应用内下载失败时（比如网络连不上 GitHub），才需要手动下载，具体步骤见下文。

## 文件（Release `model-c1`）

| 文件 | 大小 | 内容 |
|---|---|---|
| `model.gguf` | 484 MB | Qwen3-0.6B，Q4_K_M 量化 |
| `brief-lora.gguf` | 40 MB | 摘要用的 LoRA |
| `reply-lora.gguf` | 20 MB | 快捷回复和结束状态用的 LoRA |
| `llama-b12180-macos-arm64.tar.gz` | 12 MB | llama-server，Mac（Apple 芯片） |
| `llama-b12180-win-x64-vulkan.zip` | 32 MB | llama-server，Windows（Vulkan / CPU，含 VC++ 运行库） |

每个文件的 SHA256 都列在 Release 说明和 `SHA256SUMS` 文件里，和应用内置的值一致。手动下载后可以用 `shasum -a 256 -c SHA256SUMS`（Windows 用 `certutil -hashfile <文件> SHA256`）核对。

## 手动安装

1. 在 Pulse Relay 电脑端的设置里点「打开模型文件夹」，它会打开数据文件夹下的 `models`。
2. 把三个 `.gguf` 文件放进 `models`。
3. 把对应平台的 llama 压缩包解压到数据文件夹下的 `llama` 文件夹。`llama` 和 `models` 在同一层，文件直接放在 `llama` 里面，不要多套一层文件夹。Windows 用资源管理器解压 zip 就行；Mac 双击 tar.gz 即可解压。
4. 回到设置。应用校验通过后，就可以打开 Pulse Intelligence。

## Powered by

- [Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B)，Qwen 团队（阿里云），Apache License 2.0
- [llama.cpp](https://github.com/ggml-org/llama.cpp)，MIT License

许可证全文见 `LICENSE`、`NOTICE` 和 `licenses/`。

---

**English.** The on-device model behind Pulse Relay's *Pulse Intelligence*: Qwen3-0.6B (Apache-2.0, quantized to Q4_K_M) plus two LoRA adapters (Apache-2.0), served by llama.cpp's llama-server (MIT). The Pulse Relay desktop app downloads and verifies these files itself; manual download is only a fallback. See `NOTICE` for attribution and modifications.
