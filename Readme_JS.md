# Tổng hợp kiến thức javascript thuần

> Index

- [Tổng hợp kiến thức javascript thuần]()
    - [Kiến thức chung]()
        - [Compile và interpret]()
    - [javascript]()
        - [Global Scope]()
        - [Engine And Runtime Enviroment]()
        - [Let và Var]()
        - [primitive and object]()
        - [Max and Min number]()
        - [concate string]()
        - [Ternary operator]()


## Kiến thức chung

    - HTML shell (template HTML)
    - Front End (FE) không an toàn (không bảo mật thông tin) => không lưu trữ thông tin quan trọng trên FE
    - Network => see how entire web app is downloaded
    - Vấn đề lớn nhất của web app là tốc độ load trang web => phụ thuộc vào tốc độ download thông tin từ server

### Compile và Interpret

    - Compile - 1 time run, when you click run it translate all your code into something that computer can understand
    - Interpret - keep your code there, when click run it interpret your code line by line
    - JIT (Just in time complimentation) it actually compile but it will make your code look like interpret (speed improvement)
    - Compile, Interpret or JIT is depended on the engine that build inside of the web browser

## javascript

### Scope

    - Window là object lớn nhất của 1 web page
    - Đặt scope {} để phân quyền sử dụng cho biến

### Engine And Runtime Enviroment

    - ecmascript - standard for js build
    - test262 - test how the browser is compatible with ecmascript
    - there is always an engine inside of a browser to make browser run js script
    - People want to make that engine out of a browser => they invent nodejs

### Let và Var

    - Đặt let trong dấu ngoặc {} thì biến được khai báo chỉ tồn tại trong phạm vi dấu ngoặc (chặt chẽ hơn var, chỉ tồn tại trong mọi scope được tạo)
    - var sẽ chỉ bị giới hạn trong phạm vi scope của function (không bị giới hạn bới khác scope khác như if else ...) nếu đặt biến var ngoài dấu ngoặc function thì biến var sẽ thành biến global (trong windows object)
    - const giống let nhưng sẽ không cho thay đổi giá trị của biến (hằng số)
    - Khai báo biến không dùng var hay let thì mặc định engine sẽ tìm kiếm ngược lên trên xem tên biến đã được khai báo chưa, nếu chưa thì sẽ tự động khai báo thành biến global (trong windows object) 

### primitive and object

    - javascript doesn't have type (we can assign everything to the variable)
    - primitive (do not have method and properties): string, number, boolean, null, undefined, symbol
    - undefined vs null: let the computer use undefined and we (human) use null
    - primitive is immutable - can not be changed
    - boxes object: new String(), ..., "AAA".toUpperCase() -> turn primitive string to boxes object and then turn back primitive string

### Max and Min number

    - Number.MAX_SAFE_INTEGER (9007199254740991)
    - Number.MIN_SAFE_INTEGER (-9007199254740991)

### concate string

    - let myName = "javascript";
    - console.log("Hello".concate(myName));
    - console.log("Hello " + myName);
    - console.log("Hello ${myName}");

### Ternary operator

    - let name = "AAAA";
    - let points = name === "Caleb" ? 10 : 0;

### label in loop

    outerLoop: for (let i = 0; i < grades.length; i++) {
    for (let k = 0; k < grades[i].length; k++) {
            console.log(grades[i][k]);
            if (grades[i][k] == 54) {
                console.log("you found the value");
                [break/continue] outerLoop;
            }
            console.log("doing stuff");
        }
        console.log("~~~~~~~~~");
    }
    - If using break before label, you will break the loop that match with the label
    - If using continue before label, you will continue the loop that match the label
