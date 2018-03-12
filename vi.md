# 30_seconds_of_css

### Nảy khi tải trang.

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
  
  Thay đổi kiểu dáng của văn bản duoc lựa chọn .

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

`::selection` định nghĩa một bộ chọn giả trên một phần tử để định kiểu văn bản bên trong nó khi được chọn. Lưu ý rằng nếu bạn không kết hợp voi  bộ chọn khác bất kỳ, kiểu của bạn sẽ được áp dụng ở cấp gốc cua tài liệu, cho bất kỳ phần tử nào có thể lựa chọn .

#### Browser support

<span class="snippet__support-note">⚠️ Requires prefixes for full support and is not actually
in any specification.</span>

* https://caniuse.com/#feat=css-selection

<!-- tags: visual -->


### Tùy chỉnh biến.

Các biến CSS chứa các giá trị cụ thể để được sử dụng lại trong suốt tài liệu.
#### HTML

```html
<p class="custom-variables">CSS is awesome!</p>
```

#### CSS

```css
:root {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
}

.custom-variables {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-variables">
    <p>CSS is awesome!</p>
  </div>
</div>

<style>
.snippet-demo__custom-variables {
  --some-color: #686868;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray , 0 0 0.2em slategray;
}

.snippet-demo__custom-variables p {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
</style>

#### Giải thích.

biến được định nghĩa toàn cuc voi `:root` CSS pseudo-class la thu noi phần tử gốc của một cây đại diện cho tài liệu. Các biến cũng có thể được đưa vào bộ chọn nếu được định nghia trong khối
Declare a variable with `--variable-name:`.

Tái sử dụng các biến số trong toàn bộ tài liệu bằng cách sử dụng ham `var(--variable-name)`.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: other -->


### Vô hiệu hóa lựa chọn.

Làm cho nội dung không the được chọn.
#### HTML

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

#### CSS

```css
.unselectable {
  user-select: none;
}
```

#### Demo

<div class="snippet-demo">
  <p>You can select me.</p>
  <p class="snippet-demo__disable-selection">You can't select me!</p>
</div>

<style>
.snippet-demo__disable-selection {
  user-select: none;
}
</style>

#### Giải thích

`user-select: none` xác định rằng văn bản không thể được chọn.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>
<span class="snippet__support-note">⚠️ This is not a secure method to prevent users from copying content.</span>

* https://caniuse.com/#feat=user-select-none

<!-- tags: interactivity -->


### Hiệu ứng quay tròn.

Tạo một máy quay tron có thể được sử dụng để chỉ việc nội dung dang duoc tải.
#### HTML

```html
<div class="donut"></div>
```

#### CSS

```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__donut-spinner"></div>
</div>

<style>
@keyframes snippet-demo__donut-spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg);}
}
.snippet-demo__donut-spinner {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: snippet-demo__donut-spin 1.2s linear infinite;
}
</style>

#### Giải thích
Sử dụng một `border` bán trong suốt cho toàn bộ phần tử, ngoại trừ một bên sẽ
phục vụ như là chỉ số tải cho banh quay tron. Sử dụng `animation` để xoay phần tử.
#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>

* https://caniuse.com/#feat=css-animation
* https://caniuse.com/#feat=transforms2d

<!-- tags: animation -->

### Dynamic shadow

Tạo một bóng tương tự như `shadow-box` nhưng dựa trên màu sắc của phần tử đó.
#### HTML

```html
<div class="dynamic-shadow-parent">
  <div class="dynamic-shadow"></div>
</div>
```

#### CSS

