---
layout: course-typescript
title: Sử dụng Interface  
slug : typescript-interface
category: laptrinhjavascript
tags: [typescript]
summery: Interface   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Interface trong Typescrip, cách hoạt động của Interface trong Typescrip
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Interface</b> là như thế nào? 

# **1. Interface là gì**

Chúng ta sử dụng Interface để định nghĩa một cấu trúc mà bất cứ Class nào khi sử dụng nó đều phải tuân thủ các biến và phương thức có trong interface. Chúng ta sử dụng từ khoá interface để tạo.

Ví dụ như ta tạo một kiểu dữ liệu interface là IPerson như sau. Nó gồm có 2 thuộc tính là firstName, lastName và phương thức sayHi.

{% highlight javascript  linenos %}

interface IPerson { 
   firstName:string, 
   lastName:string, 
   sayHi: ()=>string 
} 

{% endhighlight %}

Ví dụ ta có đối tượng customer sử dụng cấu trúc IPerson, thì lớp customer phải định nghĩa 2 thuộc tính firstName, lastName và phương thức sayHi giống như Interface

{% highlight javascript  linenos %}

var customer:IPerson = { 
   firstName:"Tom",
   lastName:"Hanks", 
   sayHi: ():string =>{return "Hi there"} 
} 

console.log("Customer Object ") 
console.log(customer.firstName) 
console.log(customer.lastName) 
console.log(customer.sayHi())  

var employee:IPerson = { 
   firstName:"Jim",
   lastName:"Blakes", 
   sayHi: ():string =>{return "Hello!!!"} 
} 
  
console.log("Employee  Object ") 
console.log(employee.firstName);
console.log(employee.lastName);

{% endhighlight %}

Như vậy ta thấy Interface giống như định nghĩa một kiểu cấu trúc cho các Class sử dụng nó.

# **2. Interface định nghĩa cấu trúc cho function**

TypeScript Interface cũng dùng để định nghĩa kiểu của function.

{% highlight javascript  linenos %}

interface KeyValueProcessor
{
    (key: number, value: string): void;
};

function addKeyValue(key:number, value:string):void { 
    console.log('addKeyValue: key = ' + key + ', value = ' + value)
}

function updateKeyValue(key: number, value:string):void { 
    console.log('updateKeyValue: key = '+ key + ', value = ' + value)
}
    
let kvp: KeyValueProcessor = addKeyValue;
kvp(1, 'Bill'); //Output: addKeyValue: key = 1, value = Bill 

kvp = updateKeyValue;
kvp(2, 'Steve'); //Output: updateKeyValue: key = 2, value = Steve 

{% endhighlight %}

Ta khai báo let kvp: KeyValueProcessor = addKeyValue. Nghĩa là hàm addKeyValue sẽ sử dụng cấu trúc function của interface KeyValueProcessor gồm có 2 tham số truyền vào là kiểu number và String.

# **3. Interface định nghĩa cấu trúc cho Array**

Interface cũng có thể dùng định nghĩa cấu trúc cho mảng như sau

{% highlight javascript  linenos %}

interface NumList {
    [index:number]:number
}

let numArr: NumList = [1, 2, 3];
numArr[0];
numArr[1];

interface IStringList {
    [index:string]:string
}

let strArr : IStringList;
strArr["TS"] = "TypeScript";
strArr["JS"] = "JavaScript";

{% endhighlight %}

# **4. Tham số tuỳ chọn**

Trong interface chúng ta có thể cho phép một số thuộc tính hoặc phương thức có thể được có hoặc không có trong class sử dụng nó. Bằng cách sử dụng dấu ? như sau

{% highlight javascript  linenos %}

interface IEmployee {
    empCode: number;
    empName: string;
    empDept?:string;
}

let empObj1:IEmployee = {   // OK
    empCode:1,
    empName:"Steve"
}

let empObj2:IEmployee = {    // OK
    empCode:1,
    empName:"Bill",
    empDept:"IT"
}

{% endhighlight %} 

# **5. Tham số chỉ được phép đọc**

Trong Interface sẽ có những thuộc tính mà ta chỉ cho phép class dùng nó được đọc mà không được thay đổi giá trị. Ta sử dụng từ khoá readonly như sau

{% highlight javascript  linenos %}

interface Citizen {
    name: string;
    readonly SSN: number;
}

let personObj: Citizen  = { SSN: 110555444, name: 'James Bond' }

personObj.name = 'Steve Smith'; // OK
personObj.SSN = '333666888'; // Compiler Error

{% endhighlight %}

# **6. Kế thừa Interface**

Chúng ta có thể kế thừa một hoặc nhiều interface để sử dụng lại. Mình sẽ dùng từ khoá extends như sau

{% highlight javascript  linenos %}

interface IPerson {
    name: string;
    gender: string;
}

interface IEmployee extends IPerson {
    empCode: number;
}

let empObj:IEmployee = {
    empCode:1,
    name:"Bill",
    gender:"Male"
}

{% endhighlight %}

# **7. Implement Interface**

Cũng giống như các ngôn ngữ lập trình khác. TypeScript Interface cũng cho phép một class cài đặt nó. Chúng ta sử dụng từ khoá implements

{% highlight javascript  linenos %}

interface IEmployee {
    empCode: number;
    name: string;
    getSalary:(number)=>number;
}

class Employee implements IEmployee { 
    empCode: number;
    name: string;

    constructor(code: number, name: string) { 
                this.empCode = code;
                this.name = name;
    }

    getSalary(empCode:number):number { 
        return 20000;
    }
}

let emp = new Employee(1, "Steve");

{% endhighlight %}

# **8. Generic trong Interface**

Chúng ta cũng có thể tạo một Interface có kiểu Generic trong TypeScript như sau.

{% highlight javascript  linenos %}

interface KeyPair<T, U> {
    key: T;
    value: U;
}

let kv1: KeyPair<number, string> = { key:1, value:"Steve" }; // OK
let kv2: KeyPair<number, number> = { key:1, value:12345 }; // OK

{% endhighlight %}

- Chúng ta có thể sử dụng trong function 

{% highlight javascript  linenos %}

interface KeyValueProcessor<T, U>
{
    (key: T, val: U): void;
};

function processNumKeyPairs(key:number, value:number):void { 
    console.log('processNumKeyPairs: key = ' + key + ', value = ' + value)
}

function processStringKeyPairs(key: number, value:string):void { 
    console.log('processStringKeyPairs: key = '+ key + ', value = ' + value)
}
    
let numKVProcessor: KeyValueProcessor<number, number> = processNumKeyPairs;
numKVProcessor(1, 12345); //Output: processNumKeyPairs: key = 1, value = 12345 

let strKVProcessor: KeyValueProcessor<number, string> = processStringKeyPairs;
strKVProcessor(1, "Bill"); //Output: processStringKeyPairs: key = 1, value = Bill 

{% endhighlight %}

















