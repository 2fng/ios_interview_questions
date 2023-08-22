# iOS Interview Questions

iOS interview questions order by timestamp

# 22/08/2023
## Questions

1.  Swift khác Objc như thế nào?
2.  So sánh class với struct, enum
3. ViewController Life cycle
4. So sánh weak, unowned
5. Sqlite, CoreData, Realm
6. Protocol là gì? Cách dùng.
7. GCD, Queue type, NSOperation, async await
8. URLSession vs Alamofire
9. Cách config firebase service,
10. Cách config notification,
11. Git flow, Merge vs Rebase, fix confict
12. Triển khai sprint trong Aglie ntn
13. MVVM, MVP, VIPER -> Mục đích, cách dùng
14.  Denpendency Injection -> Khái niệm

## Anwsers

### Swift khác Objc như thế nào?

| Swift | Objective-C |
| ------ | ------ |
| Ra mắt năm 2014 | Ra mắt năm 1984 |
| Syntax đơn giản, dễ tiếp cận | Syntax phức tạp , ảnh hưởng bởi Smalltalk|
| Static type (Cần define kiểu dữ liệu khi khai báo biến) - Compile time |  Dynamic type - Run time|
| Tối ưu hoá cho các thiết bị phần cứng Appple,  nhanh hơn 2.6 lần so với Objective-C | Ổn định |
| Tự động quản lý bộ nhớ thông qua ARC  | Sử dụng ARC hoặc MRR (Manual Retain-Release -  Lập trình viên để ý khi nào object dùng xong và release nó - Có khả năng gây memory leak cao) |
| Có thể dùng để lập trình app từ iOS 7 trở đi| Support các version cũ hơn |
| Hiện tại Swift là lựa chọn được nhiều người dùng cho các dự án mới hơn Objective-C | Phổ biến hơn trong quá khứ, các dự án cũ | 
|Sử dụng framework UIKit và SwiftUI| Sử dụng UIKit|

<br></br>

### So sánh class với struct, enum
|  | Class | Struct | Enum |
|---|---|---|---|
| **Định nghĩa** | Đối tượng hoá vấn đề  để giải quyết  |  Đối tượng hoá vấn đề  để giải quyết   | Là tập hợp một số phần tử được liệt kê và cố định |
| **Kiểu dữ liệu** | Reference | Value | Value |
| **Nơi lưu dữ liệu** | Heap | Stack | Stack |
| **Có khả năng kế thừa** | Có | Không| Không |
| **Có thể conform Protocol** | Có | Có | Có |
| **Có properties, method** | Có | Có | Có |
| **Có thể Extend** | Có | Có | Có |
| **Có thể hàm deinit** | Có | Không | Không |

<br></br>

