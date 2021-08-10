# JQUERY Basic

[I. Jquery syntax](#i-jquery-syntax)

[II. Jquery Selector](#ii-jquery-selector)

[III. Jquery Events](#iii-jquery-events)

## I. Jquery syntax

```javascript
    $(selector).action()
```

- A `$` sign để define, truy cập jquery
- A `(selector)` để truy cập tới element = với `querySelector()`
- A jQuery `action()` để thực hiện event = với `addEventListener(...)`

**Ví dụ:**

```javascript
    $(this).hide() - ẩn element đang đc chỉ định.

    $("p").hide() - ẩn tất cả `<p>` element.

    $(".test").hide() - ẩn tất cả element với class="test".

    $("#test").hide() - ẩn tất cả element với id="test".
```

Để cho `Jquery` chạy không bị lỗi do content `html` chưa được load hết thì tất cả các code của jquery sẽ được đặt trong method dưới đây. Method giúp đợi cho content của page load hết r ms thực hiện chương trình

```javascript
    $(document).ready(function() {
        //jquery method go there
    })
```

Method này giống với

```javascript

    document.addEventListener("DOMContentLoaded"...)
```

Phương thức trên có thể viết gọn thành:

```javascript
    $(function() {
        //jquery method go there
    })

```

## II. Jquery Selector

Jquery dùng để take element được chỉ định dựa trên `tag name`, `id`, `class`, `type`, `attribute`,....

### 1. Tag name selector

**Ví dụ:**

```javascript
    $(document).ready(function(){
        $("button").click(function(){
            $("p").hide();
        });
    });

```

Khi dùng `tag name` selector, jquery sẽ select tất cả các phần tử có `tag name` được select. Như ví dụ trên khi click vào `button`, tất cả các phần tử `<p>` sẽ được ẩn đi

### 2. Id Selector

**Syntax:**

```javascript
    $("#id")
```

**Ví dụ:**

```javascript
    $(document).ready(function(){
        $("button").click(function(){
            $("#test").hide();
        });
    });

```

`id` selector thường dùng để select cho chỉ 1 đối tượng.

### 3. Class selector

**Syntax:**

```javascript
    $(".class")
```

**Ví dụ:**

```javascript
    $(document).ready(function(){
        $("button").click(function(){
            $(".test").hide();
        });
    });
```

Khi click vào button, tất cả các element có `class="test"` sẽ được ẩn đi.

### 4. Các ví dụ khác về jquery selector

Syntax | Description
-------|------------
`$("*")` | Selects all elements |
`$(this)` | Selects the current HTML element |
`$("p.intro")` | Selects all `<p>` elements with class="intro" |
`$("p:first")` | Selects the first `<p>` element |
`$("ul li:first")` | Selects the first `<li>` element of the first `<ul>` |
`$("ul li:first-child")` | Selects the first `<li>` element of every `<ul>` |
`$("[href]")` | Selects all elements with an href attribute |
`$("a[target='_blank']")` | Selects all `<a>` elements with a target attribute value equal to "_blank" |
`$("a[target!='_blank']")` | Selects all `<a>` elements with a target attribute value NOT equal to "_blank" |
`$(":button")` | Selects all `<button>` elements and `<input>` elements of type="button" |
`$("tr:even")` | Selects all even `<tr>` elements |
`$("tr:odd")` | Selects all odd `<tr>` elements

## III. Jquery Events

Một số common DOM events:

Mouse Events | Keyboard Events | Form Events | Document/Window Events
-------------|-----------------|-------------|-----------------------
click | keypress | submit | load
dblclick | keydown | change | resize
mouseenter | keyup | focus | scroll
mouseleave |   | blur | unload

### 1. Syntax

Ví dụ với `click()` event:

```javascript
    $("p").click();
```

Sau đó để khai báo công việc gì sẽ xảy ra khi event occured ta cần truyền vào `function`

```javascript
    $("p").click(
        function() {
            //code there
        }
    )
```

### 2.  $(document).ready()

Dùng method này để có thể đợi có content all load r mới thực hiện các công việc tiếp theo để tránh lỗi

### 3. click() và dbclick()

`click()` method add một `event handler` đến element, khi user click vào element đó, `event handler` sẽ được thực hiện.

**Ví dụ:**

```html

    <p>Click me to hide</p>
    <p>I will hide if you click me</p>
    <p class = "hide">I will hide if you double click me</p>
    <script>
        $(function() {
            $("p").click(
                function() {
                    $(this).hide();
                }
            );

            $(".hide").dbclick(
                function() {
                    $(this).hide();
                }
            )
        })
    </script>
```

Kết quả khi click vào các element vs `<p>` tag name, chúng sẽ ẩn đi và double click vào các element có `class = "hide"` chúng cũng sẽ ẩn đi

### 4. mouseenter() và mouseleave()

`mouseenter` sẽ được executed khi chuột trỏ vào element và `mouseleave` sẽ được executed khi chuột rời khỏi element

**Ví dụ:**

```html
    <p id="p1">Point me</p>
    <p id="p2">Leave me</p>
    <script>
        $("#p1").mouseenter(function(){
            alert("You entered p1!");
        });
        $("#p2").mouseenter(function(){
            alert("You left p2!");
        });
    </script>
```

### 5. mouseup() và mousedown()

`mousedown` được executed khi chuột trái, hoặc phải hoặc giữa được click hoặc ấn giữ tại element và ngược lại `mouseup` được executed khi release chuột ra.

**Ví dụ:**

```html

    <p id = "p1">Event happen here</p>
    <script>
        $("#p1").mouseup(function(){
            alert("Mouse up over p1!");
        });
        $("#p1").mousedown(function(){
            alert("Mouse down over p1!");
        });
    </script>
```

Khi press chuột vào `<p>` thì Hiện ra `Mouse down over p1!` còn khi release chuột ra thì có tb `Mouse up over p1!`

### 6. hover()

Method nhận vào 2 callback là 2 function kết hợp giữa `mouseenter` và `mouseleave`

```javascript

    $("#p1").hover(function(){
        alert("You entered p1!");
    },
    function(){
        alert("Bye! You now leave p1!");
    });
```

### 7. focus() và blur()

`focus` thường được attach cho `form` element ví dụ input field khi chuột vẫn đang ở input field thì sự kiện sẽ được executed, còn `blur` là khi input field bị mất focus tức là click chuột ra ngoài vùng input

```html


    Name: <input type="text" name="fullname"><br>
    Email: <input type="text" name="email">
  <script>
        $(document).ready(function(){
            $("input").focus(function(){
                $(this).css("background-color", "yellow");
            });
            $("input").blur(function(){
                $(this).css("background-color", "green");
            });
        });
    </script>
```

Khi click chuột vào ô input và để nguyên thì back ground của ô input sẽ chuyển sang màu vàng còn khi click chuột ra khỏi vùng input thì background sẽ chuyển sang màu xanh lá cây.

### 8. on()

`on()` method dùng để attaches 1 hoặc nhiều event lên một element

**Ví dụ:**

Attaches 1 event lên selected element

```html

    <p>Click me and i will hide</p>
    <script>
        $("p").on("click", function(){
            $(this).hide();
        });
    </script>
```

Attaches nhiều event lên selected element

```html
    <p>DO something with me and see how i change</p>
    <script>
        $("p").on({
            mouseenter: function(){
                $(this).css("background-color", "lightgray");
            },
            mouseleave: function(){
                $(this).css("background-color", "lightblue");
            },
            click: function(){
                $(this).css("background-color", "yellow");
            }
        });
    </script>
```

Xem thêm tại:

[Jquery overview](https://www.w3schools.com/jquery/jquery_ref_overview.asp)

[Jquery selectors](https://www.w3schools.com/jquery/jquery_ref_selectors.asp)

[Jquery events](https://www.w3schools.com/jquery/jquery_ref_events.asp)

