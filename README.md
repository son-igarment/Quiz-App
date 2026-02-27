# Quiz App

Ứng dụng Quiz App được phát triển bởi **Phạm Lê Ngọc Sơn** — một ứng dụng Android cho phép người dùng tham gia các bài kiểm tra trắc nghiệm với nhiều chủ đề đa dạng.

## Giới thiệu

Quiz App là một ứng dụng di động Android được xây dựng bằng ngôn ngữ Kotlin, cung cấp trải nghiệm làm bài quiz tương tác với giao diện Material Design hiện đại. Ứng dụng hỗ trợ nhiều danh mục câu hỏi khác nhau, hiệu ứng âm thanh phản hồi, và hiển thị kết quả chi tiết sau mỗi bài kiểm tra.

## Tính năng chính

### Màn hình giới thiệu (Onboarding)
- Hiển thị khi người dùng mở ứng dụng lần đầu tiên
- ViewPager với 2 trang giới thiệu tính năng ứng dụng
- Nút "Next" và "Get Started" để di chuyển giữa các trang
- Tự động lưu trạng thái đã xem bằng SharedPreferences

### Nhập tên người dùng
- Yêu cầu người dùng nhập tên trước khi bắt đầu làm quiz
- Kiểm tra dữ liệu đầu vào hợp lệ
- Truyền tên người dùng qua các màn hình

### Chọn danh mục câu hỏi
- 10 danh mục đa dạng:
  - Entertainment: Books
  - Entertainment: Film
  - Entertainment: Music
  - Sports
  - Art
  - Politics
  - Mythology
  - Entertainment: Japanese Anime & Manga
  - History
  - Science
- Giao diện RecyclerView với các thẻ danh mục có màu sắc riêng biệt
- Dialog xác nhận khi chọn danh mục

### Làm bài quiz
- 10 câu hỏi trắc nghiệm mỗi bài
- 4 lựa chọn trả lời cho mỗi câu
- Thanh tiến trình (ProgressBar) với hiệu ứng animation
- Phản hồi trực quan:
  - Màu xanh lá cho câu trả lời đúng
  - Màu đỏ cho câu trả lời sai
  - Màu xám cho các lựa chọn không được chọn
- Hiệu ứng âm thanh khi trả lời đúng/sai
- Các nút Submit / Next / Finish
- Vô hiệu hóa các lựa chọn sau khi đã chọn đáp án

### Màn hình kết quả
- Hiển thị tên người dùng
- Hiển thị điểm số: "You scored X out of 10"
- Nút Finish để quay lại màn hình chính

## Công nghệ sử dụng

| Thành phần | Chi tiết |
|---|---|
| **Ngôn ngữ** | Kotlin 1.7.10 |
| **Nền tảng** | Android (Native) |
| **Min SDK** | 21 (Android 5.0 Lollipop) |
| **Target SDK** | 32 (Android 12L) |
| **Build System** | Gradle 7.2.2 |
| **UI Framework** | AndroidX, Material Components 1.6.1 |
| **Tải hình ảnh** | Glide 4.13.2 |
| **Mạng** | Volley 1.2.1 |
| **Điều hướng** | AndroidX Navigation Component 2.5.2 |
| **Bố cục** | ConstraintLayout 2.1.4, ViewBinding |
| **Kiểm thử** | JUnit 4.13.2, Espresso 3.4.0 |

## Cấu trúc dự án

```
Quiz-App/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/phamlengocson/quizapp/
│   │   │   │   ├── AdapterViewPager.kt        # Adapter cho ViewPager onboarding
│   │   │   │   ├── CategoriesAdapter.kt       # Adapter RecyclerView danh mục
│   │   │   │   ├── CategoryView.kt            # Data class danh mục
│   │   │   │   ├── GetAllQuestions.kt          # Nguồn dữ liệu câu hỏi
│   │   │   │   ├── MainActivity.kt            # Màn hình nhập tên
│   │   │   │   ├── OnBoardIngItems.kt         # Data class onboarding
│   │   │   │   ├── OnBoardingScreen.kt        # Màn hình giới thiệu
│   │   │   │   ├── Questions.kt               # Data class câu hỏi
│   │   │   │   ├── QuestionsActivity.kt       # Màn hình làm bài quiz
│   │   │   │   ├── QuizCategories.kt          # Màn hình chọn danh mục
│   │   │   │   ├── ResultActivity.kt          # Màn hình kết quả
│   │   │   │   └── Splash_Screen.kt           # Màn hình khởi động
│   │   │   ├── res/
│   │   │   │   ├── drawable/                  # Hình ảnh và drawable resources
│   │   │   │   ├── layout/                    # Các file XML bố cục
│   │   │   │   ├── navigation/                # Đồ thị điều hướng
│   │   │   │   ├── raw/                       # Âm thanh (right.wav, w.mp3)
│   │   │   │   └── values/                    # Chuỗi, màu sắc, chủ đề
│   │   │   └── AndroidManifest.xml
│   │   ├── androidTest/                       # Kiểm thử trên thiết bị
│   │   └── test/                              # Kiểm thử đơn vị
│   └── build.gradle
├── build.gradle
├── settings.gradle
├── gradle.properties
└── README.md
```

## Hướng dẫn cài đặt

### Yêu cầu hệ thống
- Android Studio Arctic Fox (2021.1) trở lên
- JDK 8 trở lên
- Android SDK 32
- Thiết bị Android hoặc máy ảo chạy Android 5.0 (API 21) trở lên

### Các bước cài đặt

1. Clone repository:
```bash
git clone https://github.com/sonpln/Quiz-App.git
```

2. Mở dự án trong Android Studio:
   - Chọn **File > Open**
   - Điều hướng đến thư mục dự án vừa clone
   - Chọn thư mục `Quiz-App` và nhấn **OK**

3. Đồng bộ Gradle:
   - Android Studio sẽ tự động đồng bộ các dependency
   - Nếu không, chọn **File > Sync Project with Gradle Files**

4. Chạy ứng dụng:
   - Kết nối thiết bị Android qua USB hoặc khởi động Android Emulator
   - Nhấn nút **Run** (Shift+F10)
   - Chọn thiết bị mục tiêu và đợi ứng dụng được cài đặt

## Luồng hoạt động của ứng dụng

```
Màn hình khởi động (1 giây)
    ├── Lần đầu sử dụng → Màn hình giới thiệu → Màn hình chính
    └── Đã sử dụng trước → Màn hình chính
                                ↓
                        Nhập tên người dùng
                                ↓
                        Chọn danh mục câu hỏi
                                ↓
                        Làm bài quiz (10 câu hỏi)
                                ↓
                        Hiển thị kết quả
                                ↓
                        Quay lại màn hình chính
```

## Thông tin kỹ thuật

- **Kiến trúc:** Activity-based architecture với ViewBinding
- **Lưu trữ cục bộ:** SharedPreferences (lưu trạng thái lần đầu sử dụng)
- **Hiệu ứng chuyển màn hình:** Fade animation giữa các Activity
- **Định hướng màn hình:** Khóa chế độ dọc cho màn hình câu hỏi
- **Giao diện:** Fullscreen theme với Material Design

## Tác giả

**Phạm Lê Ngọc Sơn**

- Application ID: `com.phamlengocson.quizapp`

## Phiên bản

- **Mã phiên bản:** 1
- **Tên phiên bản:** 1.0

## Giấy phép

```
MIT License

Copyright (c) 2026 Phạm Lê Ngọc Sơn

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
