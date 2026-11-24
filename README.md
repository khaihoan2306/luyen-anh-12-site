# Luyện Anh 12 — website

Trang tĩnh (không cần build) gồm:

| File | Dùng cho App Store Connect |
|---|---|
| `index.html` | **Marketing URL**; mục `#ho-tro` dùng làm **Support URL** |
| `privacy.html` | **Privacy Policy URL** |

## Cập nhật chính sách quyền riêng tư

Đừng sửa `privacy.html` bằng tay. Nội dung gốc nằm trong app: `thptqg-tieng-anh/src/features/legal/privacyPolicy.ts`.
Sửa ở đó (nhớ đổi `updatedAt`), rồi chạy trong thư mục dự án:

```bash
node scripts/build-privacy-html.mjs ~/Desktop/luyen-anh-12-site/privacy.html
```

## Xem thử trên máy

```bash
cd ~/Desktop/luyen-anh-12-site && python3 -m http.server 8765
# mở http://localhost:8765
```

## Đăng lên web (chọn một)

**GitHub Pages**: tạo repo mới, đẩy toàn bộ thư mục này lên nhánh `main`, vào Settings → Pages →
Source: `main` / `(root)`. URL dạng `https://<tài-khoản>.github.io/<repo>/`.

**Firebase Hosting** (dự án app đã dùng Firebase):
```bash
npm i -g firebase-tools && firebase login
firebase init hosting   # public directory: .   single-page app: No
firebase deploy --only hosting
```

Sau khi có URL, điền vào `store.config.json` của app:
- `privacyPolicyUrl`: `<URL>/privacy.html`
- `supportUrl`: `<URL>/#ho-tro`
- `marketingUrl` (tuỳ chọn): `<URL>/`

Nút "Tải trên App Store" và Smart App Banner trỏ tới app id `6837941373` — chỉ hoạt động sau khi app được phát hành.
