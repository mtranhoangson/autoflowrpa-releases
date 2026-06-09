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
4. **Publish release** (KHÔNG để Draft, KHÔNG tick Pre-release — nếu không `releases/latest` sẽ không thấy).

> Quy ước tên khớp regex trong `src/lib/github.ts` của repo website:
> `/setup.*\.exe$|\.msi$/i` và `/portable.*\.zip$|\.zip$/i`.