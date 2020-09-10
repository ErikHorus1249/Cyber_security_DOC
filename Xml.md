![XML là gì? Tổng hợp các cách để mở file XML ít người biết](https://www.semtek.com.vn/wp-content/uploads/2019/11/3-4.jpg)

## 1. XML là gì?

XML là viết tắt của từ **eXtensible Markup Language**, hay còn gọi là ngôn ngữ đánh dấu mở rộng do  [W3C](http://www.w3.org/ "W3C")  đề nghị với mục đích tạo ra các ngôn ngữ đánh dấu khác. Đây là một tập hợp con đơn giản có thể mô tả nhiều loại dữ liệu khác nhau nên rất hữu ích trong việc chia sẻ dữ liệu giữa các hệ thống. Ví dụ khi bạn xây dựng một ứng dụng bằng C# và một ứng dụng bằng PHP thì hai ngôn ngữ này không thể hiểu nhau, vì vậy ta sẽ sử dụng XML để trao đổi dữ liệu.

Tất cả những đặc tả dữ liệu XML đều phải tuân theo quy luật và cú pháp của nó nên hầu như các file XML đều rất nghiêm khắc trong việc biên dịch. Tuy nhiên công nghệ này cần phải được xem xét bởi vì trong quá trình thao tác và truyền dữ liệu nó có tỉ lệ sai sót lên tới 5% - 7%. Con số này không cao nhưng cũng rất đáng để cân nhức khi sử dụng.

Điển hình nhất là ngôn ngữ đánh dấu siêu văn bản  [HTML](https://freetuts.net/html-la-gi-bo-cuc-html-cua-mot-trang-web-420.html "HTML là gì") sử dụng cú pháp của XML để tạo nên và nó có các bộ phần tử và thuộc tính không mềm dẻo nên chỉ có tác dụng trong việc trình bày dữ liệu trên trình duyệt Browser.

Để rõ hơn về khái niệm XML là gì thì bạn nên đọc ở bài viết trên  [Wiki](https://vi.wikipedia.org/wiki/XML "Wiki")  nhé.

## 2. Cú pháp của tài liệu XML

Nếu bạn đã học qua HTML rồi thì rất dễ dàng hiểu cú pháp của XML bởi vì HTML được xây dựng dựa trên cú pháp của XML.

File XML sẽ có phần mở rộng là  `.xml`. Tuy nhiên bạn hoàn toàn có thể sử dụng ngôn ngữ lập trình để thay đổi phần mở rộng cho nó (_sẽ tìm hiểu sau_).

### Cú pháp của thẻ XML:

XML được xây dựng dựa vào cấu trúc NODE lồng nhau, mỗi node sẽ có một thẻ mở và một thẻ đóng như sau:

1

    <nodename>nội dung</nodename>

Trong đó:

-   `<nodename>`  là thẻ mở, tên của thẻ này do bạn tự định nghĩa.
-   `</nodename>`  là thẻ đóng, tên của thẻ này phải trùng với tên của thẻ mở.
-   `content`  là nội dung của thẻ này

Ví dụ mình lưu trữ domain của mình thì cấu trúc như sau:

VD :

    <domain>freetuts.net</domain>

Bạn hoàn toàn có thể bổ sung các thuộc tính vào các thẻ XML bằng cách sử dụng cú pháp sau:

VD

    <nodename ten_thuoc_tinh="giá trị">content</nodename>

Ví dụ bạn lưu trữ thông tin domain và chủ sở hữu của nó thì có thể lưu như sau:

1

    <domain owner = "Nguyễn Văn Cường" email ="thehalfheart@gmail.com">freetuts.net</domain>

### Khai báo Header (Chỉ thị xử lý):

Trên đầu mỗi file XML bạn phải khai báo một thẻ để thông báo version XML đang sử dụng (_thường là version 1.0_), và còn có thể chứa các thông tin về mã hóa ký tự hoặc các phụ thuộc bên ngoài khác (_sẽ tìm hiểu sau_). Giá trị của encoding (_kiểu mã hóa ký tự_) thuộc một trong các định dạng sau: UTF-8, UTF-16, ISO-10646-UCS-2, ISO-10646-UCS-4, ISO-8859-1 to ISO-8859-9, ISO-2022-JP, Shift_JIS, EUC-JP.

Cú pháp của thẻ chỉ thị xử lý như sau:

Lời khuyên là bạn nên đặt tên thẻ là một danh từ, nên đặt tên bằng tiếng Anh vì nó đơn giản và là ngôn ngữ chuẩn trên thế giới.

# Bài 02: Cấu trúc cây trong XML

Một tài liệu XML được tạo bởi các thẻ (_XML element_) và chúng có thể được tổ chức theo một cấu trúc cây thư mục, điều này còn có thể gọi là Nested Elements trong XML. Vậy cách tổ chức như thế nào để có thể lưu trữ được dữ liệu trong thế giới thực? Chúng ta cùng tìm hiểu vấn đề này nhé.

## 1. Cấu trúc cây trong XML

Như ở bài tìm hiểu  [XML là gì](https://freetuts.net/xml-la-gi-cu-phap-can-ban-cua-xml-513.html "XML là gì") mình có giới thiệu sơ lược về cách tạo thẻ Root Node (_phần 2_). Từ ví dụ đó ta có thể rút ra kết luận rằng các thẻ XML có thể lồng lên nhau, thẻ ngoài ta gọi là thẻ cha và các thể bên trong ta gọi là thẻ con.

**Ví dụ**: Sơ đồ cấu trúc cây tổ chức lưu trữ thông tin nhân viên trong một công ty

![xml dom model jpg](https://freetuts.net/upload/tut_post/images/2015/11/28/514/xml-dom-model.jpg)

Với sơ đồ này ta sẽ thực hiện từng bước tạo tài liệu XML như sau:

**Bước 1**: Thẻ ngoài cùng root là  `company`

    <?xml version="1.0" encoding="UTF-8"?>
    <company>
         
    </company>

**Bước 2**: Bên trong thẻ `company` có hai thẻ `employee`.

    <?xml version="1.0" encoding="UTF-8"?>
    <company>
        <employee>
            
        </employee>
        <employee>
             
        </employee>
    </company>
**Bước 3**: Bên trong thẻ  `employee`  đầu tên gồm ba thẻ  `firstname`,  `lastname`  và  `contactno`  tương đương với ba giá trị như sau:

-   `firstname`  => Tanmay
-   `lastname`  => Patil
-   `contactno`  => 123456789

> <?xml version="1.0" encoding="UTF-8"?> <company>
>     <employee>
>         <firstname>
>             Tanmay
>         </firstname>
>         <lastname>
>             Patil
>         </lastname>
>         <contactno>
>             123456789
>         </contactno>
>     </employee>
>     <employee>
>          
>     </employee> </company>

**Bước 4**: Tương tự cho nội dung bên trong thẻ `employee` thứ hai.

> <?xml version="1.0" encoding="UTF-8"?> <company>
>     <employee>
>         <firstname>
>             Tanmay
>         </firstname>
>         <lastname>
>             Patil
>         </lastname>
>         <contactno>
>             123456789
>         </contactno>
>     </employee>
>     <employee>
>         <firstname>
>             Taniya
>         </firstname>
>         <lastname>
>             Mishra
>         </lastname>
>         <contactno>
>             123456789
>         </contactno>
>     </employee> </company>
Như vậy là ta đã đặc tả xong cấu trúc XML lưu trữ dữ liệu ứng dụng quản lý nhân viên trong công ty.

Câu hỏi đặt ra là nếu ta lưu trữ thêm một nhân viên nữa thì phải làm thế nào? Rất đơn giản ta chỉ việc tạo thêm một thẻ  `employee`  và thêm thông tin là được.

    <?xml version="1.0" encoding="UTF-8"?>
    <company>
        <employee>
            <firstname>
                Tanmay
            </firstname>
            <lastname>
                Patil
            </lastname>
            <contactno>
                123456789
            </contactno>
        </employee>
        <employee>
            <firstname>
                Taniya
            </firstname>
            <lastname>
                Mishra
            </lastname>
            <contactno>
                123456789
            </contactno>
        </employee>
        <employee>
            <firstname>
                Cuong
            </firstname>
            <lastname>
                Nguyen
            </lastname>
            <contactno>
                0979306603
            </contactno>
        </employee>
    </company>
## 2 Cấu trúc cây nhiều cấp trong XML

Lấy ví dụ ở phần thứ nhất và bổ sung thêm yêu cầu sau: Môi nhân viên lưu trữ thêm  **danh sách người thân của nhân viên đó** (_chỉ cần lưu trữ tên, mối quan hệ_).

Trước tiên ta cần tổ chức XML lưu trữ người thân đã. Giả sử mình sẽ lưu trữ dạng sau:

    <family>
        <person>
            <name>Nguyễn Sơn</name>
            <relationship>Cha</relationship>
        </person>
        <person>
            <name>Lê Thị Sửu</name>
            <relationship>Mẹ</relationship>
        </person>
        <person>
            <name>Nguyễn Văn Trường</name>
            <relationship>Anh trai</relationship>
        </person>
    </family>
Ráp vào bài toán thứ nhất ta sẽ có cấu trúc XML sau:

    <?xml version="1.0" encoding="UTF-8"?>
    <company>
        <employee>
            <firstname>
                Tanmay
            </firstname>
            <lastname>
                Patil
            </lastname>
            <contactno>
                123456789
            </contactno>
            <family>
                <person>
                    <name>Nguyễn Sơn</name>
                    <relationship>Cha</relationship>
                </person>
                <person>
                    <name>Lê Thị Sửu</name>
                    <relationship>Mẹ</relationship>
                </person>
                <person>
                    <name>Nguyễn Văn Trường</name>
                    <relationship>Anh trai</relationship>
                </person>
            </family>
        </employee>
    </company>
Như vậy mỗi lần thêm nhân viên thì chỉ việc bổ sung thẻ `employee` và muốn thêm người thân thì chỉ việc bổ sung thẻ `person`.

# Bài 03: Tìm hiểu Element trong XML

XML Element chúng ta đã sử dụng rất nhiều ở các ví dụ trước. Tuy nhiên ta chưa bàn tới vấn đề cú pháp và quy tắc chúng khi đặt tên cho nó, vì vậy trong bài này mình sẽ trình bày tất cả các vấn đề liên quan đến XML Elements.

## 1. Element trong XML là gì?

Như ta biết một tài liệu XML sẽ chưa nhiều thẻ XML, các thẻ XML bao gồm tất cả mọi thứ từ thẻ khai báo trên header cho đến thẻ Root, các thẻ con, ... cho đến thẻ cuối cùng trong tài liệu.

Một thẻ XML dùng để chứa dư liệu dạng đơn giản (_number, string_) cho đến phức tạp (_thẻ XML chứa thẻ XML_).

Ví dụ ta cần viết một file XML để lưu trữ danh sách sinh viên gồm các thông tin:

-   Tên sinh viên (`tensv`)
-   Năm sinh (`namsinh`)
-   Giới tính (`gioitinh`)

Lúc này ta sẽ có ba thẻ chứa dữ liệu đơn giản đó là  `tensv`,  `namsinh`  và  `gioitinh`. Có một thẻ chứa dữ liệu phức tạp đó là thẻ  `sinhvien`. Nhưng chưa dừng lại ở đó, như ở bài tìm hiểu  [xml là gì](https://freetuts.net/xml-la-gi-cu-phap-can-ban-cua-xml-513.html "xml là gì") chúng ta cần xác định thêm một thẻ Root nữa. Phân tích kỹ thì ta thấy mỗi sinh viên sẽ được mô tả bởi thẻ sinhvien và tài liệu sẽ chứa nhiều sinh viên, vì vậy mình sẽ đặt tên cho thẻ root là  `ds-sinhvien`.

Như vậy dưới đây là  [cấu cây XML](https://freetuts.net/cau-truc-cay-trong-xml-514.html "cấu cây XML")  của chúng ta.

    <?xml version="1.0" encoding="UTF-8"?>
    <ds-sinhvien>
        <sinhvien>
            <tensv>[Data]</tensv>
            <namsinh>[Data]</namsinh>
            <gioitinh>[Data]</gioitinh>
        </sinhvien>
    </ds-sinhvien>
## 2. Thẻ XML rỗng và rút gọn thẻ đóng

Một thẻ XML có thể chứa dữ liệu hoặc không chứa dữ liệu cũng được. Nếu không có dữ liệu thì ta để trống.

    <?xml version="1.0" encoding="UTF-8"?>
    <ds-sinhvien>
        <sinhvien></sinhvien>
    </ds-sinhvien>
Trường hợp này bạn có thể rút gọn thẻ đóng bằng cách sau:

    <?xml version="1.0" encoding="UTF-8"?>
    <ds-sinhvien>
        <sinhvien/>
    </ds-sinhvien>
Nghĩa là ta sẽ đóng ngay thẻ mở luôn.

Một ví dụ điển hình của trường hợp thẻ XML rỗng như sau: Giả sử cần bổ sung thêm một thuộc tính mô tả (`mota`) dùng để mô tả sinh viên ở ví dụ trên. Lúc này cấu trúc XML sẽ như sau:

    <?xml version="1.0" encoding="UTF-8"?>
    <ds-sinhvien>
        <sinhvien>
            <tensv>[Data]</tensv>
            <namsinh>[Data]</namsinh>
            <gioitinh>[Data]</gioitinh>
            <mota>[Data]</mota>
        </sinhvien>
    </ds-sinhvien>
Bây giờ mình sẽ lưu hai sinh viên thì cấu trúc XML sẽ như sau:

    <?xml version="1.0" encoding="UTF-8"?>
    <ds-sinhvien>
        <sinhvien>
            <tensv>Nguyễn Văn Cường</tensv>
            <namsinh>1990</namsinh>
            <gioitinh>Nam</gioitinh>
            <mota>Sinh viên đẹp zai thích viết tutorials.</mota>
        </sinhvien>
        <sinhvien>
            <tensv>Vũ Thị Thu Tình</tensv>
            <namsinh>1992</namsinh>
            <gioitinh>Nữ</gioitinh>
            <mota></mota>
        </sinhvien>
    </ds-sinhvien>
Như vậy ở sinh viên thứ hai phần mô tả bị trống do không có mô tả cho sinh viên đó. Lúc này ta có thể ghi gọn cho thẻ `mota` như sau:

    <sinhvien>
        <tensv>Vũ Thị Thu Tình</tensv>
        <namsinh>1992</namsinh>
        <gioitinh>Nữ</gioitinh>
        <mota/>
    </sinhvien>

## 3. Một số quy tắc liên quan đến XML Element

Có một số quy tắc và điển hình nhất là các quy tắc sau.

**Đặt tên thẻ**:

-   Tên thẻ phải bắt đầu là một chữ cái hoặc ký tự gạch dưới.
-   Tên thẻ không được bắt đầu bằng XML (hoặc Xml, xMl, xmL) vì nó giống với thẻ khai báo header.
-   Tên thẻ không được chứa khoảng trắng.
-   Tên thẻ có thể chứa chữ cái, chữ số, dấu gạch dưới, dấu gạch ngang, dấu chấm và dấu hai chấm.

**Cấu trúc thẻ**:

-   Mỗi thẻ mở đều phải có thẻ đóng và chúng phải tuân theo đúng thứ tự.
-   Bạn có thể dùng thẻ đóng rút gọn nếu như thẻ đó rỗng

**Naming styles**:

Không có một chuẩn đặt tên thẻ nào trong XML cả nhưng người ta đề xuất ra một số cách đặt tên như sau:

## Quy tắc đặt tên biến 

| Style  |  Example |Description   
|---|---|---|---|---|
|Lower case |firstname| Tất cả đều chữ in thường  |   |   |
| Upper case  | FIRSTNAME  | Tất cả đều chữ in hoa  |   |   |
| Underscore  |first_name   | Các từ cách nhau bởi dấu gạch dưới  |Pascal case   | FirstName  |Viết hoa ký tự đầu tiên trong các từ
|Camel case | firstName | Viết hoa ký tự đầu tiên trong từ thứ hai trở đi.

Lời khuyên là bạn nên đặt tên thẻ là một danh từ, nên đặt tên bằng tiếng Anh vì nó đơn giản và là ngôn ngữ chuẩn trên thế giới.

### Tham khảo :
- [freetuts](https://freetuts.net/)



