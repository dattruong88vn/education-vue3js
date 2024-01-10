## LIFE CYCLE HOOK

Vue Component trải qua 4 phase khác nhau:

- Creation
- Mounting
- Updating
- Unmounting

Life Cycle Hook là những method cho phép developer có thể can thiệp vào các thời điểm khác nhau trong các phase của Vue Component và thực thị code mong muốn.

#### Creation Phase

Đây là thời điểm Component được tạo ra.

Có 2 methods trong phase này là `beforeCreate()` và `created()`.

Các thành phần như `data properties`, `computed`, `methods` hay `watchers` chỉ sẵn sàng trong method `created()`. Do vậy `created()` là methods được sử dụng phổ biến và rộng rãi trong các project.

Áp dụng:

- `beforeCreate()`:
- `created()` cũng là nơi tốt nhất để call API khi component được render lần đầu tiên.

#### Mouting Phase

Trong phase này, component template (hay html) được mounted vào DOM để hiển thị ra UI cho người dùng.

Methods: `beforeMount` và `mounted`. Trong đó `mounted` là method được sử dụng nhiều hơn vì nó thực thi sau khi DOM đã được hình thành, có thể access đến các node.

Áp dụng:

- `beforeMount()`:
- `mounted()`: focus vào một thẻ input

#### Updating Phase

Phase này được thực hiện khi có một `reactive property` (như data property hoặc computed property) được sử dụng trong component thay đổi giá trị hoặc component re-render.

Có 2 methods:

`beforeUpdate`:

- Thực thi khi giá trị của property đã thay đổi nhưng chưa được update lên DOM node.
- Áp dụng: access và DOM node trước khi được update hoặc remove event-listener trên các element.

`updated`

- Thực thi khi các thay đội đã được cập nhật lên DOM.
- Áp dụng: Tương tự như `mounted`

#### Unmounting Phase

Thực thi khi Component được remove ra khỏi DOM.

2 methods:

`beforeUnmount`:

- Thực thi trước khi Component được remove khỏi DOM.
- Áp dụng: cancel API request, remove event listener, clear timer...

#### Một số Hooks còn lại

`activated`, `deactivated`:

- liên quan đến `keep-alive` component khi làm việc với dynamic component `<component to=""></component>
- Được call khi component được keep-alive activated và deactivated.

`errorCaptured`:

- Đươc call khi có bất cứ component nào render bị lỗi.
- Set một flag error = true trong component này, đồng thời hiển thị fallback UI để tăng trải nghiệm người dùng.
- Tương tự `ErrorBoundaries` trong React.

`renderTracked`, `renderTrigger`:

- Được sử dụng cho mục đích debugging.
- Áp dụng: xác định nguyên nhân khiến Component re-renders.
