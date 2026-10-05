# SUPER CALENDAR

## FUNCTIONAL REQUIREMENTS SPECIFICATION

**Project Name:** Super Calendar
**Document Type:** Functional Requirements Specification
**Version:** 1.0
**Platform:** Mobile Application
**Framework:** Flutter
**Programming Language:** Dart
**Target Platform:** Android – Prototype
**Future Platform:** iOS

---

# 1. INTRODUCTION

## 1.1 Purpose

Functional Requirements Specification được xây dựng dựa trên System Specification, định hướng sản phẩm, nghiên cứu các ứng dụng tương tự và các yêu cầu về giao diện, trải nghiệm người dùng đã xác định.

Tài liệu là cơ sở để:

* Thiết kế UI/UX.
* Xây dựng Use Case.
* Thiết kế Database.
* Thiết kế Class Diagram.
* Phát triển ứng dụng Flutter.
* Phát triển các thành phần Android Native khi cần.
* Xây dựng Test Case.
* Kiểm thử và nghiệm thu hệ thống.

---

# 2. SYSTEM OVERVIEW

## 2.1 Product Description

**Super Calendar** là ứng dụng quản lý năng suất cá nhân trên thiết bị di động, kết hợp giữa:

* Calendar.
* Event.
* Goal.
* Habit.
* To-do List.
* Notes.
* Notification.
* Lock Screen.
* Theme.
* Widget Template.
* VIP.
* Template Marketplace.

Mục tiêu của hệ thống là giúp người dùng **lập kế hoạch, thực hiện công việc, theo dõi thói quen và cá nhân hóa cách sử dụng ứng dụng** trong một hệ thống thống nhất.

Sản phẩm tập trung vào bốn định hướng chính:

> **PLAN – DO – PERSONALIZE – SEE IT FIRST**

Trong đó:

* **PLAN:** Quản lý lịch trình bằng Calendar.
* **DO:** Quản lý công việc bằng To-do.
* **PERSONALIZE:** Cá nhân hóa bằng Theme và Widget Template.
* **SEE IT FIRST:** Đưa lịch trình và công việc quan trọng đến nơi người dùng dễ nhìn thấy thông qua Home, Notification và Lock Screen.

---

# 3. GENERAL FUNCTIONAL REQUIREMENTS

## 3.1 Application Navigation

Ứng dụng phải cung cấp thanh điều hướng chính ở cuối màn hình (**Bottom Navigation Bar**) gồm 5 khu vực:

| STT | Tab      | Chức năng                                       |
| --- | -------- | ----------------------------------------------- |
| 1   | Home     | Dashboard, Template Center, thông tin tổng quan |
| 2   | Calendar | Event, Goal, Habit                              |
| 3   | To-do    | Quản lý Task                                    |
| 4   | Notes    | Quản lý Note                                    |
| 5   | Settings | Cấu hình ứng dụng                               |

Home là màn hình mặc định khi người dùng mở ứng dụng.

Các chức năng:

* VIP.
* Theme.
* Widget Template.
* Marketplace.

không được tạo thành các tab chính riêng biệt mà được truy cập thông qua Home, Template Center hoặc Settings.

---

## 3.2 Data Consistency

Hệ thống phải sử dụng nguyên tắc **Single Source of Truth**.

Một dữ liệu nghiệp vụ chỉ được lưu tại nguồn dữ liệu chính.

Ví dụ:

* Event được lưu trong Event.
* Task được lưu trong Task.
* Goal được lưu trong Goal.
* Habit được lưu trong Habit/HabitOccurrence.
* Note được lưu trong Note.

Home Dashboard, Notification và Lock Screen chỉ sử dụng dữ liệu từ các nguồn trên.

Không được tạo bản sao dữ liệu chỉ để phục vụ hiển thị.

---

## 3.3 Local Data Storage

Trong Prototype:

* Local Database là nguồn dữ liệu chính.
* Không bắt buộc Backend.
* Không bắt buộc Cloud Synchronization.
* Dữ liệu phải được lưu sau khi người dùng tạo hoặc chỉnh sửa.
* Dữ liệu phải còn tồn tại sau khi đóng và mở lại ứng dụng.

---

# 4. FUNCTIONAL REQUIREMENTS

---

# FR-01 – ACCOUNT MANAGEMENT

## 4.1 Description

Account Management cho phép người dùng xem và quản lý thông tin tài khoản, thông tin cá nhân cơ bản và trạng thái VIP.

Trong Prototype, hệ thống không bắt buộc phải triển khai hệ thống đăng nhập trực tuyến. User có thể được quản lý dưới dạng local account.

## 4.2 Actor

**User**

## 4.3 Preconditions

* Ứng dụng đã được cài đặt.
* Ứng dụng khởi chạy thành công.

## 4.4 Main Flow

1. User mở Settings.
2. User chọn Account/Profile.
3. System hiển thị thông tin tài khoản.
4. User có thể chỉnh sửa thông tin được hỗ trợ.
5. User lưu thay đổi.
6. System kiểm tra dữ liệu.
7. System lưu thông tin.
8. System hiển thị thông tin mới.

## 4.5 Data

Account có thể bao gồm:

* User ID.
* Display Name.
* Email nếu được hỗ trợ.
* Avatar nếu được hỗ trợ.
* VIP Status.
* Created At.
* Updated At.

## 4.6 Business Rules

* Prototype không bắt buộc Login/Logout online.
* Không lưu Device PIN hoặc Password của thiết bị.
* VIP Status phải được sử dụng để kiểm soát các chức năng Premium.

