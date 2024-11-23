<h2>Lời mở đầu.</h2>
<p>Xin chào bạn tôi là một lần trình viên trẻ khi tôi viết thư viện này tôi đang làm ở ASFY Tech, thư viện này sinh ra nhằm giúp mọi người ở công ty viết code javascript đơn giản hơn. Tôi chỉ có một mong muốn là mọi người có thể sử dụng thư viện này và phát triển nó lên cho hợp với thời đại mới của công ty.</p>

<h2>I. Bắt đầu với Helpers.</h2>
<p>
    - Logic hoạt động: Helpers được chia thành 2 phần chính là layout và form, layout có tác dụng hiển thị dữ liệu sau
    khi
    gọi api, form có tác dụng thực hiện công việc gửi dữ liệu lên backend.

</p>
- Tải thư viện: Khi bạn tiếp cận với một base code mới do quản lý cấp việc đầu tiên của bạn là chạy câu lệnh sau npm
install helpers-vu_diep@latest mục đích nhằm cập nhật phiên bản mới nhất về. Với các phiên bản ^1.1.7 thì chỉ sử dụng
với base laravel.

<h4>Hướng đẫn cài đặt:</h4>

- Đối với 1 file view có blade thì bạn cần tạo 1 file js ở trong thư mục resources/js/script.... để viết js riêng.
- VD: Trong hình tôi có tạo 1 thư mục bên trong script/tai-san/tai-san-co-dinh.js. Tiếp theo ở file view tôi tạo
section('script') và link sang file tai-san-co-dinh.js với type="module"
![alt text](assets/images/image.png)
- Lưu ý: Các bạn nên tạo như trong hình để tránh bị lỗi nhé !

<h2>II. Tổng quan về các file trong thư viện</h2>

1. common.js file chứa các function dùng chung cho các dự án trước đó.
2. coreFunctions.js file chứa các function sử dụng cho thư viện
3. core.js file chứa các class dùng chung cho toàn bộ thư viện
4. form.js file chứa các thao tác với form
5. layout.js file chứa các class thao tác với layout

<h2>III. Hướng đẫn sử dụng các class trong core.js</h2>

<h4>1. RequestServerHelpers class thao tác với server</h4>

- Khi bạn khởi tạo class bạn phải truyền vào 1 api để có thể sử dụng các phương tức trong đó.
VD: Bây giờ hãy quay lại file tai-san-co-dinh.js bạn mới tạo ở trên rồi khởi tạo nó nhé. Lưu ý hãy import
RequestServerHelpers với đường đẫn tuyệt đối vào trước khi khởi tạo nhé.
![alt text](assets/images/image-1.png)
<h5>- Giới thiệu các thuộc tính:</h5>

<p>
<ul>
    <li>route: Là api bạn truyền vào được sử dụng để giao tiếp với backend</li>
    <li>params: Params truyền vào khi bạn gửi yêu cầu</li>
    <li>statusMessage: Xác định xem có cần thông báo xong sau khi gửi request server không. Nếu bạn để false thì cả
        thông báo
        lỗi và thông báo thành công sẽ không được hiển thị.</li>
    <li> headers: Sử dụng khi bạn gọi các phương thức gửi dữ liệu, thông thường tôi sẽ sử dụng nó để gửi formData</li>
</ul>
</p>

<h5>- Giới thiệu các phương thức</h5>
<b>1.1 Phương thức getData:</b> Phương thức có tác dụng lấy ra dữ liệu và trả về dữ liệu sau khi gửi request. Lưu ý: Hàm
getData sẽ trả về Promise vậy nên bạn phải sử dụng async, await thì mới lấy được dữ liệu nhé.
<h5>- Giới thiệu các thuộc tính:</h5>

* api: Tham số này giúp bạn linh hoạt gọi các api khác mà không phải khởi tạo lại class. Nếu bạn không truyền thì nó mặc
định sẽ lấy ra api bạn truyền vào khi khởi tạo class.
![alt text](assets/images/image-2.png)

