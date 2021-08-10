# Jquery HTML note

[I. Jquery get content and attribute](#i-jquery-get-content-and-attribute)

[II. Jquery set content and attribute](#ii-jquery-set-content-and-attribute)

[III. Jquery add elements](#iii-jquery-add-elements)

[IV. Jquery remove elements](#iv-jquery-remove-elements)

[V. Jquery CSS classes](#v-jquery-css-classes)

[VI. Jquery css()](#vi-jquery-css)

[VII. Jquery Dimensions](#vii-jquery-dimensions)

## I. Jquery get content and attribute

### 1. Get content với  text(), html(), val()

- `text()` - Chỉnh hoặc lấy ra phần text content trong element
- `html()` - Chỉnh hoặc lấy ra phần html content bên trong element bao gồm cả mark up
- `val()` - Chỉnh hoặc lấy ra phần giá trị của form field

**Ví dụ:**

```html
    <p><strong>This is the content</strong></p>
    <input type="text" value="this is input value">
    <div>
        <button id="btn1">Click here to show text content</button>
        <button id="btn2">Click here to show html content</button>
        <button id="btn3">Click here to show input value</button>
    </div>
    <script>
        $(function(){
            $("#btn1").click(function() {
                alert("Text content: " + $("p").text());
            });
            $("#btn2").click(function() {
                alert("Html content: " + $("p").html());
            });
            $("#btn3").click(function() {
                alert("Input value: " + $("input").val());
            });
        })
    </script>

```

### 2. Get Attribute với attr()

`attr('atribute_name')` method dùng để lấy attribute value

**Ví dụ:**

```html

    <button type="button">Click to view my type attribute value</button>

    <script>
        $(function(){
            $("button").click(function(){
                alert("My attribute type value is: " + $("button").attr("type"));
            })
        })
    </script>

```

## II. Jquery set content and attribute

### 1. Set content

Ta dùng same function với get content để set content

**Ví dụ:**

```html
    <p><strong>This is content</strong></p>
    <input type="text" value="this is input value">
    <div>
        <button id="btn1">Click here to change content</button>
        <button id="btn2">Click here to change html content</button>
        <button id="btn3">Click here to change input value</button>
    </div>
    <script>
        $(function(){
            $("#btn1").click(function() {
                $("p").text("This content has been changed");
            });
            $("#btn2").click(function() {
                $("p").html("<strong>This content has been changed</strong>");
            });
            $("#btn3").click(function() {
                $("input").val("This input value has been changed");
            });
        })
    </script>
```

Tất cả các method set trên đều có thể đi với callback function. Callback function này nhận vào 2 tham số. Tham số đầu tiên là index của element được chọn trong số tất cả các element được selected và tham số thứ 2 là nội dung ban đầu của element đó.

Callback function return nội dung mới mà ta muốn thay đổi.

**Ví dụ:**

```html
    <p>This is old content</p>
    <p>This is old content</p>
    <button>Click here to change the content</button>
    <script>
        $(function(){
            $("button").click(function(){
                $("p").text(
                    function(index, old_content){
                        if(index == 0){
                            return "Old contetnt: "+ old_content + " New content: Hello" + " index: " + index;
                        }
                    }
                );
            });
        })
    </script>

```

### 2. Set attribute value

**Ví dụ:**

```javascript
    $("button").click(function(){
        $("#w3s").attr("href", "https://www.w3schools.com/jquery/");
});

```

Ví dụ trên làm thay đổi href của element với `id="w3s"`. Ngoài ra ta có thể thay đổi nhiều attribute at the same time

```javascript
    $("button").click(function(){
        $("#w3s").attr({
            "href" : "https://www.w3schools.com/jquery/",
            "title" : "W3Schools jQuery Tutorial"
  });
});
```

`callback` function của `attr` cũng tương tự như của bên thay đổi content

**Ví dụ:**

```javascript

    $("button").click(function(){
        $("#w3s").attr("href", function(i, origValue){
            return origValue + "/jquery/";
        });
    });
```

Xem ví dụ trong file:

[set_example](#./set_example)

[get_example](#./get_example)

## III. Jquery add elements

Các jquery method dùng để add elements:

- `append()` - Inserts content vào cuối element( bên trong)
- `prepend()` - Inserts content vào đầu element (bên trong)
- `after()` - Inserts content sau element được chọn (bên ngoài)
- `before()` - Inserts content trước element được chọn (bên ngoài)

### 1. Jquery append() method

`append` method giúp thêm html vào cuối element

**Ví dụ:**

```html
    <p>This is old content</p>
    <p>This is old content</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
    <button id="btn1">Click to append text</button>
    <button id="btn2">Click to append list item</button>
    <script>
        $(function(){
            $("#btn1").click(function(){
                $("p").append("<b> New text</b>");
            });
            $("#btn2").click(function(){
                $("ul").append("<li>Item 3</li>");
            });
        })
    </script>
```

### 2. prepend() method

Ngược lại với `append()`, `prepend` thêm content vào đầu của element.

**Ví dụ:**

```html
    <p>This is old content</p>
    <p>This is old content</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
    <button id="btn1">Click to append text</button>
    <button id="btn2">Click to append list item</button>
    <script>
        $(function(){
            $("#btn1").click(function(){
                $("p").prepend("<b> New text</b>");
            });
            $("#btn2").click(function(){
                $("ul").prepend("<li>Item 0</li>");
            });
        })
    </script>
```

**Ta có thể thêm nhiều content hoặc element một lúc với append và prepend:**

Ví dụ:

```html
    <body>
    <button>Click me</button>
    <script>
        $(function() {
            function prependText() {
                var txt1 = "<p>Text.</p>";               // Create element with HTML 
                var txt2 = $("<p></p>").text("Text.");   // Create with jQuery
                var txt3 = document.createElement("p");  // Create with DOM
                txt3.innerHTML = "Text.";
                $("body").prepend(txt1, txt2, txt3);      // Append the new elements
            }
            $("button").click(prependText);
        })
    </script>
    </body>
```

Lưu ý trong đó `txt2` và `txt3` là dạng html được tạo bởi jquery và dom, không phải string như `txt1`

### Jquery before() and after() method

Hai phương thức `before` và `after` dùng để thêm content html vào trước hoặc sau selected element

**Ví dụ:**

```html

    <p>This is selected element</p>
    <button>Click me to view what's changed</button>
    <script>
        $(function(){
            $("button").click(function(){
                $("p").before("<b>Before</b>");
                $("p").after("<i>After</i>");
            })
        })
    </script>
```

Mở `Crt + Shift + I` để thấy rõ hơn sự thay đổi.

**Tương tự như append và prepend, before và after method cũng cho phép ta add nhiều html content trước và sau một selected element:**

Ví dụ:

```html

    <!DOCTYPE html>
    <html>
    <head>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
        <script>
            function afterText() {
              var txt1 = "<b>I </b>";           // Create element with HTML
              var txt2 = $("<i></i>").text("love ");  // Create with jQuery
              var txt3 = document.createElement("b");   // Create with DOM
              txt3.innerHTML = "jQuery!";
              $("img").after(txt1, txt2, txt3);    // Insert new elements after img
            }
        </script>
    </head>
    <body>

        <img src="/images/w3jquery.gif" alt="jQuery" width="100" height="140">

        <p>Click the button to insert text after the image.</p>

        <button onclick="afterText()">Insert after</button>

    </body>
    </html>
```

## IV. Jquery remove elements

Chúng ta dùng hai phương thức sau để remove elements và content

- `remove()` - Removes element được chọn và các element inside nó
- `empty()` - Removes element bên trong element được chọn

**Ví dụ:**

```html
        <style>
            div {
                background-color: green;
                width: 50px;
                height: 50px;
                margin-botton: 20px;
            }
        </style>
    </head>
    <body>
    <div id="id1">This is a content</div>
    <div id="id2">This is a content too</div>
    <button id="btn1">Click me to remove element and its childs</button>
    <button id="btn2">Click me to remove my child element</button>
    
    <script>
        $("#btn1").click(function() {
            $("#id1").remove();
        });
        $("#btn2").click(function() {
            $("#id2").empty();
        });
    </script>
```

`remove` method cho phép truyền vào một tham số để làm filter xóa đi các content xác định với `id` hoặc `class name`

**Ví dụ:**

```html
    <style>
            div {
                background-color: green;
                width: 100px;
                height: 100px;
                margin-botton: 20px;
            }
        </style>
    </head>
    <body>
    <p>This is a content</p>
    <p class="clear"> This is a p tag with clear class</p>
    <p id="erase"> This is a p tag with id is erase</p>
    <button id="btn1">Click me to remove element and its childs</button>
    
    <script>
        $("#btn1").click(function() {
            $("p").remove(".clear, #erase");
        });
    </script>
```

## V. Jquery CSS classes

Một số phương thức để thay đổi class của element:

- addClass()

- removeClass()

- toggleClass()

- css()

Trong đó 2 phương thức đầu đề thêm một hoặc nhiều class cho element và xóa class khỏi element. Phương thức thức 3 để toggle giữa việc thêm và việc xóa một class khỏi element

**Ví dụ:**

```javascript
    $("button").click(function(){
        $("h1, h2, p").addClass("blue");
        $("div").addClass("important");
});
```

Hay ta có thể thêm nhiều class cho đối tượng:

```javascript
    $("button").click(function(){
        $("#div1").addClass("important blue");
    });
```

Xóa class từ đối tượng:

```javascript
    $("button").click(function(){
        $("h1, h2, p").removeClass("blue");
});
```

Toggle giữa việc thêm và xóa class:

```javascript
    $("button").click(function(){
        $("h1, h2, p").toggleClass("blue");
});
```

## VI. Jquery css()

Chúng ta có thể dùng `css()` method để get hoặc set một hoặc nhiều style properties

**Syntax:**

Lấy CSS properties và value

```javascript
   
    $(selector).css(property)
```

sửa CSS properties và value

```javascript
    
    $(selector).css(property,value)
```

Sửa css propeties và value sử dụng callback function

```javascript
    
    $(selector).css(property,function(index,currentvalue))
```

Sửa nhiều css properties và value

```javascript
    
    $(selector).css({property:value, property:value, ...})

```

**Ví dụ về getter:**

```html
    <script>
        $(document).ready(function(){
          $("button").click(function(){
            alert("Background color = " + $("p").css        ("background-color"));
          });
        });
    </script>
</head>
<body>

    <h2>This is a heading</h2>

    <p style="background-color:#ff0000">This is a paragraph.</p>
    <p style="background-color:#00ff00">This is a paragraph.</p>
    <p style="background-color:#0000ff">This is a paragraph.</p>

    <button>Return background-color of p</button>
```

Trong ví dụ này nó sẽ alert ra giá trị `background-color` của `p` element đầu tiên trong list `p` element. muốn trả về về các phần tử khác ta có thể sử dụng truy cập `$($("p")[index])`. Ví dụ muốn trả về `p` thứ hai ta dùng `$($("p")[1])`

**Ví dụ về set properties value:**

```javascript
    $("p").css("background-color", "yellow");
```

Đoạn code trên sẽ sửa tất cả `background-color` của các `p` elements

**Set nhiều properties value cùng một lúc:**

```javascript
    $("p").css({"background-color": "yellow", "font-size": "200%"});
```

Còn nếu muốn set theo ý muốn element tại vị trí nào đó ta có thể dùng callback function hoặc sử dụng truy cập như sau:

**Ví dụ:**

```javascript
    //Sử dụng callback
    $("p").css("background-color", function(index, oldValue){
        if(index == 1){
            //return new value
            return "yellow";
        }
    })

    // hoặc có thế truy cập trực tiếp

    $($("p")[1]).css("background-color", "yellow")

```

## VII Jquery Dimensions

Các method quan trọng để làm việc với dimentions:

- width()
- height()
- innerWidth()
- innerHeight()
- outerWidth()
- outerHeight()

**Jquery dimensions:**

![Jquery dimensions](./jquery_dim.gif)

### 1. Jquery get width() và height()

Hai phương thức `width()` và `height()` trả về width và height của element không bao gồm margin, border và padding

**Ví dụ:**

```html
    <script>
        $(document).ready(function(){
            $("button").click(function(){
                var txt = "";
                txt += "Width of div: " + $("#div1").width() + "</br>";
                txt += "Height of div: " + $("#div1").height();
                $("#div1").html(txt);
            });
        });
    </script>
    <style>
        #div1 {
          height: 100px;
          width: 300px;
          padding: 10px;
          margin: 3px;
          border: 1px solid blue;
          background-color: lightblue;
    }
    </style>
</head>
<body>

<div id="div1"></div>
<br>

<button>Display dimensions of div</button>

<p>width() - returns the width of an element.</p>
<p>height() - returns the height of an element.</p>

```

Tương tự ta có:

- `innerWidth()` và `innerHeight()` trả về width và height của element trong đó bao gốm cả padding

- `outerWidth()` và `outerHeight()` trả về width và height của element trong đó bao gồm cả padding và border

- `outerWidth(true)` và `outerHeight(true)` trả về width và height của element trong đó bao gồm cả padding và border và margin

**Ví dụ về việc trả về width() và height() của HTMl document và window(browser):**

```html
    <!DOCTYPE html>
    <html>
    <head>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
        <script>
            $(document).ready(function(){
              $("button").click(function(){
                var txt = "";
                txt += "Document width/height: " + $(document).width();
                txt += "x" + $(document).height() + "\n";
                txt += "Window width/height: " + $(window).width();
                txt += "x" + $(window).height();
                alert(txt);
              });
            });
        </script>
    </head>
    <body>

    <button>Display dimensions of document and window</button>

    </body>
    </html>


```

### 2. set width() và height()

Để thay đổi width và height ta dùng như sau:

```javascript
    $("button").click(function(){
        $("#div1").width(500).height(500);
    });

```