---

# FR-02 – HOME

## 5.1 Description

Home là màn hình chính và là màn hình mặc định khi mở Super Calendar.

Home cung cấp thông tin tổng quan và truy cập nhanh đến các chức năng quan trọng.

Home bao gồm:

* App Introduction/Welcome.
* Basic User Guide.
* Today Dashboard.
* Template Center.
* VIP/Personalization entry point.

Home không phải là một Calendar đầy đủ.

## 5.2 Main Flow

1. User mở ứng dụng.
2. System hiển thị Home.
3. System tải dữ liệu của ngày hiện tại.
4. System tổng hợp Event, Task, Goal và Habit.
5. System hiển thị Today Dashboard.
6. User có thể xem các công việc/lịch trình quan trọng.
7. User có thể truy cập Template Center.
8. User có thể chuyển sang các tab khác.

## 5.3 Today Dashboard

Today Dashboard có thể hiển thị:

* Today's Events.
* Today's Tasks.
* Today's Goals.
* Today's Habits.

Dashboard phải phản ánh dữ liệu thực tế từ Database.

Ví dụ:

Nếu User hoàn thành Task trong To-do:

> Task Database → Updated → Home Dashboard cũng phải hiển thị trạng thái Completed.

## 5.4 Template Center

Home cung cấp Template Center để người dùng:

* Xem Widget Template.
* Preview Template.
* Apply Template.
* Xem Free Template.
* Xem Premium Template.
* Truy cập Marketplace.

Prototype có thể cung cấp khoảng 3 Free Templates ban đầu.

Premium Templates phải hiển thị biểu tượng khóa.

---

# FR-03 – CALENDAR

## 6.1 Description

Calendar là trung tâm quản lý lịch trình của ứng dụng.

Calendar phải hỗ trợ hai chế độ:

* **Week View**
* **Month View**

Calendar quản lý:

* Event.
* Goal.
* Habit.

## 6.2 Calendar Interface

Calendar phải có:

* Week/Month switch ở phía trên.
* Nút **+** ở góc trên bên phải.
* Khu vực hiển thị ngày.
* Khu vực hiển thị Event.
* Khu vực GOALS.
* Khu vực Habit nếu có dữ liệu.

## 6.3 Create Event – Using +

1. User mở Calendar.
2. User nhấn **+**.
3. System mở Create Event.
4. User chọn Date.
5. User chọn Start Time.
6. User chọn End Time.
7. User nhập Event Information.
8. User chọn Save.
9. System validate.
10. System lưu Event.
11. Calendar cập nhật.

## 6.4 Create Event – Selecting Date

User cũng có thể tạo Event bằng cách nhấn trực tiếp vào một ngày.

1. User chọn một ngày trên Calendar.
2. System mở Create Event.
3. Date được tự động điền theo ngày User vừa chọn.
4. User chỉ cần nhập các thông tin còn lại.
5. User Save.
6. System lưu Event.

User không cần chọn lại Date.

## 6.5 Calendar Navigation

User có thể:

* Chuyển Week/Month.
* Di chuyển đến tuần trước/sau.
* Di chuyển đến tháng trước/sau.
* Quay về Today.
* Chọn ngày cụ thể.

---

# FR-04 – EVENT MANAGEMENT

## 7.1 Description

Event đại diện cho một hoạt động có **thời gian cụ thể** trong lịch.

Event khác Task:

* **Event:** hoạt động được lên lịch tại một thời điểm/khoảng thời gian.
* **Task:** công việc cần hoàn thành.

## 7.2 Event Fields

Event bao gồm:

| Field       | Required |
| ----------- | -------- |
| Event ID    | Yes      |
| Title       | Yes      |
| Date        | Yes      |
| Start Time  | Yes      |
| End Time    | Yes      |
| Description | No       |
| Location    | No       |
| Category    | No       |
| Color       | No       |
| Note        | No       |
| Reminder    | No       |
| Repeat      | No       |
| Source      | Yes      |
| Created At  | Yes      |
| Updated At  | Yes      |

## 7.3 Event Validation

System phải kiểm tra:

* Title không được rỗng.
* Date hợp lệ.
* Start Time không được lớn hơn End Time.
* Reminder phải hợp lệ với Event.
* Repeat Rule phải hợp lệ.

## 7.4 Edit Event

User có thể chỉnh sửa:

* Title.
* Date.
* Time.
* Location.
* Category.
* Color.
* Note.
* Reminder.
* Repeat.

Sau khi lưu, dữ liệu phải được cập nhật trên:

* Calendar.
* Home Dashboard.
* Notification.
* Lock Screen nếu Event được hiển thị.

## 7.5 Delete Event

Khi User xóa Event:

* Event bị xóa khỏi Database.
* Event biến mất khỏi Calendar.
* Event biến mất khỏi Home Dashboard.
* Reminder liên quan bị hủy.
* Lock Screen được cập nhật.

## 7.6 System Calendar Integration

Ứng dụng có thể tích hợp với Android System Calendar.

Khi cần quyền:

1. System giải thích mục đích sử dụng quyền.
2. User cho phép hoặc từ chối.
3. Nếu Allow:

   * System đọc System Calendar Event.
   * Event có `source = system_calendar`.
4. Nếu Deny:

   * Local Calendar vẫn hoạt động bình thường.

System Calendar Event không được ghi đè hoặc làm mất Local Event.

---

# FR-05 – GOAL MANAGEMENT

## 8.1 Description

Goal cho phép User thiết lập và theo dõi mục tiêu theo tuần hoặc tháng.