<b>1.2 Phương thức postData:</b> Phương thức có tác dụng gửi dữ liệu với method post và trả về object sau khi gửi request.

<h5>- Giới thiệu các thuộc tính:</h5>

* data: Dữ liệu gửi đi
* debug: Thực hiện debug khi bạn test
* api: Tham số này giúp bạn linh hoạt gọi các api khác mà không phải khởi tạo lại class. Nếu bạn không truyền thì nó mặc
định sẽ lấy ra api bạn truyền vào khi khởi tạo class.
![alt text](assets/images/image-3.png)

<b>1.3 Phương thức putData:</b> Phương thức có tác dụng gửi dữ liệu với method put và trả về object sau khi gửi request.

<h5>- Giới thiệu các thuộc tính:</h5>

* data: Dữ liệu gửi đi
* debug: Thực hiện debug khi bạn test
* api: Tham số này giúp bạn linh hoạt gọi các api khác mà không phải khởi tạo lại class. Nếu bạn không truyền thì nó mặc
định sẽ lấy ra api bạn truyền vào khi khởi tạo class.
* Bạn đang thắc mắc là đối với phương thức put thì id sẽ để ở đâu đúng không ? Đừng vội tôi sẽ chỉ cho bạn thấy cách tôi
đưa id vào với method put ngay đây.
![alt text](assets/images/image-4.png)

<h4>2. Class EventHelpers: Class này có tác dụng lắng nghe sự kiện của 1 thẻ.</h4>

<h5>- Giới thiệu các thuộc tính:</h5>

* scope: Phạm vi mà các dom được phép lắng nghe. Giả sử bạn chỉ muốn lắng nghe sự kiện của 1 form. Thì bạn truyền dom
của form đó khi khởi tạo class như vậy các sự kiện sẽ chỉ được lắng nghe trong form đó. Nếu bạn không truyền scope thì
nó sẽ mặc định là document.

<b>2.1 Phương thức addEvent:</b> Lắng nghe các sự sự kiện của 1 thẻ và thực hiện gọi hàm callback.

<h5>- Giới thiệu các thuộc tính:</h5>

* dom: id hoặc class của thẻ cần lắng nghe
* eventType: Loại event
* callback: Function thực hiện công việc nào đó

<b>2.2 Các event hiện có:</b> input, click, change, addItem, search, submit: Các phương thức này đều có điểm chung là nhận vào
1 dom và lắng nghe các sự kiện sau đó gọi 1 hàm callback để thực hiện công việc người dùng muốn.

Lưu ý: Trong trường hợp thẻ bạn cần lắng nghe chính là scope thì cứ mạnh dạng truyền vào dom của
scope nó vẫn sẽ hiểu và lắng nghe.
![alt text](assets/images/image-5.png)

<h4>3. Class URLHelpers: Class này làm việc với url</h4>

<h5>- Giới thiệu các thuộc tính:</h5>

* url: Là url bạn muốn sử dụng, mặc định là url hiện tại

<b>3.1 getLastPathSegment: </b> <span>Hàm này có tác dụng lấy ra phần cuối cùng trên url thường dùng cho việc lấy ra id.
    ![alt text](assets/images/image-6.png)
</span>

<b>3.2 getParams: </b> <span>Hàm có tác dụng lấy params trên url</span>
<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>key: Nhận vào key của param nếu bạn chỉ cần lấy 1 trường cụ thế. Nếu bạn muốn lấy tất cả param có trên url thì không cần quan tâm đến trường này</li>
</ul>

![alt text](assets/images/image-7.png)

<b>3.3 removeParam: </b> <span>Hàm có tác dụng xóa params trên url</span>
<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>key: Nhận vào key của param nếu bạn chỉ cần xóa 1 trường cụ thế. Nếu bạn muốn xóa tất cả param có trên url thì không cần quan tâm đến trường này</li>
</ul>

