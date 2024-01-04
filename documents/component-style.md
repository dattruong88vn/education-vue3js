## Component Style

#### Đặc điểm

1. Mặc định, style trong Component sẽ được apply thành global style. Nếu Component Cha và Con cùng style thì sẽ apply của Con trước Cha sau.
2. Thuộc tính `scoped` trong thẻ `style` đảm bảo style chỉ được apply cho đúng duy nhất Component mà nó được khai báo và duy nhất `root element` của component con.
3. Đối với trường hợp sử dụng `slot` để nhúng content vào component con, style của component cha luôn luôn được apply.

Ví dụ:

Trường hợp ko có thuộc tính scoped:

- Cha: <style> --> apply Global
- Con: <style> --> apply Global
  --> Cha override Con

Trường hợp có `scoped`:

- Cha có `<style scoped>`: apply Cha và `root element` của Con
