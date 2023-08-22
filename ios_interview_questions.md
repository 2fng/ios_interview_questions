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

<br></br>

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

### So sánh weak, unowned
> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

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
