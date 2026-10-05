# SUPER CALENDAR

## SYSTEM SPECIFICATION

**Project Name:** Super Calendar
**Document Type:** System Specification
**Version:** 1.0
**Platform:** Mobile Application
**Development Framework:** Flutter
**Target Platforms:** Android / iOS

---

# 1. DOCUMENT PURPOSE

Tài liệu này định nghĩa đặc tả tổng thể của hệ thống **Super Calendar** trước khi tiến hành đặc tả chi tiết từng chức năng.

Tài liệu nhằm xác định:

* Mục đích của hệ thống.
* Phạm vi của hệ thống.
* Đối tượng sử dụng.
* Các module chính.
* Mối quan hệ giữa các module.
* Nguyên tắc hoạt động của hệ thống.
* Yêu cầu tổng quát về dữ liệu.
* Yêu cầu tổng quát về giao diện.
* Yêu cầu tổng quát về kiến trúc.
* Các giới hạn và định hướng phát triển.

Các yêu cầu chức năng chi tiết sẽ được mô tả trong tài liệu **Functional Specification** riêng.

---

# 2. SYSTEM OVERVIEW

## 2.1. System Introduction

**Super Calendar** là ứng dụng quản lý thời gian và năng suất cá nhân trên thiết bị di động.

Hệ thống tích hợp các chức năng:

* Calendar.
* Event.
* To-do.
* Goal.
* Habit.
* Notes.
* Dashboard.
* Theme.
* Widget Template.
* VIP.
* Notification.
* Lock Screen / Quick Note.
* Settings.

Mục tiêu của hệ thống là cung cấp một không gian thống nhất để người dùng có thể:

> **Plan → Organize → Track → Review**

tức là:

> Lập kế hoạch → Tổ chức → Theo dõi → Đánh giá.

---

# 3. SYSTEM OBJECTIVES

Super Calendar được xây dựng với các mục tiêu chính:

### 3.1. Time Management

Cho phép người dùng quản lý lịch trình và sự kiện theo ngày, tuần và tháng.

### 3.2. Task Management

Cho phép người dùng quản lý các công việc cần thực hiện.

### 3.3. Goal Management

Cho phép người dùng thiết lập và theo dõi mục tiêu theo tuần và tháng.

### 3.4. Habit Tracking

Cho phép người dùng xây dựng và theo dõi các thói quen lặp lại.

### 3.5. Note Management

Cho phép người dùng lưu trữ các ghi chú cá nhân và tạo ghi chú nhanh.

### 3.6. Personalization

Cho phép người dùng tùy chỉnh giao diện thông qua Theme và Widget Template.

### 3.7. Quick Access

Cho phép người dùng truy cập các thông tin quan trọng và tạo Quick Note mà không cần mở đầy đủ ứng dụng.

---

# 4. SYSTEM SCOPE

## 4.1. In Scope

Phiên bản hệ thống bao gồm:

### Core Functions

* Calendar.
* Event.
* To-do.
* Notes.
* Goal.
* Habit.

### Supporting Functions

* Home Dashboard.
* Notification.
* Settings.

### Personalization

* Theme.
* Widget Template.
* VIP.

### Quick Access

* Lock Screen.
* Quick Note.

---

## 4.2. Out of Scope

Các chức năng sau không thuộc phạm vi bắt buộc của phiên bản đầu tiên:

* Social network.
* Chat.
* Team collaboration.
* Public calendar sharing.
* Online marketplace hoàn chỉnh.
* AI assistant.
* Advanced cloud synchronization.
* Third-party calendar synchronization.

Các chức năng này có thể được xem xét trong các phiên bản tương lai.

---

# 5. TARGET USERS

Hệ thống hướng đến người dùng cá nhân có nhu cầu quản lý:

* Lịch trình.
* Công việc.
* Mục tiêu.
* Thói quen.
* Ghi chú.

Hệ thống có hai cấp độ sử dụng:

```text
                    USER
                     │
            ┌────────┴────────┐
            │                 │
          FREE               VIP
            │                 │
      Basic Features    Premium Features
```

---

# 6. USER TYPES

## 6.1. Free User

Free User được sử dụng các chức năng cơ bản của hệ thống.

Bao gồm:

* Home.
* Calendar.
* Event.
* Basic Goal.
* Basic Habit.
* To-do.
* Notes.
* Basic Theme.
* Free Templates.
* Basic Notifications.
* Basic Settings.

---

## 6.2. VIP User

VIP User có toàn bộ quyền của Free User và thêm các tính năng Premium.

