Được nha. Mình đã đọc lại **file đặc tả SuperCalendar hiện tại** và sẽ lấy phần mô tả mới của bạn làm **yêu cầu cập nhật chính**, thay vì giữ nguyên các phần cũ nếu chúng bị mâu thuẫn. Đặc tả hiện tại đang có các phần Calendar, To-do, Notes, Theme/VIP, Template, Lock Screen... nên mình sẽ **mở rộng và chỉnh lại cấu trúc**, chứ không cần viết lại từ đầu. 

Đặc biệt, mình thấy có vài thay đổi khá lớn so với bản cũ:

### 1. Navigation / Taskbar

Mình đề xuất taskbar dưới cùng gồm **5 mục chính**:

| Tab              | Chức năng                                                   |
| ---------------- | ----------------------------------------------------------- |
| 🏠 **Trang chủ** | Dashboard, hướng dẫn, template/widget, tổng quan nhanh      |
| 📅 **Lịch**      | Month / Week, Event, Goals, Habit                           |
| ✅ **Cần làm**    | To-do List                                                  |
| 📝 **Ghi chú**   | Notes / Quick Notes                                         |
| ⚙️ **Cài đặt**   | Account, Appearance, Language, Date & Time, Notification... |

Mình **không khuyên nhét VIP/Template Store thành một tab riêng** vì sẽ làm taskbar hơi rối. Hai phần này có thể nằm trong **Trang chủ** hoặc **Cài đặt → VIP & Templates**.

Ngoài ra, nếu sau này muốn thêm một tính năng rất hợp với app thì mình đề xuất:

**Trang chủ → Today / Dashboard**

Ví dụ:

> Good morning 👋
>
> 📅 Today
> 3 events
>
> ✅ Tasks
> 4/7 completed
>
> 🎯 Today's Goal
> Study Flutter 2 hours
>
> 🔥 Habit
> Drink water ✓

Như vậy Home thực sự có lý do để tồn tại, thay vì chỉ là trang trung gian.

---

### 2. Trang chủ sẽ đổi khá nhiều

Theo mô tả mới của bạn, Home không phải một calendar lớn nữa mà giống **trang giới thiệu + dashboard + template center**.

Mình sẽ thiết kế đặc tả theo kiểu:

**SUPER CALENDAR**

> Welcome / hướng dẫn sử dụng

Sau đó:

**Widget Templates**

* To Do
* Habit
* Week
* Month
* Goals
* Notes
* ... có thể mở rộng thêm

Trong đó có khoảng **3 template miễn phí**.

Các template khác sẽ có:

🔒 **VIP**

Khi user bấm vào template khóa → hiển thị:

> This template is available for VIP users.
> Upgrade to VIP to unlock.

Điểm này khá hợp với hướng monetization mà bản cũ của bạn đã định hướng: VIP có Theme Builder, custom color, typography, layout và tạo Template. 

---

### 3. Calendar sẽ trở thành một module lớn hơn

Mình sẽ sửa Calendar thành:

**LỊCH**

Góc trên:

`[ WEEK ] [ MONTH ]                 [ + ]`

User có thể:

* chuyển Week / Month
* bấm `+` để tạo Event
* hoặc **bấm trực tiếp vào ngày**
* nhập:

  * tên lịch trình
  * ngày
  * giờ bắt đầu
  * giờ kết thúc
  * màu
  * ghi chú
  * địa điểm
  * reminder
  * repeat

Nếu bấm trực tiếp vào ngày thì ngày đó được chọn sẵn → không cần nhập lại ngày.

---

### 4. Goals

Mình rất thích phần này và nghĩ nên đưa thẳng vào Calendar.

Ví dụ Month:

> **GOALS — OCTOBER**
>
> ○ Finish Flutter project
> ○ Read 2 books
> ○ Exercise 12 times

Còn Week:

> **GOALS — OCT 5–11**
>
> ○ Finish Calendar UI
> ○ Study Flutter 5 hours
> ○ Complete assignment

**Monthly Goal và Weekly Goal là hai loại dữ liệu khác nhau**, dù UI nằm cùng vị trí.

Mình sẽ bổ sung vào Data Model:

`Goal`

* ID
* Title
* Description
* Type: Week / Month
* Start Date
* End Date
* Completed
* Progress
* Created At
* Updated At

Sau này còn có thể làm progress:

`██████░░░░ 60%`

---

### 5. Habit

Phần Habit nên tách khỏi Event.

Ví dụ user tạo:

> **Drink Water**

Sau đó chọn:

* Every day
* Every week
* Specific days
* Custom repeat

Ví dụ:

> Monday ✓
> Tuesday ✓
> Wednesday ✓
> Thursday ✓
> Friday ✓

App tự tạo các occurrence theo rule.

Nhưng nếu một ngày user **không muốn thực hiện**, có thể bấm riêng ngày đó:

> Oct 8
> Drink Water
> [Edit] [Delete occurrence]

Quan trọng là mình sẽ thiết kế theo kiểu **Habit Rule + Habit Occurrence**, chứ không tạo một Habit hoàn toàn mới cho từng ngày.

Như vậy sau này mới dễ xử lý repeat.

---

### 6. To-do sẽ chi tiết hơn rất nhiều