```css
.dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__dynamic-shadow-parent">
    <div class="snippet-demo__dynamic-shadow"></div>
  </div>
</div>

<style>
.snippet-demo__dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.snippet-demo__dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.snippet-demo__dynamic-shadow::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
</style>

#### Giải thích.
Đoạn mã đòi hỏi một trường hợp phức tạp của ngan xếp chồng để có được đúng, như vậy mà các phần tử giả
sẽ được đặt bên dưới phần tử cua chinh no trong khi vẫn nhìn thấy được.

1. `position: relative` thiết lập trong phan tu cha một ngữ cảnh định vị Cartesian cho các phần tử con.
2. `z-index: 1` thiết lập một ngữ cảnh xếp chồng mới.
3. `position: relative` trên phan tu con thiết lập một bối cảnh định vị cho các phần tử giả.
4. `::after` định nghĩa một phần tử giả..
5. `position: absolute`  lấy phần tử giả ra khỏi luong của tài liệu và định vị nó trong quan hệ với phan tu cha.
6. `width: 100%` and `height: 100%` kích cỡ phần tử giả để điền vào kích thước của cha  làm cho nó có kích thước bằng nhau.
7. `background: inherit` làm cho phần tử giả thừa kế gradient tuyến tính được xác định trên phần tử.
8. `top: 0.5rem` offsets phần tử giả giảm nhẹ từ cha của nó.
9. `filter: blur(0.4rem)` ẽ làm mờ phần tử giả de tạo sự xuất hiện của một cái bóng bên dưới.
10. `opacity: 0.7` làm cho phần tử giả mang một phần minh bạch.
11. `z-index: -1` định vị phần tử giả phía sau phan tu cha.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>

* https://caniuse.com/#feat=css-filters

<!-- tags: visual -->

### Easing variables 

Các biến có thể được sử dụng lại cho `transition-timing-function` thuoc tinh,nhieu tinh nang
mạnh mẽ hơn tích hợp sẵn `ease`, `ease-in`, `ease-out` and `ease-in-out`.

#### HTML

```html
<div class="easing-variables"></div>
```

#### CSS

```css
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.easing-variables {
  width: 50px;
  height: 50px;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}

.easing-variables:hover {
  transform: rotate(45deg);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__easing-variables">Hover</div>
</div>

<style>
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.snippet-demo__easing-variables {
  width: 75px;
  height: 75px;
  background: #333;
  color: white;
  font-size: 0.8rem;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 1s var(--ease-out-quart);
}

.snippet-demo__easing-variables:hover {
  transform: rotate(45deg);
}
</style>

#### Giải thích

Các biến được định nghĩa toàn cuc trong `: root` CSS pseudo-class la thu de noi với phần tử gốc của một cây đại diện cho tài liệu. Trong HTML, `: root` đại diện cho phần tử` <html> `và giống với trình chọn` html`, ngoại trừ tính cụ thể của nó cao hơn.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: animation -->

### Chữ khắc

Tạo ra một hiệu ứng mà văn bản xuất hiện để được "khắc" hoặc khắc vào nền.
#### HTML

```html
<p class="etched-text">I appear etched into the background.</p>
```

#### CSS

```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__etched-text">I appear etched into the background.</p>
</div>

<style>
.snippet-demo__etched-text {
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
  text-shadow: 0 2px 0 white;
}
</style>

#### Giải thích

`text-shadow: 0 2px white` tạo ra một bóng offset `0px` theo chiều ngang và `2px` theo chiều dọc
từ vị trí xuất phat.
Nền phải tối hơn bóng tối để hiệu ứng làm việc.
Màu văn bản nên hơi nhạt dần để làm cho nó trông giống như nó được khắc / khắc ra tren nen.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-textshadow

<!-- tags: visual -->

### Chia đều phần tử con.

Phân phối đều các phần tử con trong phần tử cha.
#### HTML

```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```

#### CSS

```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__evenly-distributed-children">
    <p>Item1</p>
    <p>Item2</p>
    <p>Item3</p>
  </div>
</div>

<style>
.snippet-demo__evenly-distributed-children {
  display: flex;
  width: 100%;  
  justify-content: space-between;
}
</style>

#### Giải thích.

1. `display: flex` cho phép uốn cong hop.
2. `justify-content: space-between` phân bố đều các phần tử con theo chiều ngang. Mục đầu tiên được đặt ở cạnh trái, trong khi mục cuối cùng được đặt ở cạnh bên phải.
Cách khác, sử dụng `justify-content: space-around` để phân phoi cho phan tu con có không gian xung quanh chúng, chứ không phải giữa chúng.
#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Needs prefixes for full support.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->

### Flexbox centering.

Theo chiều dọc và chiều dọc, phần tử con nằm trong phần tử cha sử dụng `flexbox`.
#### HTML

```html
<div class="flexbox-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__flexbox-centering">
    <p class="snippet-demo__flexbox-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích 

1. `display: flex` enables flexbox.
3. `align-items: center` centers the child vertically.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Needs prefixes for full support.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->

### Tô màu văn bản.

Làm cho 1 đoạn văn bản có màu.

#### HTML

```html
<p class="gradient-text">Gradient text</p>
```

#### CSS

```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__gradient-text">
    Gradient text
  </p>
</div>

<style>
.snippet-demo__gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  font-size: 2rem;
  font-weight: bold;
  margin: 0;
}
</style>