Goal có hai loại:

* **Weekly Goal**
* **Monthly Goal**

Hai loại được quản lý riêng về mặt logic.

## 8.2 Goal Fields

* Goal ID.
* Goal Type.
* Title.
* Description.
* Start Date.
* End Date.
* Progress.
* Completed.
* Created At.
* Updated At.

## 8.3 Create Goal

1. User chọn Create Goal.
2. User chọn Weekly hoặc Monthly.
3. User nhập Title.
4. User nhập Description nếu cần.
5. User chọn Start Date.
6. User chọn End Date.
7. System validate.
8. System lưu Goal.
9. Goal xuất hiện trên Calendar/Home.

## 8.4 Goal Management

User có thể:

* Create.
* Edit.
* Update Progress.
* Mark Completed.
* Delete.

## 8.5 Business Rules

* Start Date ≤ End Date.
* Weekly Goal và Monthly Goal không được trộn dữ liệu.
* Progress không được âm.
* Goal Completed phải được phản ánh trên Dashboard.

---

# FR-06 – HABIT MANAGEMENT

## 9.1 Description

Habit cho phép User tạo hành động lặp lại và theo dõi việc thực hiện hành động đó.

Habit được chia thành:

**Habit Rule**

và

**Habit Occurrence**

## 9.2 Habit Rule

Habit Rule xác định:

* Habit Name.
* Start Date.
* End Date.
* Repeat Rule.

## 9.3 Repeat Rule

System phải hỗ trợ:

* Every Day.
* Every Week.
* Specific Days.
* Custom Repeat.

## 9.4 Habit Occurrence

Mỗi lần Habit xuất hiện trên một ngày cụ thể được xem là một Habit Occurrence.

Occurrence có thể có:

* Occurrence ID.
* Habit ID.
* Date.
* Status.
* Override Information nếu cần.

## 9.5 Main Flow

1. User chọn Create Habit.
2. User nhập Habit Name.
3. User chọn Start Date.
4. User chọn End Date nếu cần.
5. User chọn Repeat Rule.
6. System lưu Habit Rule.
7. System tạo/xác định các Occurrences.
8. Occurrences được hiển thị trên Calendar.
9. User có thể đánh dấu Completed.

## 9.6 Single Occurrence Management

Nếu User muốn xóa hoặc chỉnh sửa **chỉ một ngày**:

1. User chọn Occurrence.
2. System hiển thị tùy chọn Edit/Delete this occurrence.
3. User xác nhận.
4. System chỉ thay đổi Occurrence đó.
5. Habit Rule không bị thay đổi.

Nếu User chọn Edit/Delete Habit:

* System thay đổi toàn bộ Rule và các Occurrence liên quan.

---

# FR-07 – TO-DO LIST

## 10.1 Description

To-do List là khu vực quản lý các công việc cần hoàn thành.

Tiêu đề màn hình:

> **TO-DO LIST**

Giao diện theo hướng tối giản với các dòng ngang giống danh sách ghi chú.

Prototype có thể hiển thị khoảng **36 dòng** và cho phép Scroll khi danh sách dài hơn.

## 10.2 Quick Add

1. User mở To-do.
2. User nhấn **+**.
3. System thêm một Task mới.
4. Text Input tự động được Focus.
5. User nhập Task Title.
6. User có thể tick Checkbox.
7. System lưu Task.

Quick Add không yêu cầu nhập toàn bộ Task Detail.

## 10.3 Task Detail

Sau khi Task được tạo, User có thể chọn Edit.

Task Detail bao gồm:

* Title.
* Description.
* Due Date.
* Due Time.
* Priority.
* Reminder.
* Repeat.
* Category.
* Color.
* Note.
* Attachment.
* Subtasks.
* Tags.
* Estimated Time.
* Completed Status.
* Created At.
* Updated At.

## 10.4 Task Subtasks

Task có thể:

* Không có Subtask.
* Có một Subtask.
* Có nhiều Subtask.

Mỗi Subtask có:

* Subtask ID.
* Task ID.
* Title.
* Completed Status.

Quan hệ:

> Task 1 → N TaskSubtask

Khi Task bị xóa, Subtasks liên quan phải được xử lý theo quy tắc Cascade Delete hoặc cơ chế tương đương.

## 10.5 Task Completion

Task có thể được hoàn thành từ:

* To-do List.
* Task Detail.
* Notification.
* Lock Screen nếu Android cho phép.

Sau khi hoàn thành:

* Task Status cập nhật.
* Home Dashboard cập nhật.
* Notification cập nhật.
* Lock Screen cập nhật.

---

# FR-08 – NOTES

## 11.1 Description

Notes cho phép User tạo, chỉnh sửa, tìm kiếm, ghim và xóa ghi chú.

## 11.2 Note Fields

* Note ID.
* Title.
* Content.
* Category.
* Color.
* Pin Status.
* Created Date.
* Updated Date.

## 11.3 Main Flow

1. User mở Notes.
2. User chọn Create Note.
3. User nhập Title.
4. User nhập Content.
5. User chọn Category/Color nếu cần.
6. User có thể Pin.
7. User Save.
8. System lưu Note.

## 11.4 Note Operations

User có thể:

* Create.
* Read.
* Edit.
* Delete.
* Search.
* Pin.
* Unpin.

## 11.5 Quick Note

Quick Note có thể được tạo từ:

* App.
* Notification.
* Lock Screen.
* Shortcut nếu nền tảng hỗ trợ.

Quick Note phải sử dụng **cùng Note Database** với Notes thông thường.

