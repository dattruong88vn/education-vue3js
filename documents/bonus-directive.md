## Bonus Directive

#### v-once

Render HTML element 1 lần duy nhất, những lần render sau sẽ sử dụng static content và bỏ qua element này.

Vue sẽ skip tất cả các element có thuộc tính v-once khi kiểm tra khác biệt trong DOM ảo, từ đó tăng performance cho application.

#### v-pre

Vue sẽ skip compile những element tương ứng có chưa thuộc tính `v-pre`