#### Giải thích

1. `background: -webkit-linear-gradient(...)` Tạo cho văn bản có nền màu.
2. `webkit-text-fill-color: transparent` điền văn bản với màu trong suốt.
3. `webkit-background-clip: text` clips the background with the text, filling the text with
   the gradient background as the color.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Uses non-standard properties.</span>

* https://caniuse.com/#feat=text-stroke

<!-- tags: visual -->

### Định vị lưới

Theo chiều dọc và chiều dọc, phần tử con nằm trong phần tử gốc sử dụng `grid`.

#### HTML

```html
<div class="grid-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-centering">
    <p class="snippet-demo__grid-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. `display: grid` Cho phép lưới.
2. `justify-content: center` tập trung phần tử con theo chiều ngang.
3. `align-items: center` tập trung phần tử con theo chiều dọc.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid### Grid layout

Bố trí trang web cơ bản sử dụng `grid`.

#### HTML

```html
<div class="grid-layout">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">
    Content
    <br>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
  </div>
  <div class="footer">Footer</div>
</div>
```

#### CSS

```css
.grid-layout {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    'sidebar header header'
    'sidebar content content'
    'sidebar footer  footer';
  color: white;
}
.grid-layout > div {
  background: #333;
  padding: 10px;
}
.sidebar {
  grid-area: sidebar;
}
.content {
  grid-area: content;
}
.header {
  grid-area: header;
}
.footer {
  grid-area: footer;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-layout">
    <div class="box snippet-demo__grid-layout__header">Header</div>
    <div class="box snippet-demo__grid-layout__sidebar">Sidebar</div>
    <div class="box snippet-demo__grid-layout__content">Content
      <br> Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </div>
    <div class="box snippet-demo__grid-layout__footer">Footer</div>
  </div>
</div>

<style>
.snippet-demo__grid-layout {
  margin: 1em;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "sidebar header header"
    "sidebar content content"
    "sidebar  footer  footer";
  background-color: #fff;
  color: white;
}
.snippet-demo__grid-layout > div {
  background: #333;
  padding: 10px;
}
.snippet-demo__grid-layout__sidebar {
    grid-area: sidebar;
}
.snippet-demo__grid-layout__content {
    grid-area: content;
}
.snippet-demo__grid-layout__header {
    grid-area: header;
}
.snippet-demo__grid-layout__footer {
    grid-area: footer;
}
</style>

#### Giải thích

1. `display: grid` cho phép dùng lưới.
2. `grid-gap: 10px` định nghĩa khoảng cách giữa các phần tử.
3. `grid-template-columns: repeat(3, 1fr)` định nghĩa 3 cột có cùng kích thước.
4. `grid-template-areas` định nghĩa tên của các vùng lưới.
5. `grid-area: sidebar` làm cho phần tử sử dụng vùng đó có tên `sidebar`.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->

### Đường xọc

Cung cấp cho một phần tử một đường xọc bằng 1 pixel của thiết bị gốc có chiều rộng, có thể nhìn được.

#### HTML

```html
<div class="hairline-border">text</div>
```

#### CSS

```css
.hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hairline-border">Text with a hairline border around it.</p>
</div>

<style>
.snippet-demo__hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
</style>

#### Giải thích

1. `box-shadow`, when only using spread, adds a pseudo-border which can use subpixels\*.
2. Use `@media (min-resolution: ...)` to check the device pixel ratio (`1dppx` equals 96 DPI),
   setting the spread of the `box-shadow` equal to `1 / dppx`.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ Needs alternate syntax and JavaScript user agent checking for full support.</span>

* https://caniuse.com/#feat=css-boxshadow
* https://caniuse.com/#feat=css-media-resolution

<hr>

\*Chrome does not support subpixel values on `border`. Safari does not support subpixel values on `box-shadow`. Firefox supports subpixel values on both.

<!-- tags: visual -->

### Gạch chân khi di chuột lên

Tạo ra một hiệu ứng gạch chân khi văn bản được hover qua.

<small>**Credit:** https://flatuicolors.com/</small>

#### HTML

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

#### CSS

```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hover-underline-animation">Hover this text to see the effect!</p>
</div>

<style>
.snippet-demo__hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.snippet-demo__hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.snippet-demo__hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>

#### Giải thích

1. `display: inline-block` làm cho khối `p` và `inline-block` ngăn bị gạch dưới từ  việc kéo dài chiều dài của cha nó hơn nội dung (Văn bản).
2. `position: relative` on the element establishes a Cartesian positioning context for pseudo-elements.
3. `::after` định nghĩa một phần tử giả.
4. `position: absolute` lấy phần tử giả ra khỏi dòng của tài liệu và định vị nó trong quan hệ với cha.
5. `width: 100%` đảm bảo phần tử mẫu trải dài toàn bộ chiều rộng của khối.
6. `transform: scaleX(0)` initially scales the pseudo element to 0 so it has no width and is not visible.
7. `bottom: 0` and `left: 0` đặt nó ở góc dưới trái của khối.
8. `transition: transform 0.25s ease-out` có nghĩa là thay đổi `transform`  sẽ được chuyển trong 0.25 giấy với hàm tính giờ `ease-out`.
9. `transform-origin: bottom right` nghĩa là thay đổi điểm neo là đặt tại góc dưới bên phải khối
10. `:hover::after` rồi dùng `scaleX(1)` để thay đổi chiều rộng đến 100%,rồi thay đổi `transform-origin`
    đến `bottom left` để điểm neo được đảo ngược, cho phép nó chuyển tiếp theo một hướng khác khi over ra.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=transforms2d
* https://caniuse.com/#feat=css-transitions

<!-- tags: animation -->

### Dốc theo sau con trỏ chuột.

hover chuột có hiệu ứng dốc theo sau.

<small class="snippet__credit">**Credit:** [Tobias Reich](https://codepen.io/electerious/pen/MQrRxX)</small>

#### HTML

```html
<button class="mouse-cursor-gradient-tracking">
  <span>Hover me</span>
</button>
```

#### CSS

```css
.mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.mouse-cursor-gradient-tracking span {
  position: relative;
}

.mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, pink, transparent);
  transform: translate(-50%, -50%);
  transition: width 0.2s ease, height 0.2s ease;
}

.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

#### JavaScript

```js
var btn = document.querySelector('.mouse-cursor-gradient-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```

#### Demo

<div class="snippet-demo">
  <button class="snippet-demo__mouse-cursor-gradient-tracking">
    <span>Hover me</span>
  </button>
</div>

<style>
.snippet-demo__mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.snippet-demo__mouse-cursor-gradient-tracking span {
  position: relative;
}

.snippet-demo__mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, aqua, rgba(0,255,255,0.0001));
  transform: translate(-50%, -50%);
  transition: width .2s ease, height .2s ease;
}

.snippet-demo__mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
</style>

<script>
(function () {
  var btn = document.querySelector('.snippet-demo__mouse-cursor-gradient-tracking')
  btn.onmousemove = function (e) {
    var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
    var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
    btn.style.setProperty('--x', x + 'px')
    btn.style.setProperty('--y', y + 'px')
  }
})()
</script>

#### Giải thích

_TODO_

**Chú ý !**

Nếu thuộc tính cha có thuộc tính đinh vị nội dung (`position: relative`), bạn sẽ cần khử nó thật tốt.

```js
var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
```

#### Trình duyệt hỗ trợ.

<div class="snippet__requires-javascript">Requires JavaScript</div>
<span class="snippet__support-note">⚠️ Requires JavaScript.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: visual, interactivity -->

### :không chọn

The `:not` bộ chọn chèn rất hữu ích cho kiểu dáng một nhóm các yếu tố, trong khi để nguyên tố cuối cùng (hoặc được chỉ định) không bị xáo trộn.

#### HTML

```html
<ul class="css-not-selector-shortcut">
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
  <li>Four</li>
  <li>Five</li>
</ul>
```

#### CSS

```css
.css-not-selector-shortcut {
  display: flex;
}

li {
  list-style-type: none;
  margin: 0;
  padding: 0 0.75rem;
}

li:not(:last-child) {
  border-right: 2px solid #d2d5e4;
}
```

#### Demo

<div class="snippet-demo">
  <ul class="snippet-demo__css-not-selector-shortcut">
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
    <li>Five</li>
  </ul>
</div>

<style>
.snippet-demo__css-not-selector-shortcut {
  display: flex;
  padding: 0;
}

.snippet-demo__css-not-selector-shortcut li {
  list-style-type: none;
  margin: 0;
  padding: 0 0.75rem;
}

.snippet-demo__css-not-selector-shortcut li:not(:last-child) {
  border-right: 2px solid #d2d5e4
}
</style>

#### Giải thích

`li:not(:last-child)` xác định rằng các phong cách nên áp dụng cho tất cả thành phần `li` ngoại trử thẻ con `:last-child`.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-sel3

<!-- tags: visual -->

### Cuộn tràn dốc.

Thêm dốc cho một phần tử tràn để biểu thị tốt hơn có nhiều nội dung cần được cuộn lại.

#### HTML

```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Content to be scrolled
  </div>
</div>
```

#### CSS

```css
.overflow-scroll-gradient {
  position: relative;
}
.overflow-scroll-gradient::after {
  content: '';
  position: absolute;
  bottom: 0;
  width: 240px;
  height: 25px;
  background: linear-gradient(
    rgba(255, 255, 255, 0.001),
    white
  ); /* transparent keyword is broken in Safari */
  pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__overflow-scroll-gradient">
    <div class="snippet-demo__overflow-scroll-gradient__scroller">
      Content to be scrolled
    </div>
  </div>
</div>

<style>
.snippet-demo__overflow-scroll-gradient {
  position: relative;
}
.snippet-demo__overflow-scroll-gradient::after {
  content: '';
  background: linear-gradient(rgba(255, 255, 255, 0.001), white);
  position: absolute;
  width: 240px;
  height: 25px;
  bottom: 0;
  pointer-events: none;
}
.snippet-demo__overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
</style>

<script>
document.querySelector('.snippet-demo__overflow-scroll-gradient__scroller').innerHTML = 'content '.repeat(100)
</script>

#### Giải thích

1. `position: relative` trên cha thiết lập một ngữ cảnh định vị Descartes cho các phần tử giả.
2. `::after` định nghĩa một phần tử giả.
3. `background-image: linear-gradient(...)` adds a linear gradient that fades from transparent to white
   (top to bottom).
4. `position: absolute` lấy phần tử giả ra khỏi dòng chảy của tài liệu và định vị nó trong quan hệ với cha.
5. `width: 240px` phù hợp với kích thước của phần tử cuộn.
6. `height: 25px` là chiều cao của phần tử giả mờ , cần được giữ ở mức tương đối nhỏ.
7. `bottom: 0` định vị phần tử giả ở dưới cùng của cha.
8. `pointer-events: none` xác định rằng phần tử giả không thể là một mục tiêu của sự kiện chuột, cho phép văn bản đằng sau nó vẫn có thể được lựa chọn / tương tác.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->

### Bật ra menu

Menu bật ra khi hover chuột.

#### HTML

```html
<div class="reference">
  <div class="popout-menu">
    Popout menu
  </div>
</div>
```

#### CSS

```css
.reference {
  position: relative;
}
.popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
}
.reference:hover > .popout-menu {
  visibility: visible;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reference">
    <div class="snippet-demo__popout-menu">
      Popout menu
    </div>
  </div>
</div>

<style>
.snippet-demo__reference {
  background: linear-gradient(135deg, #ff4c9f, #ff7b74);
  height: 75px;
  width: 75px;
  position: relative;
  will-change: transform;
}
.snippet-demo__popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
  background: #333;
  color: white;
  font-size: 0.9rem;
  padding: 0.4rem 0.8rem;
  width: 100px;
  text-align: center;
}
.snippet-demo__reference:hover > .snippet-demo__popout-menu {
  visibility: visible;
}
</style>

#### Giải thích.

1. `position: relative` thiết lập bối cảnh định vị cho con nó.
2. `position: absolute` lấy phần tử giả ra khỏi dòng chảy của tài liệu và định vị nó trong quan hệ với cha.
3. `left: 100%` di chuyển menu 100% theo chiều ngang của cha từ bên trái
4. `visibility: hidden` ẩn menu popout ban đầu và cho phép chuyển tiếp (unlike `display: none`).
5. `.reference:hover > .popout-menu`có nghĩa là khi `.reference` được hover qua , Chọn ngay
   children với 1 lớp của `.popout-menu` và thay đổi chúng `visibility` đến `visible`, trong đó hiển thị popout.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: interactivity -->

### Gạch chân văn bản đẹp.

Một sự thay thế đẹp hơn cho `text-decoration: underline` nơi những người hạ sĩ không gạch dưới.
thực hiện tự động giống `text-decoration-skip-ink: auto` nhưng nó có ít kiểm soát hơn gạch dưới.

#### HTML

```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```

#### CSS

```css
.pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px;
  text-shadow: 1px 1px 0 #f5f6f9, -1px 1px 0 #f5f6f9, -1px -1px 0 #f5f6f9, 1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}
.pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
.pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__pretty-text-underline">Pretty text underline without clipping descending letters.</p>
</div>

<style>
.snippet-demo__pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px !important;
  text-shadow: 1px 1px 0 #f5f6f9,
    -1px 1px 0 #f5f6f9,
    -1px -1px 0 #f5f6f9,
    1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}

.snippet-demo__pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}

.snippet-demo__pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
</style>

#### Giải thích

1. `text-shadow: ...` có 4 giá trị được đặt lại giá trị 4x4 px để đảm bảo gạch dưới
    có một cái bóng "dày" để thay đổi mỗi dòng nơi mà dấu gạch dưới kẹp dưới nó. Sử dụng màu
    phù hợp với nền. Đối với phông chữ lớn hơn, sử dụng kích thước `px` lớn hơn.
2. `background-image: linear-gradient(...)`tạo ra một gradient 90deg với 
    màu văn bản hiện tại (`currentColor`).
3. `background- *` thuộc tính kích thước gradient như 1x1px ở dưới cùng và lặp lại nó dọc theo trục x.
4. Bộ chọn giả `:: selection` đảm bảo rằng bóng văn bản không can thiệp vào văn bản
    lựa chọn.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ The distance of the underline from the text depends on the internal metrics of a font, so you must ensure everyone sees the same font (i.e. no system fonts which will change based on the OS).</span>

* https://caniuse.com/#feat=css-textshadow
* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->

### Reset tất style.

Đặt lại tất cả các kiểu cho các giá trị mặc định với một thuộc tính. Điều này sẽ không ảnh hưởng đến `direction` và` unicode-bidi`.
#### HTML

```html
<div class="reset-all-styles">
  <h4>Title</h4>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
.reset-all-styles {
  all: initial;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reset-all-styles">
    <h3>Title</h3>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
  </div>
</div>

<style>
.snippet-demo__reset-all-styles {
  all: initial;
}
</style>

#### Giải thích.

Thuộc tính `all` cho phép bạn đặt lại tất cả các kiểu (kế thừa hoặc không) thành các giá trị mặc định.
#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">⚠️ MS Edge status is under consideration.</span>

* https://caniuse.com/#feat=css-all

<!-- tags: visual -->

### Tách hình.

Sử dụng một hình dạng SVG để tách hai khối khác nhau để tạo ra một hình ảnh thú vị hơn so với sự phân chia ngang theo tiêu chuẩn.

#### HTML

```html
<div class="shape-separator"></div>
```

#### CSS

```css
.shape-separator {
  position: relative;
  height: 48px;
  background: #333;
}
.shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
```

#### Demo

<div class="snippet-demo is-distinct">
  <div class="snippet-demo__shape-separator"></div>
</div>

<style>
.snippet-demo__shape-separator {
  position: relative;
  height: 48px;
  margin: -0.75rem -1.25rem;
}
.snippet-demo__shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
</style>

#### Giải thích.

1. `position: relative`  trên phần tử thiết lập một ngữ cảnh định vị Descartes cho các phần tử giả.
2. `::after` định nghĩa một phần tử giả.
3. `background-image: url(...)`thêm hình SVG (hình tam giác 24x24 ở định dạng cơ sở64) làm hình nền
    của phần tử giả, lặp lại theo mặc định. Nó phải có màu sắc tương tự như khối đang được
    phân chia. 
4. `position: absolute` lấy phần tử giả ra khỏi luồng của tài liệu và định vị nó trong quan hệ với phần tử cha.
5. `width: 100%` đảm bảo phần tử trải dài toàn bộ chiều rộng của cha.
6. `height: 24px`là chiều cao tương tự như hình dạng.
7. `bottom: 0` 
57/5000
định vị phần tử giả ở dưới cùng của cha mẹ.

#### Trình duyệt hỗ trợ.

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=svg

<!-- tags: visual -->

### Cùng loại mở dần.

Mở các thành phần cùng loại khi nó được hover.

#### HTML

```html
<div class="sibling-fade">
  <span>Item 1</span>
  <span>Item 2</span>
  <span>Item 3</span>
  <span>Item 4</span>
  <span>Item 5</span>
  <span>Item 6</span>
</div>
```

#### CSS

```css
span {
  padding: 0 1rem;
  transition: opacity 0.2s;
}

.sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
```

#### Demo

<div class="snippet-demo">
  <nav class="snippet-demo__sibling-fade">
    <span>Item 1</span>
    <span>Item 2</span>
    <span>Item 3</span>
    <span>Item 4</span>
    <span>Item 5</span>
    <span>Item 6</span>
  </nav>
</div>

<style>
.snippet-demo__sibling-fade {
  cursor: default;
  line-height: 2;
  vertical-align: middle;
}

.snippet-demo__sibling-fade span {
  padding: 1rem;
  transition: opacity 0.2s;
}

.snippet-demo__sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
</style>

#### Explanation

1. `transition: opacity 0.2s` chỉ định rằng thay đổi độ mờ đục sẽ được chuyển tiếp trong 0.2 giây.
2. `.sibling-fade: hover span: not (: hover)` chỉ ra rằng khi cha mẹ được hovered, chọn bất kỳ `span` con
    hiện không được hovered và thay đổi độ mờ của chúng thành `0.5`.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-sel3
* https://caniuse.com/#feat=css-transitions

<!-- tags: interactivity -->

### System font stack

Sử dụng phông chữ bản địa của hệ điều hành để có được cảm nhận gần giống với ứng dụng gốc.
#### HTML

```html
<p class="system-font-stack">This text uses the system font.</p>
```

#### CSS

```css
.system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__system-font-stack">This text uses the system font.</p>
</div>

<style>
.snippet-demo__system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial, sans-serif;
}
</style>

#### Explanation

Trình duyệt tìm kiếm mỗi phông chữ liên tiếp, thích đầu tiên nếu có thể, và
quay trở lại kế tiếp nếu nó không thể tìm thấy phông chữ (trên hệ thống hoặc được định nghĩa trong CSS).

1. `-apple-system` là San Francisco, được sử dụng trên iOS và macOS (không phải là Chrome)
2. `BlinkMacSystemFont` là San Francisco, được sử dụng trên macOS Chrome
3. `Segoe UI` được sử dụng trên Windows 10
4. Roboto được sử dụng trên Android
5. `Oxygen-Sans` được sử dụng trên GNU + Linux
6. `Ubuntu` được sử dụng trên Linux
7. `" Helvetica Neue "" và "Helvetica" được sử dụng trên macOS 10.10 và phiên bản dưới đây (được bao bọc bởi dấu ngoặc kép bởi vì nó có khoảng trắng)
8. `Arial` là một font được hỗ trợ rộng rãi bởi tất cả các hệ điều hành
9. `sans-serif` là phông chữ sans-serif fallback nếu không có phông chữ nào được hỗ trợ

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->

### Triangle

Creates a triangle shape with pure CSS.

#### HTML

```html
<div class="triangle"></div>
```

#### CSS

```css
.triangle {
  width: 0;
  height: 0;
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__triangles">
    <div class="snippet-demo__triangle snippet-demo__triangle-1"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-2"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-3"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-4"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-5"></div>
  </div>
</div>

<style>
.snippet-demo__triangles {
  display: flex;
  align-items: center;
}

.snippet-demo__triangle {
  display: inline-block;
  width: 0;
  height: 0;
  margin-right: 0.25rem;
}

.snippet-demo__triangle-1 {
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-2 {
  border-bottom: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-3 {
  border-left: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-4 {
  border-right: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-5 {
  border-top: 40px solid #333;
  border-left: 15px solid transparent;
  border-right: 15px solid transparent;
}
</style>

#### Explanation

[View this link for a detailed explanation.](https://stackoverflow.com/q/7073484)
Màu của đường viền là màu của tam giác. Phía đỉnh điểm tam giác
tương ứng với thuộc tính `border- *` ngược lại. Ví dụ: màu trên `border-top`
có nghĩa là mũi tên xuống.

Thử nghiệm với các giá trị `px` để thay đổi tỷ lệ tam giác.
#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->

### Truncate text


88/5000
Nếu văn bản dài hơn một dòng, nó sẽ được cắt ngắn và kết thúc bằng một dấu chấm phẩy '... `.
#### HTML

```html
<p class="truncate-text">If I exceed one line's width, I will be truncated.</p>
```

#### CSS

```css
.truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__truncate-text">
    This text will be truncated if it exceeds 200px in width.
  </p>
</div>

<style>
.snippet-demo__truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
  margin: 0;
}
</style>

#### Explanation

1. `overflow: hidden` ngăn văn bản tràn lên kích thước của nó
    (đối với một khối, chiều rộng 100% và chiều cao tự động).
2. `trắng-không gian: nowrap` ngăn chặn các văn bản từ vượt quá một chiều cao.
3. `text-overflow: dấu chấm lửng 'làm cho nó để nếu văn bản vượt quá kích thước của nó, nó
    sẽ kết thúc bằng một dấu chấm lửng.
4. `width: 200px;` đảm bảo rằng phần tử có một chiều, để biết khi nào có dấu chấm lửng

#### Browser support

<span class="snippet__support-note">⚠️ Only works for single line elements.</span>

* https://caniuse.com/#feat=text-overflow

<!-- tags: layout -->