Không được tạo một nguồn dữ liệu riêng cho Quick Note.

---

# FR-09 – THEME MANAGEMENT

## 12.1 Description

Theme quản lý giao diện tổng thể của Super Calendar.

Theme áp dụng cho toàn bộ ứng dụng.

## 12.2 Theme Properties

Theme có thể kiểm soát:

* Primary Color.
* Secondary Color.
* Background.
* Typography.
* Font.
* Border Radius.
* Shadow.
* Component Style.
* Spacing.
* Icon Style.
* Dark Mode.
* Layout Style.

## 12.3 Default Theme

Free User được sử dụng Default Theme.

Default Theme phải theo định hướng:

* Minimal.
* Clean.
* Simple.
* Easy to read.
* Không quá nhiều hiệu ứng.

## 12.4 VIP Theme

VIP có thể mở khóa:

* Custom Color.
* Custom Font.
* Advanced Typography.
* Advanced Layout.
* Theme Builder.
* Premium Components.

## 12.5 Theme and Widget Template Separation

Theme và Widget Template là hai đối tượng độc lập.

Ví dụ:

> Theme = Pastel Pink
> Widget Template = Minimal To-do

Thay đổi Widget Template không được thay đổi Theme toàn ứng dụng.

---

# FR-10 – WIDGET TEMPLATE

## 13.1 Description

Widget Template quyết định cách một nhóm dữ liệu được trình bày trên giao diện.

Template không thay đổi giao diện tổng thể của ứng dụng.

## 13.2 Supported Widget Types

Template có thể áp dụng cho:

* To-do.
* Habit.
* Week.
* Month.
* Goal.
* Notes.
* Các Widget khác trong tương lai.

## 13.3 Template Classification

Template được chia thành:

* Free.
* Premium/VIP.

Prototype có thể cung cấp khoảng 3 Free Templates.

## 13.4 Apply Template

1. User mở Template Center.
2. User chọn Template.
3. System hiển thị Preview.
4. Nếu Free:

   * User chọn Apply.
5. Nếu Premium:

   * System kiểm tra quyền.
   * Nếu User không có quyền, hiển thị VIP Prompt.
6. Nếu User đủ quyền:

   * Template được Apply.
7. Home/Widget cập nhật giao diện.

---

# FR-11 – VIP MANAGEMENT

## 14.1 Description

VIP là hệ thống kiểm soát quyền truy cập các chức năng Premium.

VIP không phải một module nghiệp vụ độc lập mà là cơ chế Access Control được các chức năng khác sử dụng.

## 14.2 Free Features

Free User được sử dụng:

* Calendar.
* Event.
* Basic Goal.
* Habit.
* To-do.
* Notes.
* Default Theme.
* Free Widget Templates.
* Basic Notifications.

## 14.3 VIP Features

VIP User được mở khóa:

* Premium Widget Templates.
* Custom Colors.
* Custom Fonts.
* Advanced Layout.
* Theme Builder.
* Premium Widget Customization.
* Premium Lock Screen Customization nếu được triển khai.

## 14.4 VIP Check

Khi User truy cập Premium Feature:

1. System kiểm tra VIP Status.
2. Nếu Free:

   * Hiển thị Lock.
   * Hiển thị VIP Prompt.
3. Nếu VIP:

   * Cho phép sử dụng.

## 14.5 Mock Purchase

Prototype có thể mô phỏng:

> Free → Upgrade → Mock Payment → VIP

Không triển khai:

* Real Payment.
* Banking.
* Credit Card.
* Payment Gateway.

---

# FR-12 – NOTIFICATION

## 15.1 Description

Notification cung cấp các lời nhắc liên quan đến Event, Task, Habit và Goal.

## 15.2 Supported Reminder

* Event Reminder.
* Task Reminder.
* Habit Reminder.
* Goal Reminder.

## 15.3 Main Flow

1. User tạo Reminder.
2. System lưu Reminder Configuration.
3. System lập lịch Notification.
4. Đến thời gian:

   * System gửi Notification.
5. User chọn Notification.
6. System mở dữ liệu liên quan.

## 15.4 Task Notification Actions

Nếu Android hỗ trợ:

* Done.
* Snooze.

Khi User chọn Done:

> Notification → Task ID → Task Status = Completed

Không tạo Task mới từ Notification.

## 15.5 Data Consistency

Nếu dữ liệu nguồn:

* Deleted → Reminder bị hủy.
* Rescheduled → Reminder được cập nhật.
* Completed → Reminder được xử lý tương ứng.

---

# FR-13 – LOCK SCREEN

## 16.1 Description

Lock Screen đưa thông tin quan trọng của User đến khu vực có thể xem nhanh mà không cần mở toàn bộ ứng dụng.

Prototype ưu tiên Android.

## 16.2 Schedule

Schedule hiển thị lịch trình.

Schedule phải:

* Read-only.
* Không Edit trực tiếp.
* Không Delete trực tiếp.
* Không Drag.
* Không Reschedule.

Khi User chọn Schedule, ứng dụng có thể được mở để thao tác chi tiết.

## 16.3 To-do

Lock Screen có thể hiển thị:

* Task chưa hoàn thành.
* Task quan trọng.
* Task sắp đến hạn.

Nếu Android cho phép, User có thể Complete Task trực tiếp.

Dữ liệu phải được cập nhật vào Task Database.

## 16.4 Quick Note

User có thể tạo Quick Note từ:

* Lock Screen.
* Notification.
* Shortcut.

Quick Note phải được lưu vào Note Database.

## 16.5 Security

