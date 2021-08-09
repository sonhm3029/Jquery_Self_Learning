# Jquery effect

## I. Jquery Hide and Show

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