Mình sẽ đổi phần cũ từ một danh sách Task thông thường thành **TO-DO LIST editor**.

Mặc định:

> **TO-DO LIST**
>
> ─────────────────
> ☐
> ─────────────────
> ☐
> ─────────────────
> ☐
> ─────────────────

Khoảng **36 dòng**, có thể scroll.

Góc phải:

**＋**

Bấm `+`:

1. tạo một dòng mới
2. xuất hiện checkbox
3. tự focus vào dòng
4. con trỏ sẵn sàng nhập text

Ví dụ:

> ☐ Finish Java assignment

Sau khi tạo xong, cuối task có:

**Edit**

Bấm Edit có thể mở phần chi tiết:

* Title
* Description
* Due date
* Due time
* Priority
* Reminder
* Repeat
* Category
* Color
* Note
* Attachment
* Subtasks
* Tags
* Estimated time

Mình đặc biệt đề xuất thêm **Subtasks**.

Ví dụ:

> ☐ Finish Java assignment
> `Edit`
>
> Subtasks:
>
> * ☐ Write code
> * ☐ Test
> * ☐ Submit

Cái này sẽ làm To-do của app mạnh hơn nhiều mà vẫn giữ được UI minimal.

---

### 7. Settings

Mình sẽ xây Settings thành các nhóm rõ ràng:

**ACCOUNT**

* Account
* Profile
* VIP Status

**APPEARANCE**

* Theme
* Custom Color 🔒 VIP
* Widget Style
* Font 🔒 VIP
* Layout 🔒 VIP
* Dark Mode

**CALENDAR**

* Default Calendar
* Week starts on
* Calendar permissions
* Default event duration

**TASKS**

* Default priority
* Completed task behavior
* Default reminder

**NOTIFICATIONS**

* Enable notifications
* Event reminder
* Task reminder
* Habit reminder
* Goal reminder

**LANGUAGE & REGION**

* Language
* Date format
* Time format
* First day of week

**LOCK SCREEN**

* Enable Lock Screen
* Schedule visibility
* To-do visibility
* Quick Note

**HELP**

* Hướng dẫn sử dụng
* FAQ
* About SuperCalendar

**APP**

* Version
* Privacy
* Terms

---

### 8. Lock Screen cũng cần sửa theo mô tả mới

Bản hiện tại đang mô tả Schedule + To-do, nhưng bạn vừa thay đổi thành **3 khu vực**. Bản cũ hiện ghi Lock Screen có Schedule và To-do, còn Quick Add Note mới chỉ được mô tả sơ bộ. 

Mình sẽ sửa thành:

**LOCK SCREEN**

### Section 1 — Schedule

Hiển thị lịch trình.

* Read-only
* Không edit trực tiếp
* Không delete
* Tap → mở app

### Section 2 — To-do

Hiển thị task.

Prototype có thể cho:

* xem task
* tick complete

### Section 3 — Quick Note

Cho phép Android sử dụng **thanh thông báo của SuperCalendar** để nhập nhanh note.

Ví dụ:

> 📝 SuperCalendar
> Quick Note
> `[ Type something... ]`

Sau khi lưu → Note được lưu vào database chung.

Điểm này cũng phù hợp với nguyên tắc hiện tại của spec là Lock Screen/Notification phải sử dụng **cùng nguồn dữ liệu với app chính**. 

---

## Một thay đổi mình rất muốn bổ sung vào đặc tả

Hiện tại model dữ liệu của bạn mới có:

`User / Event / Task / Note / Theme / Template / Purchase` 

Với chức năng mới, mình nghĩ phải thêm:

```text
Goal
Habit
HabitOccurrence
WidgetTemplate
TaskSubtask
Category
```

Đặc biệt **WidgetTemplate** và **Theme** nên tách nhau.

Vì:

**Theme**

> màu + font + radius + shadow + overall appearance

Còn:

**Widget Template**

> cách một loại widget được bố trí.

Ví dụ:

```text
Theme
└── Pastel Pink

Widget Template
└── To-Do Minimal
    ├── Layout
    ├── Checkbox Style
    ├── Typography
    ├── Spacing
    └── Preview
```

Như vậy sau này user có thể:

> Theme: Pastel Pink
> To-Do Widget: Minimal 01
> Habit Widget: Soft Grid
> Calendar Widget: Monthly Clean

→ Đây sẽ là nền tảng rất tốt cho hệ thống **VIP + Template Marketplace** sau này.

---

**Tóm lại:** mình sẽ không chỉ "chèn" phần bạn vừa nói vào file cũ, mà sẽ **refactor lại đặc tả để các chức năng mới khớp với nhau**, đặc biệt là `Navigation → Home → Calendar → Goals/Habit → To-do → Notes → Settings → VIP/Template → Lock Screen`.

Nếu mình viết bản đặc tả hoàn chỉnh tiếp theo, mình sẽ giữ **văn phong và cấu trúc kiểu tài liệu kỹ thuật hiện tại**, đánh số lại các section và cập nhật cả **Data Model, Navigation, UI/UX, VIP, Template, Acceptance Criteria và Roadmap** để sau này bạn có thể dùng chính file đó làm tài liệu phát triển Flutter.