System không được lưu hoặc yêu cầu:

* Device PIN.
* Device Password.
* Biometric credentials.

Nếu cần xác thực, ứng dụng sử dụng cơ chế bảo mật của hệ điều hành.

## 16.6 Native Android

Các chức năng liên quan đến:

* Lock Screen.
* Notification.
* System Calendar.
* Shortcut/System Integration.

có thể yêu cầu Android Native/Kotlin.

---

# FR-14 – SETTINGS

## 17.1 Description

Settings cho phép User quản lý cấu hình ứng dụng.

Settings được chia thành các nhóm.

## 17.2 Account

* Account.
* Profile.
* VIP Status.

## 17.3 Appearance

* Theme.
* Custom Color.
* Widget Style.
* Font.
* Layout.
* Dark Mode.

## 17.4 Calendar

* Default Calendar.
* Week Starts On.
* Calendar Permission.
* Default Event Duration.

## 17.5 Tasks

* Default Priority.
* Completed Task Behavior.
* Default Reminder.

## 17.6 Notifications

* Enable/Disable Notifications.
* Event Reminder.
* Task Reminder.
* Habit Reminder.
* Goal Reminder.

## 17.7 Language & Region

* Language.
* Date Format.
* Time Format.
* First Day of Week.

## 17.8 Lock Screen

* Enable/Disable.
* Schedule Visibility.
* To-do Visibility.
* Quick Note.

## 17.9 Help

* User Guide.
* FAQ.
* About.

## 17.10 Application

* Version.
* Privacy.
* Terms.

---

# FR-15 – TEMPLATE MARKETPLACE

## 18.1 Description

Template Marketplace là khu vực cho phép User khám phá, Preview, sở hữu và sử dụng các Widget Template được cung cấp trên hệ thống.

Marketplace mở rộng Template Center và cho phép hệ thống cung cấp thêm Template ngoài các Template mặc định.

Marketplace tập trung vào **Widget Template**, không bán Theme toàn ứng dụng.

## 18.2 Marketplace Content

Marketplace có thể chứa:

* Free Templates.
* Premium Templates.
* Official Templates.
* User-created Templates.

## 18.3 Browse Marketplace

1. User mở Marketplace.
2. System hiển thị Template.
3. User có thể Search.
4. User có thể Filter.
5. User chọn Template.
6. System mở Template Detail.

## 18.4 Template Detail

Template Detail phải hiển thị:

* Template Name.
* Preview.
* Description.
* Category.
* Widget Type.
* Creator/Provider.
* Free/Premium Status.
* Price nếu có.
* Apply/Purchase action.

## 18.5 Free Template

Nếu Template Free:

1. User Preview.
2. User chọn Apply.
3. System áp dụng Template.
4. Không cần Purchase.

## 18.6 Premium Template

Nếu Template Premium:

1. User mở Template.
2. System kiểm tra VIP Status/Ownership.
3. Nếu chưa có quyền:

   * Hiển thị Premium Information.
   * Hiển thị Purchase/Unlock.
4. User chọn Purchase.
5. Prototype thực hiện Mock Purchase.
6. System tạo Purchase Record.
7. Template được đánh dấu Owned.
8. User có thể Apply.

## 18.7 Template Ownership

Ownership và Apply là hai trạng thái khác nhau.

Ví dụ:

User có thể:

> Own 5 Templates
> Apply 1 Template

User không bị giới hạn chỉ một Template đã sở hữu.

## 18.8 Search

Marketplace hỗ trợ tìm kiếm theo:

* Template Name.
* Keyword.
* Category.

## 18.9 Filter

Marketplace có thể hỗ trợ:

* Free.
* Premium.
* Category.
* New.
* Popular.

Các tiêu chí New/Popular chỉ cần triển khai khi Prototype có dữ liệu phù hợp.

---

# FR-16 – TEMPLATE CREATOR & PUBLISH

## 19.1 Description

VIP User có thể tạo Widget Template của riêng mình và publish lên Marketplace.

Trong Prototype, đây là chức năng mô phỏng hệ sinh thái Template.

## 19.2 Create Template

1. VIP User mở Template Creator.
2. System kiểm tra VIP Status.
3. User chọn Widget Type.
4. User thiết kế Layout.
5. User cấu hình thành phần.
6. User Preview.
7. User Save.
8. System lưu Template ở trạng thái Draft.

## 19.3 Template Draft

Draft chưa được hiển thị công khai trên Marketplace.

User có thể:

* Edit.
* Preview.
* Delete.
* Publish.

## 19.4 Publish Template

1. User chọn Publish.
2. System kiểm tra Template.
3. System yêu cầu:

   * Name.
   * Description.
   * Category.
   * Preview.
   * Template Type.
4. User xác nhận.
5. System chuyển Status:

> Draft → Published

6. Template có thể xuất hiện trên Marketplace.

## 19.5 Template Status

Template có thể có:

* Draft.
* Published.
* Unpublished.
* Owned.
* Applied.

## 19.6 Prototype Limitation

Prototype không yêu cầu:

* Creator Verification.
* Content Moderation phức tạp.
* Real Marketplace Backend.
* Revenue Sharing.
* Creator Payout.
* Real Payment.

Các chức năng trên thuộc Production/Future Development.

---

# 5. ENTITY AND DATA REQUIREMENTS

## 5.1 User

| Field       | Description    |
| ----------- | -------------- |
| UserID      | Định danh User |
| DisplayName | Tên hiển thị   |
| Email       | Email nếu có   |
| Avatar      | Avatar nếu có  |
| VIPStatus   | Trạng thái VIP |
| CreatedAt   | Ngày tạo       |
| UpdatedAt   | Ngày cập nhật  |