### ViewController Life cycle
![ViewController life cycle](https://images.viblo.asia/c7a3245c-6d21-4cc1-b914-d6948a91c6c2.jpg "ViewController life cycle")
1. `loadView()`: Được gọi khi view controller đã được cấp phát bộ nhớ nhưng  view hierrachy  chưa được load vào bộ nhớ
2. `loadViewIfNeeded()`: Được gọi khi view của view controller vẫn chưa được load 
3. `viewDidLoad()`: Được gọi khi cả view controller và view hierrachy của nó đã được load vào bộ nhớ 
4. `viewWillAppear(_:)`: Được gọi trước khi các thành phần của view controller xuất hiện trên màn 
5. `viewWillLayoutSubviews()`: Được gọi trước khi view controller lay out các subviews của view tổng
6. `viewDidLayoutSubviews()`: Được gọi sau khi view controller lay out các subviews của view tổng
7. `viewDidAppear(_:)`: Được gọi khi view controller đã hoàn thành các công việc trên và hiển thị view 
8. `viewWillDisappear(_:)`: Được gọi trước khi các thành phần thuộc view hierrachy của view controller chuẩn bị  deallocate khỏi bộ nhớ

<br></br>

### So sánh weak, unowned
| | `weak` | `unowned` |
|---|---|---|
| **Định nghĩa** | Không tạo liên kết mạnh tới  instance  nó liên kết  (Không tăng reference count) | Không tạo liên kết mạnh tới  instance  nó liên kết  (Không tăng reference count)  |
| **Optional or Non-Optional** | Được định nghĩa là optional | Không phải optional - Không thể nil |
| **Use Case** | Dùng khi thời gian sử dụng của biến ngắn,  hoặc khi chưa chắc chắn biến có thể nil hay không  |Phải đảm bảo biến không thể nil khi define unowned |
| **Điều gì xảy ra khi object được liên kết bị deallocated?** | Tự động set thành nil| App có thể crash khi cố trỏ đến biến unowned khi object liên kết đã bị deallocated |

<br></br>

###  Sqlite, CoreData, Realm

| | SQLite | Core Data | Realm |
|---|---|---|---|
| **Định nghĩa** | SQLite là một thư viện cho phép lưu trữ  local trên thiết bị. Cho phép lập trình viên truy cập, setup   database dễ dàng hơn so với MySQL hay SQL server | Core Data là framework của Apple phát triển, cho phép lưu trữ local và được build trên nền tảng SQLite.| Realm là giải pháp open source  đưa ra giải pháp cho việc lưu dữ liệu local |
| **Platform Support** | Support nhiều nền tảng | Chỉ sản phẩm của Apple | Hỗ trợ cả Android và iOS  |
| **Ease of Use** | Cần viết SQL query để tương tác với database | Tương tác với database thông qua nhiều phương thức  được định nghĩa ở bậc cao chứ không cần  trực tiếp làm việc với SQL  | Tương tự như Core Data|
| **Performance** | Nhanh| Nhanh hơn SQLite với các tác vụ nặng (Do có cơ chế cache)  tuy nhiên tốn nhiều tài nguyên hơn SQLite | Nhanh hơn cả SQLite và Core Data|

<br></br>

### Protocol là gì? Cách dùng.
- Hoạt động như interface/abtract class ở các ngôn ngữ khác
- Định nghĩa các properties và methods mà các class, struct, enum khi conform phải tự khai báo
- Có thể extend
- Có thể được coi như một kiểu dữ liệu
- Có thể được dùng để phục vụ cho các mục đích như  một  interface, Delegate, Dependency Injection,...

_Ví dụ ứng dụng Protocol như một interface_
```sh
protocol SwitchType {
    var name: String { get set }
    var status: Bool { get }
    mutating func toggle()
}

class Switch: SwitchType {
    var name: String
    var status = false
    
    init(name: String) {
        self.name = name
    }
    
    func toggle() {
        print("Status\nBefore: \(self.status)")
        self.status = !status
        print("After: \(self.status)")
    }
}
```
<br></br>

### GCD, Queue type, NSOperation, async await
Trước khi tìm hiểu các vấn đề trên, ta cần biết về  khái niệm Concurrency
> Là khả năng giải quyết nhiều công việc một lúc
> và các công việc đó không nhất thiết phải xảy ra tại một thời điểm

**=> Lập trình bất đồng bộ giúp cho app hoạt động mượt mà, tiết kiệm thời gian và tối ưu tài nguyên**
Ta có thể lập trình bất đồng bộ trong iOS thông qua nhiều cách, nhiều công cụ, trong đó có thể kể đến GCD, NSOperation

**GCD**
* GCD là API cấp thấp quản lý thực hiện các tác vụ 
* Cải thiện hiệu năng app
* Tương tác với thread để xử lý task
* Người dùng tương tác với Queue của GCD để handle tác vụ

**Queue Type**
Có 2 loại queue chính:
* Main queue: Là serial queue, sử dụng main thread
* Global queue: Có thể concurrent hoặc serial queue tuỳ ý, được sử dụng các thread không phải main thread và gồm 4 loại QoS có sẵn định nghĩa hoặc người dùng có thể custom. Sau đây là các QoS được sắp xếp độ ưu tiên từ cao xuống thấp:
1. userInteractive
2. userInitiated
3. utility
4. background

**NSOperation**
Build dựa trên GCD, có cải tiến hơn khi có thể thêm sự phụ thuộc giữa các operation, tái sử dụng, huỷ hoặc dừng chúng.
Có 4 state chính của một operation: isReady -> isExecuting -> isCancelled hoặc isFinished.
Ngoài ra có thể xác định operation có đang chạy bất đồng bộ hay không thông qua property isConcurent và isAsynchronous.

**Async/Await**
`async/await` là từ khoá mới được thêm vào Swift 5.5. async/await được thêm vào nhằm rút gọn code completion trước đây.
Trước khi dùng `async/await`:
```sh
let A = 10
let B = 20
// Gọi đơn giản
cong(a: A, b: B) { result in
    print("cộng OKE nè : \(result)")
}
// Gọi lồng nhau
cong(a: A, b: B) { result in
    print("cộng OKE nè : \(result)")
    
    nhan(a: A, b: B) { result in
        print("nhân OKE nè : \(result)")
        
        cong(a: A, b: B) { result in
            print("cộng OKE 2 nè : \(result)")
            
            nhan(a: A, b: B) { result in
                print("nhân OKE 2 nè : \(result)")
            }
        }
    }
}
```

Sau khi dùng:
```sh
    let A = 10
    let B = 20
    print("... #1")
    await cong(a: A, b: B)
    print("... #2")
    await nhan(a: A, b: B)
    await cong(a: A, b: B)
    await nhan(a: A, b: B)
    print("2 kết quả nè: \(Cong) & \(Nhan)")
```

<br></br>

## URLSession vs Alamofire
- Cả URLSession và Alamofire đều mang chung một công dụng là hỗ trợ việc networking trong Swift
- URLSession là công cụ thuộc Foundation (Do Apple phát triển), trái lại Alamofire lại là thư viện bên thứ ba
- Alamofire tỏ ra vượt trội hơn về độ ngắn gọn và  sạch sẽ đối với tác vụ nhẹ như các request call không phức tạp
- Alamofire còn kết hợp rất tốt với  các thư viện phổ biến như ObjectMapper, RxSwift ; Kèm theo những template có sẵn khiến cho việc networking nhanh gọn và dễ dàng nên tới nay vẫn có nhiều người dùng
- Đối với các trường hợp scope app không có networking quá phức tạp,  nhiều người vẫn ưu tiền dùng Alamofire vì sự tiện dụng. Tuy nhiên vì là thư viện bên thứ ba nên Alamofire đem lại khá nhiều rủi ro ví dụ như khi update iOS, có nguy cơ thư viện không phát triển, phát triển chậm,...

<br></br>

## Cách config firebase service
1. Tạo project Firebase
2. Đăng ký app (BundleID, tên app, app store id nếu có)
3. Tải file GoogleService-Info.plist nhận được sau khi đăng ký và đưa vào root folder của project (Ngang hàng với Info.plist)
4. Add Firebase SDK vào app (SPM, cocoapods, carthage)
5. Thêm FirebaseApp.configure() vào AppDelegate
6. Dùng Firebase ở các file cần thiết

<br></br>

## Cách config notification (UNUserNotificationCenter, UIUserNotificationSettings, FirebaseMessaging)
1. Xin quyền gửi noti cho người dùng ở AppDelegate 
2. Bật Push Notification và Background ở Capabilities
3. Lên firebase -> Settings -> Up file .p12 (APNs certìicate)
3. Đăng ký nhận remote notification
4. Check fcm token ở AppDelegate
5. Đăng ký nhận push
6. Test

<br></br>

## Git flow, Merge vs Rebase, fix confict
**Git flow hiện tại đang follow**
![Git flow](https://dochub.com/tunghuason/r4D6EkZVZJ6Gxd3VpQXW7O/screenshot-2023-08-22-at-19-27-54-png "Git flow")
https://drive.google.com/file/d/118ehb09RJ-nlb5Yxu6jRBdHohCbO_pd6/view

**Rebase vs Merge**
- Đều có chung mục đích kết hợp sự thay đổi  giữa nhánh này với nhánh kia
- Git merge lấy thay đổi của nhánh này, apply vào nhánh kia rồi tạo commit mới
- Git rebase lấy thay đổi của nhánh này **ghi đè** lên đầu của nhánh kia, tạo ra một  cây commit liên tục 
=> Việc dùng git merge an toàn hơn, tuy nhiên git rebase lại đưa ra commit tree gọn gàng, sạch đẹp hơn

**Fix conflict**
- Muốn fix conflict git cần xét rất nhiều yếu tố
1. Code gây conflict là của mình hay của người khác? Nếu của người khác phải cùng họ bàn về tính logic (nếu cần) để giữ phần code hoặc kết hợp cả 2 sao cho hiệu quả
2. Code gây conflict có ảnh hưởng nhiều về mặt logic không? Nếu có phải có report đầy đủ để giữ **evidence** ,phòng cho việc sau này cần quay lại dễ tracking
3. Một số tool dùng để fix conflict: SourceTree, Android Studio, Terminal, Xcode

<br></br>

## Triển khai sprint trong Aglie
Scrum là một framework rất linh hoạt có hệ tư tưởng Agile, để triển khai một sprint gồm rất nhiều yếu tố, và có thể cô đọng lại thành các bước cơ bản sau:
1. Sprint planning: Xác định scope của sprint, mục đích của sprint, có thể đạt được điều gì và làm thế nào để đạt được điều đó trong và sau sprint. Ngoài ra sau khi xác định scope  và nguồn lựccó thể  xác định độ dài của sprint từ 2-4 tuần tuỳ scope. (Sử dụng Product Backlog và requirement đưa tới để xác định scope)
2. Sau khi planning xong ta có sprint backlog. Lúc này cần tool tracking task (redmine, jira, trello,...) và nếu có thể là một sheet excel để theo dõi tổng quan quá trình làm task của development team cùng với burndown chart để xem tính khả thi của sprint (Nếu có xu hướng không thành công cần báo sớm với các bên liên quan)
3. Khi đã chuẩn bị đủ Planning, Sprint Backlog, file quản lý tiến hành Implement và chạy sprint
4. Trong khoảng thời gian sprint chạy, mỗi ngày cần chọn ra một giờ để daily meeting  (Trả lời 3 câu hỏi: Hôm qua làm gì? Có gặp khó khăn gì không? Hôm nay làm gì?) Lưu ý 1 daily meeting chỉ diễn ra 15 phút
5. Đến giai đoạn cuối sprint, tổ chức sprint review để  deliver những gì làm được trong sprint cho khách hàng, PO xem
6. Sau buổi sprint review sẽ đến sprint retrospective để team review toàn bộ sprint vừa qua, nêu ra những điểm tốt để phát huy, điểm trừ cần cải thiện và đóng góp ý kiến để sprint sau thành công hơn
7. kết thức một sprint. Sau đó lại bắt đầu vòng lặp với sprint planning

<br></br>

## MVVM, MVP, VIPER
MVVM, VIPER và MVP là ba kiến trúc thường thấy trong mảng lập trình iOS.  Kiến trúc được dùng để phân tầng , tách biệt để dễ dàng hình dung, bảo trì và phát triển. 
- **MVVM** (Model - View - View Model): Có 3 thành phần chính. Model đại diện cho data-model, view đảm nhiệm phần hiển thị và nhận sự kiện,  và bắn sự kiện cho viewModel xử lý. iewModel xử lý các sự kiện,  nhận từ view thông qua bindingcác logic của app.
- **VIPER** (View - Interactor - Presenter - Entity - Router): Giống với MVVM, tuy nhiên Router xử lý các việc liên quan đến đổi màn, navgigation,... Entity chỉ là các cấu trúc dữ liệu chứ không  đảm nhiệm thêm việc access từ logic như Model ở MVVM, phần này được Interactor xử lý.
- **MVP** (Model - View - Presenter): Chia tách View và Model (Vẫn có nhiệm vụ giống MVVM) và phần xử lý logic, phần logic hiển thị và update view đều được Presenter xử lý.

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