![alt text](assets/images/image-8.png)

<b>3.4 removeParamsExcept: </b> <span>Hàm có tác dụng xóa params trên url nhưng sẽ không xóa params bạn muốn</span>
<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>keysToKeep: Nhận vào array các key mà bạn không muốn xóa trên url</li>
</ul>

![alt text](assets/images/image-9.png)

<b>3.5 addParamsToURL: </b> <span>Hàm có tác dụng thêm params trên url </span>
<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>params: Nhận vào array các key mà bạn muốn thêm trên url</li>
</ul>

![alt text](assets/images/image-10.png)


<h4>4. Class ConfirmHelpers: Class này làm việc với confirm khi bạn muốn hỏi người dùng làm việc gì đó</h4>

<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>
        config: Cấu hình khi hiển thị confirm
        <ul>
            <li>text: Đoạn text hiển thị</li>
            <li>btnText: Nội dung nút xác nhận</li>
            <li>btnBg: Màu nút</li>
            <li>title: Tiêu đề của nút</li>
            <li>sucess: Hàm được sử dụng sau khi người dùng đồng ý</li>
        </ul>
    </li>
</ul>

<b>4.1 loading: </b> <span>Thực hiện loading ở nút button </span>
<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>type: Trạng thái bật hay tắt loading. False: Tắt, True: Bật</li>
</ul>
<p><b>4.2 hide: </b> <span>Thực hiện ẩn confirm </span></p>
<p><b>4.3 show: </b> <span>Thực hiện show confirm </span></p>
<b>Ví dụ: </b>

![alt text](assets/images/image-11.png)

<h4>4. Class FileHelpers: Class này làm việc thao tác với việc xử lý file</h4>
<b>4.1 exportExcel và exportPDF: </b> <span>Hàm có tác dụng tải file PDF và Excel </span>
<h5>- Giới thiệu các thuộc tính:</h5>
<ul>
    <li>api: api xuất file</li>
    <li>name: Tên file</li>
    <li>dom: Id hoặc class thẻ lắng nghe sự kiện. Khi bạn không truyền tham số cho thuộc tính này thì nó tự động tải file</li>
    <li>params: params đi kèm</li>
    <li>getParams: Lấy params động rồi đi kèm</li>
</ul>

![alt text](assets/images/image-12.png)

<h2>VI. Hướng đẫn sử dụng các class trong layout.js</h2>
<h4>1. PaginationHelpers class thao tác với việc phân trang. Khi bạn khởi tạo thì nó sẽ tự động phân trang cho bạn.</h4>
<h5>- Giới thiệu các thuộc tính:</h5>

<ul>
    <li>data: Object trả về từ backend có chứa phân trang</li>
    <li>renderUI: Function gọi ra giao diện</li>
    <li>pagination: Id thẻ html nơi đổ dữ liệu phân trang</li>
</ul>

![alt text](assets/images/image-13.png)

<h4>2. BaseLayoutHelpers class này là cơ sở cho việc phát triển các layout.  </h4>
<p>Lưu ý:  Khi bạn sử dụng class này nó sẽ tự động khởi tạo phân trang cho bạn và trong dom bạn phải có thẻ chứ id paginations, trong trường hợp bạn không muốn phân trang thì sét thuộc tính pagination = false.</p>
<h5>- Giới thiệu các thuộc tính:</h5>

<ul>
    <li>api: Api gọi lấy dữ liệu</li>
    <li>template: Bản thiết kế cho giao diện</li>
    <li>total: Trường cần tính tổng. Trong trường hợp bạn có nhiều trường cần tính tổng thì truyền theo dạng mảng</li>
    <li>defaultParams: Dữ liệu mặc định khi gọi api lấy layout</li>
</ul>

<b>2.1 renderUI: </b> <span>Hàm có tác dụng đưa dom ra màn hình </span>
![alt text](assets/images/image-14.png)