---

## 5.2 Event

| Field         | Description           |
| ------------- | --------------------- |
| EventID       | ID                    |
| Title         | Tên Event             |
| Description   | Mô tả                 |
| StartDateTime | Bắt đầu               |
| EndDateTime   | Kết thúc              |
| Location      | Địa điểm              |
| Category      | Danh mục              |
| Color         | Màu                   |
| Reminder      | Nhắc nhở              |
| Repeat        | Lặp                   |
| Source        | Local/System Calendar |
| CreatedAt     | Ngày tạo              |
| UpdatedAt     | Ngày cập nhật         |

---

## 5.3 Task

| Field         | Description       |
| ------------- | ----------------- |
| TaskID        | ID                |
| Title         | Tên Task          |
| Description   | Mô tả             |
| DueDate       | Hạn ngày          |
| DueTime       | Hạn giờ           |
| Priority      | Mức độ ưu tiên    |
| Reminder      | Nhắc nhở          |
| Repeat        | Lặp               |
| Category      | Danh mục          |
| Color         | Màu               |
| Note          | Ghi chú           |
| Attachment    | File đính kèm     |
| Tags          | Tag               |
| EstimatedTime | Thời gian dự kiến |
| Completed     | Trạng thái        |
| CreatedAt     | Ngày tạo          |
| UpdatedAt     | Ngày cập nhật     |

---

## 5.4 TaskSubtask

| Field     | Description |
| --------- | ----------- |
| SubtaskID | ID          |
| TaskID    | Task cha    |
| Title     | Nội dung    |
| Completed | Trạng thái  |

Quan hệ:

> Task 1 — N TaskSubtask

---

## 5.5 Goal

| Field       | Description    |
| ----------- | -------------- |
| GoalID      | ID             |
| Type        | Weekly/Monthly |
| Title       | Tên            |
| Description | Mô tả          |
| StartDate   | Bắt đầu        |
| EndDate     | Kết thúc       |
| Progress    | Tiến độ        |
| Completed   | Hoàn thành     |
| CreatedAt   | Ngày tạo       |
| UpdatedAt   | Ngày cập nhật  |

---

## 5.6 Habit

| Field      | Description   |
| ---------- | ------------- |
| HabitID    | ID            |
| Title      | Tên           |
| StartDate  | Ngày bắt đầu  |
| EndDate    | Ngày kết thúc |
| RepeatRule | Quy tắc lặp   |
| CreatedAt  | Ngày tạo      |
| UpdatedAt  | Ngày cập nhật |

---

## 5.7 HabitOccurrence

| Field        | Description    |
| ------------ | -------------- |
| OccurrenceID | ID             |
| HabitID      | Habit Rule     |
| Date         | Ngày           |
| Status       | Trạng thái     |
| OverrideData | Thay đổi riêng |

Quan hệ:

> Habit 1 — N HabitOccurrence

---

## 5.8 Note

| Field     | Description   |
| --------- | ------------- |
| NoteID    | ID            |
| Title     | Tiêu đề       |
| Content   | Nội dung      |
| Category  | Danh mục      |
| Color     | Màu           |
| IsPinned  | Ghim          |
| CreatedAt | Ngày tạo      |
| UpdatedAt | Ngày cập nhật |

---

## 5.9 Theme

| Field          | Description |
| -------------- | ----------- |
| ThemeID        | ID          |
| Name           | Tên         |
| Colors         | Màu         |
| Typography     | Font/Text   |
| Background     | Background  |
| Radius         | Bo góc      |
| Shadow         | Shadow      |
| ComponentStyle | Style       |
| IsVIP          | Premium     |

---

## 5.10 WidgetTemplate

| Field         | Description         |
| ------------- | ------------------- |
| TemplateID    | ID                  |
| Name          | Tên                 |
| Description   | Mô tả               |
| WidgetType    | Loại Widget         |
| Category      | Danh mục            |
| Configuration | Cấu hình Layout     |
| Preview       | Preview             |
| CreatorID     | Người tạo           |
| Price         | Giá                 |
| IsPremium     | Premium             |
| Status        | Draft/Published/... |
| CreatedAt     | Ngày tạo            |
| UpdatedAt     | Ngày cập nhật       |

---

## 5.11 Purchase

| Field        | Description |
| ------------ | ----------- |
| PurchaseID   | ID          |
| UserID       | Người mua   |
| TemplateID   | Template    |
| PurchaseDate | Ngày mua    |
| Price        | Giá         |
| Status       | Trạng thái  |

Trong Prototype, Purchase chỉ phục vụ Mock Purchase.

---

# 6. FUNCTIONAL RELATIONSHIP

Các chức năng phải liên kết với nhau theo mô hình:

```text
                    SUPER CALENDAR
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
      PLAN               DO            PERSONALIZE
        │                 │                 │
    Calendar           To-do          Theme / Template
        │                 │                 │
 ┌──────┼──────┐          │          ┌──────┴──────┐
 │      │      │          │          │             │
Event  Goal   Habit      Task      Template      VIP
 │             │          │          │             │
 │             │       Subtask       │         Access Control
 │             │                     │
 └─────────────┴──────────┬──────────┘
                          │
                    Home Dashboard
                          │
              ┌───────────┴───────────┐
              │                       │
         Notification             Lock Screen
              │                       │
              └───────────┬───────────┘
                          │
                         Notes
```

