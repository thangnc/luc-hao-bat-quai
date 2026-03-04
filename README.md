# i-ching-plugins

A collection of Vietnamese I Ching (Kinh Dịch) divination plugins for Claude — covering Lục Hào, Bát Quái, and related metaphysical arts.

## Plugins

### `luc-hao` — Lục Hào Bát Quái (六爻八卦)

Gieo quẻ và luận giải Lục Hào Bát Quái theo phương pháp Mai Hoa Dịch Số — Vietnamese Six-Line I Ching divination with hexagram casting and interpretation.

## Cấu trúc

```
.claude-plugin/
  marketplace.json                  # Marketplace listing (repo-level)
plugins/
  luc-hao/
    .claude-plugin/
      plugin.json                   # Plugin metadata và entry points
    commands/
      gieo-que.md                   # /gieo-que — Gieo quẻ Lục Hào
      luan-giai.md                  # /luan-giai — Luận giải quẻ
    skills/
      gieo-que/
        SKILL.md                         # Tự động khi user muốn gieo quẻ
        references/bang-tra-cuu.md       # Bảng tra cứu Nạp Giáp, Nạp Chi, 64 quẻ, Lục Thần, Nạp Âm
      luan-giai/
        SKILL.md                         # Tự động khi user muốn giải quẻ
        references/quy-tac-luan-giai.md  # Quy tắc luận giải Dụng Thần, Vượng Suy, hào động
```

## Commands vs Skills

| | Commands | Skills (auto-invoked) |
|---|---|---|
| **Kích hoạt** | User gõ `/gieo-que` hoặc `/luan-giai` | Claude tự nhận diện từ ngữ cảnh |
| **Khi nào** | User biết lệnh, muốn chạy trực tiếp | User nói tự nhiên ("gieo quẻ cho tôi") |
| **Logic** | Chứa toàn bộ hướng dẫn chi tiết | Nhẹ, trỏ về commands/ để thực hiện |

Skills hoạt động như "bộ nhận diện" — khi user nói tự nhiên, skill kích hoạt và thực hiện theo hướng dẫn trong commands.

## Thành phần

### `/gieo-que` + skill `gieo-que`

Kích hoạt khi: `gieo quẻ`, `bói quẻ`, `xem quẻ`, `xin quẻ`, `lục hào`, `khởi quẻ`, `lập quẻ`, `bói dịch`, hoặc user cung cấp tên + ngày sinh kèm câu hỏi vận mệnh.

**Quy trình:**
1. Thu thập: họ tên, ngày sinh, giờ sinh, giới tính, câu hỏi
2. Lập Tứ Trụ (Bát Tự) theo Can Chi + Nạp Âm
3. Tính Thượng Quái, Hạ Quái, hào động theo Mai Hoa Dịch Số
4. Lập bảng Lục Hào (Nạp Chi, Lục Thân, Lục Thần, Thế/Ứng, hào động)
5. Hỏi người dùng có muốn luận giải không

**Ví dụ:**
```
/gieo-que Nguyễn Văn A, 15/03/1990, nam, hỏi tài lộc
"Tôi muốn gieo quẻ xem tài lộc, tên Nguyễn Văn A, sinh 15/03/1990"
```

### `/luan-giai` + skill `luan-giai`

Kích hoạt khi: `luận giải`, `giải quẻ`, `phân tích quẻ`, `ý nghĩa quẻ`, `đoán quẻ`, `quẻ này tốt không`, hoặc ngay sau khi gieo quẻ xong.

**Quy trình:**
1. Xác định Dụng Thần theo lĩnh vực hỏi
2. Phân tích Vượng/Suy (Nguyệt kiến, Nhật thần)
3. Phân tích Hào Động (hồi đầu sinh/khắc, hợp/xung)
4. Phân tích Thế Ứng + Lục Thần bổ trợ
5. Tổng hợp kết luận + thời vận + lời khuyên

**Output format:**
```
🔮 TỔNG QUAN   — quẻ tượng + ý nghĩa chính
📊 DỤNG THẦN   — dụng thần nào, vượng/suy
⚡ HÀO ĐỘNG    — hào động hóa gì, tác dụng
🔮 KẾT LUẬN    — tốt/xấu/bình hòa
📅 THỜI VẬN    — khi nào ứng nghiệm
💡 LỜI KHUYÊN  — hành động cụ thể
```

**Ví dụ:**
```
/luan-giai Thiên Phong Cấu, hào 1 động, mệnh Hỏa, hỏi tài lộc
"Quẻ này có ý nghĩa gì?" / "Giải quẻ giúp tôi"
```

## Luồng sử dụng

```
Cách 1: Dùng commands
  /gieo-que + thông tin  →  /luan-giai

Cách 2: Nói tự nhiên (skills tự kích hoạt)
  "Gieo quẻ cho tôi..."  →  "Giải quẻ giúp tôi"

Cách 3: Luận giải quẻ có sẵn
  /luan-giai Thiên Phong Cấu, hào 1 động, mệnh Hỏa, hỏi tài lộc
```

## Cài đặt

Cài qua Claude marketplace hoặc sao chép thư mục `plugins/luc-hao/` vào `.claude/plugins/`.

## Lưu ý

Nên tắt **thinking mode** (extended thinking) khi dùng plugin này. Tính toán Lục Hào đã được hướng dẫn chi tiết từng bước trong commands — thinking mode không cần thiết và làm chậm phản hồi.
