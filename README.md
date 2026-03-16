Nike Shoes Shop App - Đồ Án Di Động Đa Nền Tảng
Ứng dụng mua sắm Nike được xây dựng bằng Flutter và Firebase, tích hợp Chatbot AI thông minh hỗ trợ tư vấn bán hàng.
 Giới thiệu
Đây là đồ án môn học Di động đa nền tảng, tập trung vào việc xây dựng một ứng dụng thương mại điện tử hoàn chỉnh với trải nghiệm người dùng hiện đại và tích hợp công nghệ AI.
 Công nghệ sử dụng
Frontend: Flutter (Dart)
Backend: Firebase (Authentication, Firestore Database)
AI: Google Generative AI (Gemini)
 Các tính năng chính
1. Quản lý Tài khoản (Authentication)
Đăng ký & Đăng nhập: Hỗ trợ đăng ký tài khoản mới với Email, Mật khẩu và Ảnh đại diện.
Phân quyền: Hệ thống tự động nhận diện và chuyển hướng người dùng vào giao diện Khách hàng hoặc Admin dựa trên vai trò (role).
Bảo mật: Mật khẩu được mã hóa và quản lý bởi Firebase Authentication.
2. Trang chủ (Home - Dành cho Khách hàng)
Danh sách sản phẩm: Hiển thị danh sách giày từ Firestore với giao diện lưới (Grid) đẹp mắt.
Lọc danh mục: Thanh chọn danh mục (Jordan, Running, Lifestyle...) với hiệu ứng chuyển đổi mượt mà.
Banner động: Banner quảng cáo thay đổi tự động theo danh mục được chọn.
Tìm kiếm: Tích hợp công cụ tìm kiếm sản phẩm theo tên.
Badge Giỏ hàng: Hiển thị số lượng sản phẩm trong giỏ hàng ngay trên icon.
3. Chi tiết Sản phẩm (Product Detail)
Hiệu ứng Hero: Animation chuyển cảnh mượt mà khi bấm vào sản phẩm.
Chọn Size: Giao diện chọn kích cỡ giày trực quan.
Thêm vào giỏ: Tính năng thêm sản phẩm vào giỏ hàng với hiệu ứng bay vào giỏ.
Yêu thích: Thả tim để lưu sản phẩm vào danh sách yêu thích.
4. Giỏ hàng & Thanh toán (Cart & Checkout)
Quản lý giỏ hàng: Xem danh sách, xóa sản phẩm, tự động tính tổng tiền.
Thanh toán: Form nhập thông tin giao hàng chi tiết.
Voucher: Hỗ trợ mã giảm giá (Ví dụ: nhập CR7 giảm 11%).
Xác nhận đơn hàng: Lưu đơn hàng vào hệ thống và làm trống giỏ hàng.
5. Quản lý Đơn hàng (Order History)
Lịch sử mua hàng: Xem lại danh sách các đơn hàng đã đặt.
Trạng thái đơn hàng: Theo dõi trạng thái (Đang xử lý, Đang giao, Giao thành công).
Tự động cập nhật: Đơn hàng sẽ tự động chuyển sang trạng thái "Giao thành công" sau 24 giờ (tính năng giả lập).
6. Chatbot AI Thông minh (Trợ lý ảo)
Tư vấn sản phẩm: Bot tự động học dữ liệu từ kho hàng để trả lời về giá, tên giày.
Tư vấn Size: Hỗ trợ nhập số đo chân (cm) để quy đổi ra size giày chuẩn Nike.
Thông tin shop: Trả lời các câu hỏi về địa chỉ, chính sách đổi trả, ship hàng.
Chế độ Hybrid: Tự động chuyển đổi giữa AI và Kịch bản (Rule-based) nếu mất kết nối mạng, đảm bảo luôn phản hồi khách hàng.
7. Admin Panel (Quản trị viên)
Quản lý sản phẩm: Xem, Thêm mới, Sửa, Xóa sản phẩm (CRUD).
Quản lý đơn hàng: Xem danh sách tất cả đơn hàng của khách, chi tiết từng đơn.
 Cấu trúc Cơ sở dữ liệu (Firebase Firestore)
Dữ liệu được tổ chức thành các Collections chính sau:
1. Collection users (Người dùng)
Lưu trữ thông tin hồ sơ và dữ liệu cá nhân của từng người dùng.
uid (Document ID): Mã định danh duy nhất từ Authentication.
username: Tên hiển thị.
email: Email đăng nhập.
img: URL hoặc Base64 ảnh đại diện.
role: Vai trò (user hoặc admin).
createdAt: Thời gian tạo tài khoản.
Sub-collection cart: Giỏ hàng của người dùng.
productId_size (Doc ID): ID sản phẩm + Size.
name, price, img, size, quantity.
Sub-collection wishlist: Danh sách yêu thích.
productId (Doc ID): ID sản phẩm.
likedAt: Thời gian thích.
2. Collection products (Sản phẩm)
Lưu trữ danh sách toàn bộ giày đang bán.
Auto-ID: Mã sản phẩm tự sinh.
name: Tên giày (Ví dụ: Nike Air Jordan 1).
price: Giá bán (Ví dụ: 3.500.000 đ).
img: URL ảnh sản phẩm hoặc chuỗi Base64.
category: Danh mục (Jordan, Running, Lifestyle...).
description: Mô tả chi tiết sản phẩm.
createAt: Thời gian tạo.
3. Collection orders (Đơn hàng)
Lưu trữ lịch sử đặt hàng của tất cả người dùng.
Auto-ID: Mã đơn hàng.
userId: ID của người đặt hàng.
status: Trạng thái đơn (pending, shipping, completed, cancelled).
createdAt: Thời gian đặt hàng.
userInfo (Map): Thông tin giao hàng.
name, phone, address, province.
paymentDetails (Map): Chi tiết thanh toán.
totalOriginal, discount, totalPaid, voucher, method.
items (Array): Danh sách sản phẩm trong đơn.
Mỗi phần tử chứa: name, price, img, size, quantity.
 Cài đặt & Chạy ứng dụng
Clone dự án:

Cài đặt thư viện:



Cấu hình Firebase:
Tạo dự án trên Firebase Console.
Thêm file google-services.json (Android) hoặc GoogleService-Info.plist (iOS) vào thư mục tương ứng.
Bật Authentication (Email/Password) và Firestore Database.
Chạy ứng dụng:



👨‍💻 Tác giả
Họ và tên: HUỲNH VĂN HẠ HUYÊN
Lớp: 22SE1B
Mã sinh viên: 22IT.B096