Bao gồm:

* Premium Templates.
* Custom Color.
* Custom Typography.
* Advanced Layout.
* Theme Builder.
* Premium Widget customization.

VIP không tạo thành một hệ thống riêng mà là **access level** của User.

---

# 7. SYSTEM MODULES

Hệ thống được chia thành các module chính:

```text
                         SUPER CALENDAR
                                │
       ┌──────────┬─────────────┼─────────────┬──────────┐
       │          │             │             │          │
      HOME     CALENDAR       TO-DO         NOTES    SETTINGS
                   │
             ┌─────┼─────┐
             │     │     │
           EVENT  GOAL  HABIT
                         │
                  HABIT OCCURRENCE
```

Các hệ thống hỗ trợ:

```text
Theme
Template
VIP
Notification
Lock Screen
Quick Note
```

---

# 8. APPLICATION NAVIGATION

Ứng dụng sử dụng **Bottom Navigation Bar** làm navigation chính.

Gồm 5 mục:

| Position | Module   | Purpose               |
| -------- | -------- | --------------------- |
| 1        | Home     | Dashboard và Template |
| 2        | Calendar | Event, Goal, Habit    |
| 3        | To-do    | Task Management       |
| 4        | Notes    | Note Management       |
| 5        | Settings | System Configuration  |

Navigation chính:

```text
Home
Calendar
To-do
Notes
Settings
```

Các chức năng như VIP, Template, Theme và Lock Screen không được đưa thành tab chính riêng.

Chúng được truy cập thông qua Home hoặc Settings tùy chức năng.

---

# 9. HOME

Home là màn hình tổng quan của hệ thống.

Home có ba khu vực chính:

```text
HOME
│
├── Welcome
│
├── Today Dashboard
│
└── Template Center
```

---

## 9.1. Welcome

Welcome cung cấp thông tin giới thiệu và hướng dẫn cơ bản cho người dùng.

---

## 9.2. Today Dashboard

Dashboard cung cấp thông tin tổng quan của ngày hiện tại.

Có thể hiển thị:

* Today's Schedule.
* Task Progress.
* Today's Goal.
* Today's Habit.

Dashboard không sở hữu dữ liệu riêng.

Dashboard chỉ tổng hợp dữ liệu từ các module tương ứng.

---

## 9.3. Template Center

Template Center cho phép người dùng:

* Xem Template.
* Xem Preview.
* Chọn Template.
* Sử dụng Free Template.
* Xem Premium Template.

Template được phân loại:

```text
FREE
VIP
```

---

# 10. CALENDAR

Calendar là module trung tâm của hệ thống.

Calendar quản lý:

* Event.
* Goal.
* Habit.

Calendar hỗ trợ hai chế độ:

```text
WEEK
MONTH
```

---

## 10.1. Week View

Week View hiển thị dữ liệu theo tuần.

Người dùng có thể:

* Xem lịch trình.
* Chọn ngày.
* Xem Event.
* Xem Weekly Goal.
* Xem Habit.
* Tạo Event.

---

## 10.2. Month View

Month View hiển thị dữ liệu theo tháng.

Người dùng có thể:

* Xem lịch trình.
* Chọn ngày.
* Xem Event.
* Xem Monthly Goal.
* Xem Habit.
* Tạo Event.

---

# 11. EVENT

Event đại diện cho một lịch trình hoặc sự kiện có thời gian cụ thể.

Event có thể bao gồm:

* Title.
* Date.
* Start Time.
* End Time.
* Color.
* Note.
* Location.
* Reminder.
* Repeat.

Event có thể được tạo bằng:

1. Nút `+`.
2. Chọn trực tiếp một ngày trên Calendar.

Nếu người dùng chọn ngày trước, hệ thống phải sử dụng ngày đó làm ngày mặc định cho Event.

---

# 12. GOAL

Goal đại diện cho mục tiêu người dùng muốn hoàn thành trong một khoảng thời gian.

Hệ thống hỗ trợ:

```text
Weekly Goal
Monthly Goal
```

Weekly Goal thuộc phạm vi một tuần.

Monthly Goal thuộc phạm vi một tháng.

Goal có thể theo dõi:

* Completion.
* Progress.

Ví dụ:

```text
GOALS — OCTOBER

○ Finish Flutter Project
○ Read 2 Books
○ Exercise 12 Times
```

---

# 13. HABIT

Habit đại diện cho một hành vi người dùng muốn duy trì theo quy tắc lặp.

