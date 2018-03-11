# 30_seconds_of_css

### Bouncing loader

`Creates a bouncing loader animation.`

Tạo hiệu ứng nảy khi tải trang.
#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__bouncing-loader">
  	<div></div>
    <div></div>
    <div></div>
  </div>
</div>

<style>
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.snippet-demo__bouncing-loader {
  display: flex;
  justify-content: center;
}
.snippet-demo__bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.snippet-demo__bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.snippet-demo__bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>

#### Giải thích

Ghi chú: `1rem` tương đương `16px`.

1. Ta sử dụng tag `@keyframes` để định nghĩa hiệu ứng có 2 trạng thái, khi thành phần thay đổi độ trong suốt `opacity` và nó được dịch chuyển lên trong mặt phẳng 2D thì sử dụng thuộc tính `transform: translateY()`.

2. `.bouncing-loader` là khối chứa các hình tròn có hiệu ứng nảy lên  và các hình tròn đó có sử dụng các thuộc tính`display: flex`
   và `justify-content: center` để cố định vị trí của chúng vào giữa ( theo chiều dọc ).

3. thành phần `.bouncing-loader > div`, tập trung vào 3 thẻ con `div` nằm trong class cha `.bouncing-loader`  targets the three child `div`s of the parent to be styled. The `div`s are given a width and height of `1rem`, using `border-radius: 50%` to turn them from squares to circles.

4. `margin: 3rem 0.2rem` quy định rằng mỗi khối hình tròn có khoản cách top vào bootom là `3rem` và trái phải là `0.2rem` như thế chúng sẽ không bị chạm vào nhau và cho chúng những khoảnh cách.

5. `animation` là thuộc tính viết tắt của các thuộc tính sau : `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction` được sử dụng.

6. `nth-child(n)` chỉ tới thuộc tính thứ n của cha nó.

7. `animation-delay` được sử dụng với thẻ `div` thứ 2 và thứ 3,như vây các khối tròn sẽ không bắt đầu lên xuống cùng 1 thời điểm.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->
### Đặt lại kích thước khối.

Reset lại khối để `width` và `height`không bị thay đổi khi có thêm `border` hoặc `padding`.

#### CSS

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__box-sizing-reset">Demo</div>
</div>

<style>
.snippet-demo__box-sizing-reset {
  box-sizing: border-box;
  width: 200px;
  padding: 1.5em;
  color: #7983ff;
  font-family: sans-serif;
  background-color: white;
  border: 5px solid;
}
</style>

#### Giải thích

1. `box-sizing: border-box` làm cho việc thêm `padding` hoặc `border`không ảnh hưởng tới `width` và `height`.
2. `box-sizing: inherit` làm cho thành phần con không thể làm thay đổi kích thước của phần từ mẹ `box-sizing`.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css3-boxsizing



### Circle

Tạo hình tròn trong CSS

#### HTML

```html
<div class="circle"></div>
```

#### CSS

```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__circle"></div>
</div>

<style>
.snippet-demo__circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
</style>

#### Explanation

`border-radius: 50%` dùng đường cong của khối để tạo hình tròn.

Một hình tròn với cùng bán kính thì chiều rộng và chiều cao phải có giá trị bằng nhau. Nếu giá trị khác nó sẽ trở thành hình eclip.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=border-radius

<!-- tags: visual -->


<!-- tags: layout -->
### Clearfix

Đảm bảo rằng thuộc tính con sẽ được clear.

###### Note: Điều này chỉ hữu ích khi ta dùng để xây bố cục của layout. Hãy dùng phương pháp tốt để tạo ra các layout hoặc grid layout.

#### HTML

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

#### CSS

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.floated {
  float: left;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__clearfix">
    <div class="snippet-demo__floated">float a</div>
    <div class="snippet-demo__floated">float b</div>
    <div class="snippet-demo__floated">float c</div>
  </div>
</div>

<style>
.snippet-demo__clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.snippet-demo__floated {
  float: left;
}
</style>

#### Giải thích

1. `.clearfix::after` tạo ra phần tử giả.
2. `content: ''` cho phép phần tử giả thay đổi bố cục layout.
3. `clear: both` chỉ ra rằng bên phải và bên trái không thể kể với các phần tử nào.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ For this snippet to work properly you need to ensure that there are no non-floating children in the container and that there are no tall floats before the clearfixed container but in the same formatting context (e.g. floated columns).</span>

<!-- tags: layout -->
### Chiều rộng cố định để chiều cao tỉ lệ.

Với phần tử có chiều rộng thay đổi đảm bảo chiều cao vẫn đúng tỉ lệ.
(i.e., its width to height ratio remains constant).

#### HTML

```html
<div class="constant-width-to-height-ratio"></div>
```

#### CSS

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

#### Demo

Thay đổi kích thước cửa sổ trình duyệt của bạn để xem tỷ lệ phần tử vẫn được giữ nguyên.
<div class="snippet-demo">
  <div class="snippet-demo__constant-width-to-height-ratio"></div>
</div>

<style>
.snippet-demo__constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.snippet-demo__constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.snippet-demo__constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
</style>

#### Giải thích 

`padding-top` ở trong `::before` tao ra phần tử có chiều cao bằng một phần trăm nào đó của chiều rộng.
. `padding-top`:: before là 100% nên chiều cao sẽ luôn bằng chiều rộng.
Phương pháp này cũng cho phép nội dung được đặt bên trong phần tử bình thường.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

### Counter

là bộ đếm. Bản chất là biến được duy trì bởi CSS mà giá trị của nó được tăng lên để theo dõi số lần sử dụng chúng.

#### HTML

```html
<ul>
  <li>List item</li>
  <li>List item</li>
  <li>List item</li>
