# Nhánh `vn-channel` — bản vá cho kênh tiếng Việt

Nhánh này giữ nguyên Skill gốc của kaomei và chỉ thêm các bản vá nhỏ, không đổi mặc định, để dễ cập nhật từ upstream.

| Bản vá | Cách dùng |
|---|---|
| Font viết tay có đủ dấu tiếng Việt `assets/fonts/PatrickHand.ttf` (OFL), thay cho Caveat vốn thiếu ơ, ư và dấu thanh | `AUTOPILOT_FONT=<skill>/assets/fonts/PatrickHand.ttf` hoặc trường `font` trong `project.json` |
| Encode bằng GPU NVIDIA (NVENC) cho renderer B1–B4 | `AUTOPILOT_VIDEO_ENCODER=h264_nvenc` (hoặc `hevc_nvenc`). Mặc định vẫn `libx264` |
| Whisper tự dùng GPU khi có | `align_captions.py` mặc định `--device auto` (CUDA nếu có), bật fp16 trên GPU. Nên thêm `--language vi --model large-v3` |

Font mặc định cho phụ đề B1–B4 khổ ngang (Noto Sans) và chữ hook của B4 (Nunito 900) đã đủ dấu tiếng Việt, không cần vá. Phụ đề B6 (Archivo Black) thiếu dấu; nếu dùng B6 phải chọn font khác qua `caption_override`.

## Cập nhật từ upstream

```bash
git remote add upstream https://github.com/kaomei/stickman-video-director.git
git fetch upstream main
git checkout vn-channel && git rebase upstream/main
```

Sau khi rebase, chạy lại test của Skill (`npm test` trong `skills/directing-stickman-videos`) rồi mới nâng phiên bản submodule trong repo kênh.