Habit được thiết kế theo mô hình:

```text
Habit Rule
     │
     ├── Occurrence
     ├── Occurrence
     ├── Occurrence
     └── Occurrence
```

Habit Rule định nghĩa:

* Tên Habit.
* Ngày bắt đầu.
* Ngày kết thúc.
* Quy tắc lặp.

Habit Occurrence đại diện cho một lần thực hiện cụ thể.

Ví dụ:

```text
Habit:
Drink Water

Rule:
Every Weekday

Occurrences:
Monday ✓
Tuesday ✓
Wednesday ✓
Thursday ○
Friday ✓
```

Việc chỉnh sửa một Occurrence không làm thay đổi toàn bộ Habit Rule.

---

# 14. TO-DO

To-do là module quản lý công việc.

Một Task có thể tồn tại độc lập hoặc chứa nhiều Subtask.

Mô hình:

```text
Task
 │
 ├── Subtask
 ├── Subtask
 └── Subtask
```

Task có thể có:

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

---

# 15. NOTES

Notes là module quản lý ghi chú cá nhân.

Note có thể bao gồm:

* Title.
* Content.
* Category.
* Color.
* Pin Status.
* Created Date.
* Updated Date.

Hệ thống hỗ trợ:

* Create.
* Edit.
* Delete.
* Search.
* Pin.

---

# 16. QUICK NOTE

Quick Note là phương thức tạo Note nhanh.

Quick Note có thể được truy cập từ:

* Notification.
* Lock Screen.
* Shortcut nếu được hỗ trợ.

Quick Note sử dụng **cùng Note data source** với Notes module.

```text
Quick Note
    │
    ▼
Note
    │
    ▼
Note Data Source
```

Không tạo database riêng cho Quick Note.

---

# 17. THEME

Theme quy định giao diện tổng thể của ứng dụng.

Theme có thể bao gồm:

* Color.
* Typography.
* Background.
* Border Radius.
* Shadow.
* Component Style.

Theme là cấp độ tùy chỉnh **toàn ứng dụng**.

---

# 18. WIDGET TEMPLATE

Widget Template quy định cách một loại nội dung được trình bày.

Ví dụ:

```text
To-do Minimal
│
├── Layout
├── Checkbox Style
├── Typography
├── Spacing
└── Preview
```

Widget Template và Theme là hai đối tượng độc lập.

Ví dụ:

```text
Theme
Pastel Pink

+

Widget Template
To-do Minimal
```

có thể được sử dụng cùng nhau.

---

# 19. VIP

VIP là cơ chế kiểm soát quyền truy cập tính năng Premium.

VIP không phải một module nghiệp vụ độc lập như Calendar hay To-do.

Nó hoạt động như một **Access Control Layer**.

```text
User
 │
 ▼
VIP Status
 │
 ▼
Access Control
 │
 ├── Free Feature
 └── Premium Feature
```

---

# 20. NOTIFICATION

Notification được sử dụng để nhắc người dùng về:

* Event.
* Task.
* Habit.
* Goal.

Notification lấy thông tin từ dữ liệu chính.

Ví dụ:

```text
Event
 │
 ▼
Reminder Rule
 │
 ▼
Notification
```

Notification không tạo một Event hoặc Task mới.

---

# 21. LOCK SCREEN

Lock Screen cung cấp khả năng truy cập nhanh thông tin quan trọng.

Gồm ba khu vực:

```text
LOCK SCREEN
│
├── Schedule
├── To-do
└── Quick Note
```

### Schedule

* Read-only.
* Không Edit.
* Không Delete.
* Tap → mở ứng dụng.

### To-do

* Xem Task.
* Có thể Complete Task nếu hệ điều hành cho phép.

### Quick Note

* Nhập nội dung nhanh.
* Lưu trực tiếp vào Note data source.

---

# 22. SETTINGS

Settings là nơi cấu hình hệ thống.

Các nhóm:

```text
SETTINGS
│
├── Account
├── Appearance
├── Calendar
├── Tasks
├── Notifications
├── Language & Region
├── Lock Screen
├── Help
└── App
```

Settings không quản lý dữ liệu nghiệp vụ chính mà chủ yếu quản lý **system configuration và user preferences**.

---

# 23. DATA DOMAIN

Các domain dữ liệu chính:

```text
User
│
├── Event
├── Task
│    └── TaskSubtask
├── Goal
├── Habit
│    └── HabitOccurrence
├── Note
├── Theme
├── WidgetTemplate
└── Purchase
```

---