</ul>
```

#### CSS

```css
ul {
  counter-reset: counter;
}

li::before {
  counter-increment: counter;
  content: counters(counter, '.') ' ';
}
```

#### Demo

<div class="snippet-demo">
	<div class="snippet-demo__countable-section">
    <ul>
      <li>List item</li>
      <li>List item</li>
      <li>
        List item
        <ul>
          <li>List item</li>
          <li>List item</li>
          <li>List item</li>
        </ul>
      </li>
    </ul>
  </div>
</div>

<style>
  .snippet-demo__countable-section ul {
    counter-reset: counter;
    list-style-type: none;
  }

  .snippet-demo__countable-section li::before {
    counter-increment: counter;
    content: counters(counter, '.') ' ';
  }
</style>

#### Explanation

Bạn có thể tạo một danh sách được sắp xếp sử dụng bất kỳ loại HTML nào.

1. `counter-reset` Khởi tạo một bộ đếm, giá trị là tên của bộ đếm. Mặc định bộ đếm bắt đầu = 0. Thuộc tính này cũng có thể sử dụng để thay đổi giá trị.

2. `counter-increment` được sử dụng thì sẽ tăng bộ đếm. Once `counter-reset` initialized, a counter's value can be increased or decreased.

3. `counter(name, style)` hiển thị giá trị của biến đếm. hay được dùng với thuộc tính `content`. Đây là 1 hàm có thể có 2 tham số thứ nhất là tên và thứ 2 là số decimal hoặc upper-roman. (decimal được mặc định).

4. `counters(counter, string, style)` hiển thị giá trị của biến đếm. hay được dùng với thuộc tính `content`. Đây là 1 hàm có thể có 3 tham số thứ nhất là tên và thứ 2 là chuỗi và tham số thứ 3 là số  decimal hoặc upper-roman. (decimal được mặc định).


5. Độ đến hữu ích để tạo ra danh sách Bởi vì một trường hợp mới của bộ đếm được tự động tạo ra trong các phần tử con. Dùng hàm `counters()` , separating text can be inserted between different levels of nested counters.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-counters

<!-- tags: visual, other -->


### Tùy chỉnh thanh cuộn.

Tùy chỉnh kiểu cuộn cho tài liệu và các phần tử có bị tràn, trên nền tảng WebKit.

#### HTML

```html
<div class="custom-scrollbar">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
/* Document scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

/* Scrollable element */
.some-element::webkit-scrollbar {
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-scrollbar">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
  </div>
</div>

<style>
.snippet-demo__custom-scrollbar {
  height: 100px;
  overflow: auto;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
</style>

#### Giải thích

1. `::-webkit-scrollbar` đối tượng là toàn bộ phần tử thanh cuộn.
2. `::-webkit-scrollbar-track` đối tượng chỉ rãnh của thanh cuộn thanh trượt.
3. `::-webkit-scrollbar-thumb` đối tượng là thanh trượt.

https://codepen.io/xmenkingofstar/pen/rdVadK

có nhiều yếu tố khác để tạo kiểu thanh cuộn. Hãy ghé thăm [WebKit Blog](https://webkit.org/blog/363/styling-scrollbars/)

#### Browser support

<span class="snippet__support-note">⚠️ Scrollbar styling doesn't appear to be on any standards track.</span>

* https://caniuse.com/#feat=css-scrollbar

<!-- tags: visual -->


### Custom text selection (Lựa chọn văn bản tùy chọn)
  
  Thay đổi kiểu dáng của lựa chọn văn bản.

#### HTML

```html
<p class="custom-text-selection">Select some of this text.</p>
```

#### CSS

```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__custom-text-selection">Select some of this text.</p>
</div>

<style>
.snippet-demo__custom-text-selection::selection {
  background: deeppink;
  color: white;
}
.snippet-demo__custom-text-selection::-moz-selection {
  background: deeppink;
  color: white;
}
</style>

#### Giải thích 

`::selection` defines a pseudo selector on an element to style text within it when selected. Note that if you don't combine any other selector your style will be applied at document root level, to any selectable element.

#### Browser support

<span class="snippet__support-note">⚠️ Requires prefixes for full support and is not actually
in any specification.</span>

* https://caniuse.com/#feat=css-selection

<!-- tags: visual -->


