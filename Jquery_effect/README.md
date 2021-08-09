# Jquery effect

[I. Jquery Hide and Show](#i-jquery-hide-and-show)

[II. Jquery Fade](#ii-jquery-fade)

[III. Jquery Slide](#iii-jquery-slide)

## I. Jquery Hide and Show

### 1. Hide and show

**Syntax:**

```javascript
    $(selector).hide(speed, callback);
    $(selector).show(speed, callback);
```

Trong đó `speed` để define tốc độ hide và show với các option:

- `"slow"`
- `"fast"`
- `miliseconds` ví dụ 1000 (1s)

Và `callback` thực hiện function nào đó sau khi `hide` và `show` method complete.

**Ví dụ:**

```html

    <p>This is the content wich can hide and show</p>
    <button id="hide">Hide</button>
    <button id="show">Show</button>
    <script>
        $(function() {
            $("hide").click(function() {
                $("p").hide("slow");
            });
            $("show").click(function() {
                $("p").show(1000);
            });

        })
    </script>
```

Khi ấn vào button hide nó sẽ ẩn `<p>` đi từ từ còn khi ấn vào button show nó sẽ hiện `<p>` ra sau 1s.

### 2. Jquery Toggle()

Chúng ta có thể chuyển đối giữa `hide` và `show` bằng toggle method. Tức là ban đầu element được selected sẽ `show`, click lần 1 sẽ `hide` đi và click lần nữa sẽ lại `show` ...

**Syntax:**

```javascript
    $(selector).toggle(speed, callback);
```

**Ví dụ:**

```html
    <p>This content is togglable</p>
    <button id="toggle">Show and hide toggle</button>
    <script>
        $(function() {
            $("toggle").click(function() {
                $("p").toggle();
            })
        })
    </script>
```

**Lưu ý:** Không nên đặt toggle trực tiếp lên click event của element cần đc toggle vì khi `hide` đi là nó biến mất, k click để `show` được nữa

## II. Jquery Fade

Với Jquery ta có thể fade element khi ẩn và hiện

Jquery gồm các fade method sau:

- fadeIn()
- fadeOut()
- fadeToggle()
- fadeTo()

### 1. Jquery fadeIn() và fadeOut() method

`fadeIn` dùng để tạo hiệu ứng `fade in` cho hidden element và ngược lại `fadeOut` để tạo hiệu ứng khi ấn element đi

**Syntax:**

```javascript
    $(selector).fadeIn(speed, callback);
    $(selector).fadeOut(speed, callback);

```

**Ví dụ:**

```html
    <div style="width:50px;height:50px;background-color:red;display:none"></div>
    <button id="btn1">Click me to fade in content</button>
    <button id="btn2">Click me to fade out content</button>
    <script>
        $(function() {
            $("#btn1").click(function() {
                $("div").fadeIn("slow");
            });
            $("#btn2").click(function() {
                $("div").fadeOut(3000);
            })
        })
    </script>
```

### 2. fadeToggle()

`fadeToggle` cũng có chức năng tương tự như `toggle` method nhưng thêm hiệu ứng fade.

**Syntax:**

```javascript
    $(selector).fadeToggle(speed, callback);
```

**Ví dụ:**

```html
    <div style="width:50px;height:50px;background-color:red;display:none"></div>
    <button>Click me to fade in/out content</button>
    <script>
        $(function() {
            $("button").click(function() {
                $("div").fadeToggle(3000);
            })
        })
    </script>
```

### 3. fadeTo()

`fadeTo()` cho phép element fading với opacity.

**Syntax:**

```javascript
    $(selector).fadeTo(speed, opacity, callback)
```

Trong đó `opacity` nằm trong đoạn từ `0 - 1`

**Ví dụ:**

```html
    <div style="width:50px;height:50px;background-color:red;display:none"></div>
    <button>Click me to fade in/out content</button>
    <script>
        $(function() {
            $("button").click(function() {
                $("div").fadeTo(3000,0.5);
            })
        })
    </script>
```

Ví dụ trên sẽ làm `<div>` fading từ trạng thái `hide`( opacity = 0) sang hiện ra với `opacity=0.5`
muốn hiện ra hoàn toàn thì `opacity=1`

## III. Jquery Slide