# 24. DATA OWNERSHIP

Mỗi loại dữ liệu phải có một nguồn dữ liệu chính.

| Data             | Owner           |
| ---------------- | --------------- |
| Event            | Event           |
| Task             | Task            |
| Goal             | Goal            |
| Habit            | Habit           |
| Habit Occurrence | Habit           |
| Note             | Note            |
| Theme            | Theme           |
| Template         | Widget Template |
| VIP              | User / Purchase |

Các module khác chỉ được **consume/read/update thông qua domain tương ứng**.

Ví dụ:

```text
Event
 ├── Calendar
 ├── Home
 ├── Notification
 └── Lock Screen
```

Không tạo:

```text
CalendarEvent
DashboardEvent
LockScreenEvent
```

cho cùng một dữ liệu.

---

# 25. SYSTEM DATA FLOW

## Event

```text
User
 ↓
Event
 ↓
Event Data
 ├── Calendar
 ├── Home
 ├── Notification
 └── Lock Screen
```

## Task

```text
User
 ↓
Task
 ↓
Task Data
 ├── To-do
 ├── Home
 ├── Notification
 └── Lock Screen
```

## Habit

```text
User
 ↓
Habit Rule
 ↓
Habit Occurrence
 ├── Calendar
 └── Home
```

## Note

```text
User
 ├── Notes
 └── Quick Note
        ↓
      Note Data
```

---

# 26. SYSTEM ARCHITECTURE

Hệ thống được định hướng theo kiến trúc phân tầng:

```text
┌─────────────────────────────┐
│      Presentation Layer      │
│ Flutter Screens / Widgets    │
└──────────────┬──────────────┘
               │
┌──────────────▼──────────────┐
│       Business Layer         │
│ Business Rules / Services    │
└──────────────┬──────────────┘
               │
┌──────────────▼──────────────┐
│          Data Layer          │
│ Repository / Database / API  │
└─────────────────────────────┘
```

Chi tiết implementation có thể được quyết định trong giai đoạn System Design.

---

# 27. GENERAL UI/UX PRINCIPLES

## 27.1. Consistency

Các màn hình phải thống nhất về:

* Typography.
* Color.
* Spacing.
* Icon.
* Button.
* Input.
* Navigation.

## 27.2. Minimal Interaction

Các thao tác thường xuyên phải được thực hiện với số bước tối thiểu.

## 27.3. Visibility

Các chức năng chính phải dễ tìm thấy.

## 27.4. Feedback

Sau các thao tác quan trọng, hệ thống phải cung cấp feedback phù hợp.

Ví dụ:

* Save successful.
* Task completed.
* Event created.
* Note deleted.

---

# 28. GENERAL BUSINESS RULES

### BR-01

Một Event phải có thời gian bắt đầu và kết thúc hợp lệ.

### BR-02

Một Goal phải thuộc một loại:

* Weekly.
* Monthly.

### BR-03

Một Habit gồm một Rule và nhiều Occurrences.

### BR-04

Xóa Habit Occurrence không được xóa Habit Rule.

### BR-05

Task có thể có nhiều Subtasks.

### BR-06

Xóa Task phải xử lý các Subtask liên quan.

### BR-07

VIP Feature chỉ được truy cập bởi User có quyền VIP.

### BR-08

VIP Template phải được đánh dấu rõ ràng là Premium.

### BR-09

Quick Note phải sử dụng cùng nguồn dữ liệu với Note.

### BR-10

Dashboard, Notification và Lock Screen không được tạo bản sao độc lập của dữ liệu nghiệp vụ.

---

# 29. NON-FUNCTIONAL REQUIREMENTS

## Performance

Ứng dụng phải có khả năng phản hồi nhanh đối với các thao tác thông thường.

## Usability

Người dùng mới có thể hiểu được navigation chính mà không cần hướng dẫn phức tạp.

## Reliability

Dữ liệu phải được lưu và truy xuất nhất quán.

## Maintainability

Các module phải được thiết kế độc lập để dễ bảo trì và mở rộng.

## Scalability

Kiến trúc phải cho phép bổ sung các chức năng trong tương lai.

## Security

Dữ liệu người dùng và quyền VIP phải được bảo vệ khỏi truy cập trái phép.

---

# 30. SYSTEM CONSTRAINTS

Hệ thống được phát triển dưới dạng mobile application bằng Flutter.

Các giới hạn phụ thuộc vào:

* Android/iOS API.
* Notification API.
* Lock Screen capabilities.
* Device permissions.
* Local database.
* Network availability nếu sử dụng backend.

