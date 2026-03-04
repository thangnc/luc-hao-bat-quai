---
name: gieo-que
description: Gieo quẻ Lục Hào (六爻) - Kinh Dịch, Ngũ Hành, Bát Quái. Tự động kích hoạt khi người dùng muốn gieo quẻ, bói quẻ, xem quẻ, xin quẻ, hoặc hỏi về vận mệnh, tình duyên, tài lộc, sự nghiệp, sức khỏe mà cần gieo quẻ. Trigger khi gặp từ khoá gieo quẻ, bói quẻ, xem quẻ, lục hào, xin quẻ, khởi quẻ, lập quẻ, bói dịch, hoặc khi người dùng cung cấp thông tin cá nhân (tên, ngày sinh) kèm câu hỏi vận mệnh mà chưa dùng lệnh /gieo-que.
---

# Gieo Quẻ Lục Hào (Auto-invoked)

Skill này được kích hoạt tự động khi Claude nhận diện người dùng muốn gieo quẻ qua ngữ cảnh hội thoại.

## Hành động

Thực hiện đúng quy trình gieo quẻ như lệnh `/gieo-que`.

Tra bảng chi tiết (nạp giáp, nạp chi, 64 quẻ, cung quẻ, lục thần, nạp âm) tại: `${CLAUDE_PLUGIN_ROOT}/skills/gieo-que/references/bang-tra-cuu.md`

Tham khảo quy trình tại: `${CLAUDE_PLUGIN_ROOT}/commands/gieo-que.md`

1. Thu thập thông tin (họ tên, ngày sinh, giới tính, câu hỏi)
2. Lập Tứ Trụ (Bát Tự)
3. Tính Thượng Quái, Hạ Quái, hào động
4. Lập bảng quẻ Lục Hào (nạp giáp, nạp chi, lục thân, thế ứng, lục thần)
5. Trình bày kết quả
6. Hỏi người dùng có muốn luận giải không

Nếu thiếu thông tin, hỏi lịch sự:

> Để gieo quẻ, xin cung cấp:
> 1. 📛 Họ tên đầy đủ
> 2. 📅 Ngày tháng năm sinh (dương lịch)
> 3. 🕐 Giờ sinh (nếu biết)
> 4. 👤 Giới tính
> 5. ❓ Câu hỏi hoặc lĩnh vực muốn hỏi