Marketplace nằm trong hệ sinh thái Template:

```text
Home
 │
 └── Template Center
       │
       ├── My Templates
       │
       ├── Free Templates
       │
       └── Marketplace
              │
              ├── Browse
              ├── Search
              ├── Preview
              ├── Purchase
              ├── Apply
              │
              └── Create/Publish
                    │
                  VIP
```

---

# 7. BUSINESS RULES

## BR-01 – Event and Task

Event và Task là hai loại dữ liệu khác nhau.

* Event = hoạt động có lịch.
* Task = công việc cần hoàn thành.

Không được sử dụng Task thay thế cho Event hoặc ngược lại.

## BR-02 – Habit

Habit Rule và Habit Occurrence phải được quản lý riêng.

Chỉnh sửa một occurrence không được thay đổi toàn bộ Habit Rule.

## BR-03 – Goal

Weekly Goal và Monthly Goal phải được phân biệt bằng Goal Type.

## BR-04 – Theme

Theme điều khiển giao diện tổng thể.

## BR-05 – Widget Template

Widget Template chỉ điều khiển layout/presentation của một Widget.

## BR-06 – VIP

VIP quyết định quyền truy cập chức năng Premium.

## BR-07 – Marketplace

Marketplace quản lý việc khám phá và sở hữu Template.

## BR-08 – Ownership

Sở hữu Template không đồng nghĩa với đang Apply Template.

## BR-09 – Notification

Notification chỉ tham chiếu dữ liệu nguồn và không tạo dữ liệu nghiệp vụ trùng lặp.

## BR-10 – Lock Screen

Lock Screen không được trở thành một nguồn dữ liệu độc lập.

## BR-11 – Quick Note

Quick Note sử dụng cùng Note Database với Notes.

## BR-12 – Data Persistence

Dữ liệu sau khi Save phải được lưu và khôi phục sau khi ứng dụng được mở lại.

---

# 8. NON-FUNCTIONAL REQUIREMENTS

## 8.1 Usability

Giao diện phải:

* Đơn giản.
* Tối giản.
* Dễ hiểu.
* Dễ thao tác.
* Không có quá nhiều menu.
* Không yêu cầu người dùng nhập quá nhiều thông tin khi thực hiện thao tác nhanh.

## 8.2 Performance

Các thao tác cơ bản phải phản hồi nhanh:

* Create.
* Edit.
* Delete.
* Complete.
* Search.
* Apply Template.

## 8.3 Reliability

System phải hạn chế mất dữ liệu khi:

* Đóng ứng dụng.
* Chuyển màn hình.
* Khởi động lại ứng dụng.

## 8.4 Maintainability

Code phải được tổ chức để có thể mở rộng:

* Backend.
* Cloud Sync.
* iOS.
* Real Marketplace.
* Real Payment.

trong tương lai.

---

# 9. PROTOTYPE SCOPE

Prototype phải ưu tiên chứng minh các chức năng cốt lõi:

### Core

* Home.
* Calendar.
* Week/Month.
* Event CRUD.
* Goal.
* Habit.
* To-do.
* Task CRUD.
* Task Completion.
* Subtask.
* Notes CRUD.

### Personalization

* Default Theme.
* Theme Change.
* Widget Template.
* Template Center.
* Free Template.
* VIP Template Lock.

### Monetization

* VIP Status.
* Premium Feature Gating.
* Mock Purchase.

### Marketplace

* Marketplace.
* Template Detail.
* Preview.
* Search/Filter cơ bản.
* Mock Purchase.
* Template Ownership.
* Template Apply.
* Template Creator.
* Draft.
* Publish.

### System Integration

* Android Calendar Permission.
* Notification.
* Lock Screen ở mức khả năng của Android Prototype.
* Quick Note.

---

# 10. OUT OF SCOPE

Các chức năng sau không thuộc Prototype:

* Real Backend.
* Real Account Authentication.
* Cloud Sync.
* Real Payment Gateway.
* Credit Card Processing.
* Banking Integration.
* Real Template Marketplace Backend.
* Creator Revenue Sharing.
* Creator Payout.
* Complex Moderation.
* Review/Rating System.
* Social Network.
* Chat.
* Team Collaboration.
* Public Social Sharing.
* AI Assistant.
* Advanced Third-party Calendar Synchronization.

Các chức năng này có thể được phát triển trong phiên bản Production.

---

# 11. ACCEPTANCE CRITERIA

## 11.1 Navigation

* Có đúng 5 tab chính.
* Home là màn hình mặc định.
* User chuyển đổi giữa các tab thành công.

## 11.2 Home

* Hiển thị Dashboard.
* Hiển thị dữ liệu hiện tại.
* Có Template Center.
* Không tạo dữ liệu trùng lặp.

## 11.3 Calendar

* Có Week View.
* Có Month View.
* Có nút +.
* Có thể chọn trực tiếp ngày.
* Có Event.
* Có Goal.
* Có Habit.

## 11.4 Event

* Create.
* Read.
* Edit.
* Delete.
* Reminder.
* Repeat.
* System Calendar Permission.

## 11.5 Goal

* Weekly Goal.
* Monthly Goal.
* Progress.
* Complete.
* Edit/Delete.

## 11.6 Habit

* Create Habit.
* Repeat.
* Occurrence.
* Complete.
* Edit/Delete individual occurrence.
* Edit/Delete entire Habit Rule.

## 11.7 To-do

* Quick Add.
* Auto Focus.
* Checkbox.
* Edit.
* Task Detail.
* Subtask.
* Reminder.
* Complete/Delete.