Một số tính năng như Lock Screen có thể cần implementation khác nhau giữa Android và iOS.

---

# 31. TECHNOLOGY DIRECTION

Công nghệ dự kiến:

```text
Frontend
    ↓
Flutter / Dart

State Management
    ↓
To be selected during System Design

Local Storage
    ↓
To be selected during System Design

Backend / Cloud
    ↓
Optional / Future Scope
```

Việc lựa chọn package, database và state management cụ thể không được cố định trong System Specification.

Các quyết định này thuộc tài liệu **System Design / Technical Design**.

---

# 32. SYSTEM BOUNDARY

Hệ thống Super Calendar bao gồm:

```text
┌──────────────────────────────────────┐
│           SUPER CALENDAR             │
│                                      │
│ Home                                 │
│ Calendar ── Event                    │
│           ├─ Goal                    │
│           └─ Habit                   │
│                                      │
│ To-do ──── Task ── Subtask           │
│                                      │
│ Notes ──── Note / Quick Note         │
│                                      │
│ Settings                             │
│ Theme                                │
│ Template                             │
│ VIP                                  │
│ Notification                         │
│ Lock Screen                          │
└──────────────────────────────────────┘
```

Các hệ thống bên ngoài có thể tương tác:

```text
Operating System
        │
        ├── Notification
        ├── Lock Screen
        └── Permissions
```

---

# 33. REQUIREMENT DOCUMENT STRUCTURE

Sau khi System Specification này được phê duyệt, các chức năng sẽ được đặc tả chi tiết trong **Functional Specification**.

Cấu trúc tài liệu tiếp theo:

```text
FUNCTIONAL SPECIFICATION

FR-01 Account Management
FR-02 Home
FR-03 Calendar
FR-04 Event
FR-05 Goal
FR-06 Habit
FR-07 To-do
FR-08 Notes
FR-09 Theme
FR-10 Widget Template
FR-11 VIP
FR-12 Notification
FR-13 Lock Screen
FR-14 Settings
```

Mỗi FR sẽ được mô tả theo một format thống nhất:

```text
FR-ID
Function Name

1. Description
2. Actor
3. Preconditions
4. Trigger
5. Main Flow
6. Alternative Flow
7. Exception Flow
8. Input
9. Output
10. Business Rules
11. Data Requirements
12. Acceptance Criteria
```

---

# 34. DEVELOPMENT TRACEABILITY

Sau khi hoàn thành Functional Specification, mỗi requirement sẽ được liên kết theo chuỗi:

```text
System Specification
        ↓
Functional Requirement
        ↓
Use Case
        ↓
UI Design
        ↓
Database / Class Design
        ↓
Implementation
        ↓
Test Case
        ↓
Acceptance
```

Ví dụ:

```text
FR-04 Create Event
       ↓
UC-04 Create Event
       ↓
Create Event Screen
       ↓
Event Entity
       ↓
Flutter Implementation
       ↓
TC-04-01
       ↓
Accepted
```

---

# 35. FUTURE SCOPE

Các chức năng có thể được phát triển sau phiên bản đầu:

* Cloud Synchronization.
* Google Calendar Integration.
* Multi-device Synchronization.
* Productivity Statistics.
* Habit Streak.
* Goal Analytics.
* Pomodoro.
* AI Planning Assistant.
* Smart Schedule.
* Template Marketplace.
* User-generated Templates.
* Social / Collaboration Features.

Các chức năng này **không thuộc phạm vi bắt buộc của phiên bản hiện tại**.

---

# 36. SUMMARY

Super Calendar là hệ thống quản lý năng suất cá nhân tập trung vào:

> **Calendar + Task + Goal + Habit + Note**

với các hệ thống hỗ trợ:

> **Dashboard + Template + Theme + VIP + Notification + Lock Screen**

Hệ thống được xây dựng theo các nguyên tắc:

1. **Modularization** – chia hệ thống thành các module độc lập.
2. **Separation of Concerns** – tách UI, business logic và data.
3. **Single Source of Truth** – mỗi loại dữ liệu có một nguồn chính.
4. **Consistency** – thống nhất giao diện và quy tắc.
5. **Traceability** – requirement có thể truy ngược đến implementation và test.
6. **Scalability** – có khả năng mở rộng trong tương lai.

Đây là **System Specification cấp tổng thể**.

Các chi tiết về từng chức năng sẽ được định nghĩa ở tài liệu **Functional Specification**, bắt đầu từ `FR-01`.
