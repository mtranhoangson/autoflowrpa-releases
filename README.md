# AutoFlowRPA — Releases

Repo công khai chỉ để **host file cài đặt** cho nút Download trên website (autoflowrpa.com).
Website đọc release **mới nhất đã publish** qua GitHub API (`releases/latest`).

## Cách phát hành phiên bản mới
1. Vào tab **Releases → Draft a new release**.
2. Tạo **tag** dạng `v1.0.0` (semver).
3. **Attach binaries** — đặt tên file đúng quy ước để website tự nhận:
   - Installer: tên chứa `setup` + đuôi `.exe`, hoặc đuôi `.msi`
     - ví dụ: `AutoFlowRPA-Setup-1.0.0.exe`
   - Bản portable: tên chứa `portable` + đuôi `.zip`
     - ví dụ: `AutoFlowRPA-portable-1.0.0.zip`
   - Bản macOS: tên chứa `macos` + đuôi `.dmg`
     - ví dụ: `AutoFlowRPA-macos-arm64-1.0.0.dmg`
     - ghi rõ kiến trúc (`arm64` / `x64`) vì hai bản không thay thế được cho nhau
4. **Publish release** (KHÔNG để Draft, KHÔNG tick Pre-release — nếu không `releases/latest` sẽ không thấy).

> Quy ước tên khớp regex trong `src/lib/github.ts` của repo website:
> `/setup.*\.(exe|msi|zip)$/i`, `/portable.*\.zip$/i` và `/\.dmg$/i`.

## Lưu ý về bản macOS

Bản macOS hiện **ký ad-hoc, chưa notarize**, nên Gatekeeper sẽ cảnh báo
"unidentified developer". Người dùng phải chuột phải > **Open** lần đầu, hoặc
chạy `xattr -dr com.apple.quarantine /Applications/AutoFlowRPA.app`.

Muốn hết cảnh báo này cần tài khoản Apple Developer ($99/năm) và chứng chỉ
Developer ID Application — xem bảng biến môi trường `APPLE_*` trong
`docs/BUILD_MACOS.md` của repo code.