## 11.8 Notes

* Create.
* Edit.
* Delete.
* Search.
* Pin.
* Quick Note.

## 11.9 Theme

* Default Theme.
* VIP Theme features.
* Theme applies consistently.

## 11.10 Template

* Free Template.
* Premium Template.
* Preview.
* Apply.
* Lock.

## 11.11 VIP

* Free/VIP Status.
* Premium Access Control.
* Mock Purchase.

## 11.12 Notification

* Event Reminder.
* Task Reminder.
* Habit Reminder.
* Goal Reminder.
* Task Done/Snooze where supported.

## 11.13 Lock Screen

* Schedule display.
* Read-only Schedule.
* To-do display.
* Task completion where supported.
* Quick Note where supported.

## 11.14 Marketplace

* Browse.
* Search.
* Filter.
* Template Detail.
* Preview.
* Free Template Apply.
* Premium Template Purchase.
* Ownership.
* Apply.

## 11.15 Template Creator

* VIP check.
* Create Template.
* Edit Template.
* Preview.
* Save Draft.
* Publish.

---

# 12. REQUIREMENT TRACEABILITY

Functional Requirements phải được sử dụng làm cơ sở cho toàn bộ quá trình phát triển:

```text
SYSTEM SPECIFICATION
        ↓
FUNCTIONAL REQUIREMENTS
        ↓
USE CASE
        ↓
UI/UX DESIGN
        ↓
DATABASE DESIGN
        ↓
CLASS / ARCHITECTURE DESIGN
        ↓
FLUTTER IMPLEMENTATION
        ↓
ANDROID NATIVE INTEGRATION
        ↓
TEST CASE
        ↓
ACCEPTANCE TEST
```

Mỗi chức năng được triển khai phải có FR tương ứng.

Mỗi FR phải có thể truy ngược về System Specification.

Mỗi Test Case phải xác định được FR mà Test Case đó kiểm tra.

---

# 13. FUNCTIONAL REQUIREMENTS SUMMARY

| ID    | Functional Requirement     | Main Responsibility           |
| ----- | -------------------------- | ----------------------------- |
| FR-01 | Account Management         | Quản lý tài khoản             |
| FR-02 | Home                       | Dashboard và Template Center  |
| FR-03 | Calendar                   | Week/Month và điều hướng lịch |
| FR-04 | Event Management           | Quản lý lịch trình            |
| FR-05 | Goal Management            | Weekly/Monthly Goal           |
| FR-06 | Habit Management           | Habit Rule/Occurrence         |
| FR-07 | To-do List                 | Task/Subtask                  |
| FR-08 | Notes                      | Quản lý ghi chú               |
| FR-09 | Theme Management           | Giao diện tổng thể            |
| FR-10 | Widget Template            | Layout Widget                 |
| FR-11 | VIP Management             | Premium Access Control        |
| FR-12 | Notification               | Reminder                      |
| FR-13 | Lock Screen                | Schedule/To-do/Quick Note     |
| FR-14 | Settings                   | Cấu hình hệ thống             |
| FR-15 | Template Marketplace       | Khám phá/sở hữu Template      |
| FR-16 | Template Creator & Publish | Tạo và Publish Template       |

---

# 14. FINAL SYSTEM FUNCTIONAL STRUCTURE

Super Calendar được tổ chức thành các nhóm chức năng:

### CORE PRODUCT

**Home → Calendar → To-do → Notes → Settings**

### CALENDAR MANAGEMENT

**Event → Goal → Habit**

### PRODUCTIVITY

**Task → Subtask → Reminder**

### PERSONALIZATION

**Theme → Widget Template**

### PREMIUM

**VIP → Premium Feature Access**

### TEMPLATE ECOSYSTEM

**Template Center → Marketplace → Template Detail → Purchase → Ownership → Apply**

**VIP User → Template Creator → Draft → Publish → Marketplace**

### SYSTEM INTEGRATION

**Notification → Event/Task/Habit/Goal**

**Lock Screen → Schedule/Task/Quick Note**

**System Calendar → Event**

---

# 15. CONCLUSION

Functional Requirements của Super Calendar được xây dựng theo hướng một ứng dụng quản lý năng suất cá nhân có cấu trúc đơn giản ở giao diện nhưng có khả năng mở rộng về chức năng.

Hệ thống tập trung vào:

> **PLAN → DO → PERSONALIZE → SEE IT FIRST**

Trong đó:

* Calendar quản lý lịch trình.
* Event quản lý hoạt động theo thời gian.
* Goal quản lý mục tiêu.
* Habit quản lý hành vi lặp lại.
* To-do quản lý công việc.
* Notes quản lý ghi chú.
* Theme cá nhân hóa giao diện.
* Widget Template cá nhân hóa cách hiển thị.
* VIP kiểm soát chức năng Premium.
* Marketplace mở rộng hệ sinh thái Template.
* Notification nhắc nhở người dùng.
* Lock Screen đưa thông tin quan trọng đến vị trí dễ nhìn thấy.
* Settings quản lý cấu hình ứng dụng.

Prototype ưu tiên Local Database và Flutter, đồng thời sử dụng Android Native khi cần tích hợp với System Calendar, Notification và Lock Screen.

Cấu trúc FR này là cơ sở để chuyển sang các tài liệu tiếp theo gồm:

**Use Case Specification → UI/UX Specification → Database Specification → Class Diagram → Architecture → Implementation → Test Case.**

**END OF FUNCTIONAL REQUIREMENTS SPECIFICATION – SUPER CALENDAR v1.0**
