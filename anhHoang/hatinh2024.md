# A. Truy vấn đổi hướng cạnh

## Đề bài

Cho đồ thị đầy đủ có hướng $n$ đỉnh. Ban đầu mỗi cặp $(u, v)$ với $1 \leq u < v \leq n$ có một cạnh nối có hướng từ $u$ đến $v$. Có $q$ truy vấn, mỗi truy vấn sẽ thay đổi hướng một cạnh $(u, v)$, nếu cạnh đang có hướng từ $u$ đến $v$ thì sẽ đổi lại thành từ $v$ sang $u$, hoặc ngược lại. 

Sau mỗi lần đổi hướng cạnh, hãy đếm số bộ ba $(a, b, c)$ mà:
- Có cạnh từ $a$ đến $b$,
- Có cạnh từ $b$ đến $c$,
- Có cạnh từ $c$ đến $a$.

## Dữ liệu vào

- Dòng đầu chứa số $n, q$ ($1 \leq n \leq 2 \cdot 10^5$, $1 \leq q \leq 10^6$).
- $q$ dòng tiếp theo, mỗi dòng chứa hai số $u, v$ mô tả cạnh bị đổi hướng.

## Dữ liệu ra

Với mỗi truy vấn, đưa ra một dòng là số bộ ba $(a, b, c)$ thỏa mãn.

## Subtasks

1. (15 điểm): $n, q \leq 100$.
2. (20 điểm): $n \leq 100$.
3. (25 điểm): $n \leq 2000$.
4. (40 điểm): Không có ràng buộc gì thêm.

## Sample Input

    4 4
    1 2
    2 4
    2 3
    4 2

## Sample Output

    0
    2
    2
    1

## Giải thích

- Sau truy vấn 1: Không có bộ ba nào thỏa mãn.
- Sau truy vấn 2: Các bộ ba thỏa mãn là $(1, 2, 4)$ và $(2, 3, 4)$.
- Sau truy vấn 3: Các bộ ba thỏa mãn là $(1, 2, 4)$ và $(1, 2, 3)$.
- Sau truy vấn 4: Chỉ còn một bộ ba thỏa mãn là $(1, 2, 3)$.

# B. Gần bằng nhau

## Đề bài

Hai tập multiset $A$ và $B$ được gọi là gần bằng nhau nếu kích thước bằng nhau và chỉ cần thay đổi giá trị của một phần tử của tập $A$ thì ta được tập $B$.

Cho hai dãy số nguyên $a_1, a_2, \ldots, a_n$ và $b_1, b_2, \ldots, b_n$ thỏa mãn $a_i \geq b_i$. Xét tập $A = \{a_1, a_2, \ldots, a_i\}$ và $B = \{b_1, b_2, \ldots, b_i\}$, hãy thực hiện ít thao tác chọn một phần tử của tập $A$ giảm đi $1$ đơn vị để hai tập $A, B$ là gần bằng nhau, với $1 \leq i \leq n$.

## Dữ liệu vào

- Dòng đầu chứa số $T$ là số lượng test case, $T$ nhóm dòng tiếp theo:
  - Dòng đầu chứa số $n$ $(1 \leq n \leq 2 \cdot 10^5)$.
  - Dòng thứ hai chứa $n$ số $a_i$ $(1 \leq a_i \leq 10^9)$.
  - Dòng thứ ba chứa $n$ số $b_i$ $(1 \leq b_i \leq a_i)$.

Dữ liệu đảm bảo tổng $n$ không quá $2 \cdot 10^5$.

## Dữ liệu ra

Với mỗi test, ghi ra trên một dòng gồm $n$ số là kết quả tương ứng với mỗi $i$ từ 1 đến $n$.

## Giới hạn

- (15 điểm): $n \leq 100$.
- (15 điểm): $n \leq 500$.
- (25 điểm): $n \leq 3000$.
- (15 điểm): $a_i \leq b_{i+1}$.
- (15 điểm): $a_i \leq a_{i+1}; b_i \leq b_{i+1}$.
- (15 điểm): Không có ràng buộc gì thêm.

## Sample Input

    2
    2
    4 5
    2 3
    2
    4 5
    2 4

## Sample Output

    0 1 
    0 0 

## Giải thích

- Test case 1: $A = \{4, 5\}$ và $B = \{2, 3\}$.
    - Với $i=1$, tập $\{4\}$ và $\{2\}$ đã gần bằng nhau.
    - Với $i=2$, ta giảm $4$ thành $3$ để $A = \{3, 5\}$ và $B = \{2, 3\}$.

# C. Thứ tự duyệt cây

## Đề bài

Cho cây nhị phân $n$ đỉnh có gốc là $1$, mỗi đỉnh $u$ có đỉnh con trái là $l_u$ và đỉnh con phải là $r_u$. Với mỗi đỉnh $u$ có một trọng số $c_u$, ban đầu tất cả $c_u = -1$.  

Dãy thứ tự $s$ của các đỉnh của cây đã cho được xác định đệ quy như sau:  
- Nếu duyệt đến đỉnh $u$:  
  - Nếu $c_u = -1$: Thêm $u$ vào cuối $s$, sau đó đệ quy tới $l_u$ rồi đệ quy tới $r_u$.  
  - Nếu $c_u = 0$: Đệ quy tới $l_u$, sau đó thêm $u$ vào cuối $s$, rồi đệ quy tới $r_u$.  
  - Nếu $c_u = 1$: Đệ quy tới $l_u$, rồi đệ quy tới $r_u$, sau đó thêm $u$ vào cuối $s$.  

Lưu ý: Chỉ đệ quy tới $l_u$ hoặc $r_u$ nếu chúng khác $0$.

Có $q$ truy vấn thuộc một trong hai loại sau:  
1. `1 l r v`: Gán $c_i = v$ với $l \leq i \leq r$.  
2. `2 i`: Hỏi cây hiện tại, đỉnh $i$ nằm ở vị trí nào trong danh sách $s$.

## Dữ liệu vào

- Dòng đầu chứa hai số $n, q$ $(1 \leq n, q \leq 10^5)$.  
- $n$ dòng tiếp theo, dòng thứ $u$ chứa hai số $l_u, r_u$ $(0 \leq l_u, r_u \leq n)$. Dữ liệu đảm bảo cây là cây nhị phân.  
- $q$ dòng tiếp theo, mỗi dòng mô tả một trong hai truy vấn:
  - `1 l r v` $(1 \leq l \leq r \leq n; -1 \leq v \leq 1)$
  - `2 i` $(1 \leq i \leq n)$.

## Dữ liệu ra

- Với mỗi truy vấn loại 2, ghi ra một dòng là vị trí của đỉnh $i$ trong danh sách $s$.

## Giới hạn

- $1 \leq n, q \leq 10^5$.
- Dữ liệu đảm bảo đầu vào là một cây nhị phân hợp lệ.

## Sample Input

    5 5
    3 4
    0 0
    5 2
    0 0
    0 0
    2 2
    1 1 3 1
    2 4
    1 3 3 0
    2 5


## Sample Output

    4
    4
    1

## Giải thích

- Ban đầu, dãy $s = [1, 3, 5, 2, 4]$. Do đó $2$ nằm ở vị trí $4$.
- Sau truy vấn `1 1 3 1`, dãy $s = [5, 2, 3, 4, 1]$. Do đó $4$ nằm ở vị trí $4$.
- Sau truy vấn `1 3 3 0`, dãy $s = [5, 3, 2, 4, 1]$. Do đó $5$ nằm ở vị trí $1$.

# D. Đoạn tốt

## Đề bài

Cho dãy $a_1, a_2, \ldots, a_n$. Hãy trả lời $q$ truy vấn, mỗi truy vấn xét dãy con $a_l, a_{l+1}, \ldots, a_r$, hãy đếm xem có bao nhiêu đoạn con tạo thành dãy $b$ với $b_1 = a_i, b_2 = a_{i+1}, \ldots, b_j = a_j$ với $l \leq i \leq j \leq r$ mà thỏa mãn $b_t \mod t = 0$ với mọi $1 \leq t \leq j - i + 1$.

## Dữ liệu vào

- Dòng đầu chứa số $T$ $(1 \leq T \leq 10)$ là số lượng test con.
- Tiếp theo là $T$ nhóm dòng, mỗi nhóm gồm:
  - Dòng đầu chứa số $n$ $(1 \leq n \leq 10^5)$.
  - Dòng thứ hai chứa $n$ số $a_i$ $(1 \leq a_i \leq 10^{18})$.
  - Dòng thứ ba chứa số $q$ $(1 \leq q \leq 10^5)$.
  - $q$ dòng tiếp theo, mỗi dòng chứa hai số $l, r$ $(1 \leq l \leq r \leq n)$ mô tả các truy vấn.

## Dữ liệu ra

Với mỗi truy vấn, đưa ra kết quả trên một dòng.

## Giới hạn

1. (10 điểm): $n, q \leq 200$.
2. (20 điểm): $n \leq 2000$.
3. (30 điểm): $a_i \leq 10^6$.
4. (40 điểm): Không có ràng buộc gì thêm.

## Sample Input

    1
    5
    6 8 10 6 24
    3
    1 3
    1 5
    2 4

## Sample Output

    5
    12
    6

## Giải thích

- Truy vấn $1$: Có $5$ đoạn con thỏa mãn: $[6], [8], [10], [6, 8], [8, 10]$.

# E. Đỉnh DFS thứ k

## Đề bài

Cho cây $n$ đỉnh đánh số từ $1$ đến $n$, có gốc là đỉnh $1$. $c[u]$ là tập các đỉnh con trực tiếp của $u$. Cho số nguyên $k$, với đoạn mã dưới đây, hãy cho biết những đỉnh nào có thể nằm ở vị trí $a[k - 1]$.

Đoạn mã C++:

```cpp
vector<int> a, b;

void DFS(int u, vector<int> c[]) {
    a.push_back(u);
    for (auto v : c[u]) {
        DFS(v, c);
    }
}

int solve(int n, int k, vector<int> c[]) {
    for (int u = 1; u <= n; u++) {
        random_shuffle(c[u].begin(), c[u].end());
    }
    a.clear();
    DFS(1, c);
    cout << a[k - 1];
}
```

Giải thích một số thuật ngữ trong đề bài:

- Cây: Là đồ thị liên thông, không có chu trình.
- DFS (Depth First Search): Thuật toán duyệt đồ thị theo chiều sâu.
- random_shuffle: Hàm trộn ngẫu nhiên các phần tử trong mảng.

## Dữ liệu vào

- Dòng đầu chứa hai số nguyên $n, k$ $(1 \leq k \leq n \leq 10^4)$.
- $n - 1$ dòng tiếp theo, mỗi dòng chứa hai số $u, v$ mô tả cây có cạnh nối đỉnh $u$ với $v$ $(1 \leq u, v \leq n)$.

## Dữ liệu ra

- Ghi ra chỉ số của các đỉnh thoả mãn, ghi ra theo chỉ số tăng dần.

## Giới hạn

- $1 \leq k \leq n \leq 10^4$
- Cây có $n - 1$ cạnh nối.

## Subtasks

1.	(10 điểm): $n \leq 10$
2.	(40 điểm): $n \leq 500$
3.	(30 điểm): $n \leq 4000$
4.	(20 điểm): Không có ràng buộc gì thêm.

## Sample Input

    8 5
    1 2
    1 3
    2 5
    2 6
    3 7
    4 1
    5 8


## Sample Output

    2 5 6 8 

# F. Cóc nhảy

## Đề bài

Cho $n$ điểm trên trục $Ox$, một con cóc sẽ nhảy qua hết $n$ điểm theo quy tắc sau: nếu nó đang ở điểm $p$ thì nó sẽ nhảy sang điểm gần nhất mà nó chưa đứng ở điểm đó. Nếu có hai điểm có cùng khoảng cách nhỏ nhất thì nó sẽ nhảy sang điểm có tọa độ nhỏ hơn.

Hãy cho biết điểm cuối cùng mà con cóc nhảy đến nếu ban đầu nó đứng ở điểm $s$ với mọi $0 \leq s < n$.

## Dữ liệu vào

- Dòng đầu chứa số nguyên $n$ $(2 \leq n \leq 10^6)$.
- Dòng thứ hai chứa $n$ số $x_i$ $(1 \leq x_i \leq 10^{12}; x_i < x_{i+1})$, là tọa độ của $n$ điểm.

## Dữ liệu ra

- Ghi ra $n$ số tương ứng với kết quả của $s$ từ $0$ đến $n-1$.

## Giới hạn

- $2 \leq n \leq 10^6$
- $1 \leq x_i \leq 10^{12}$
- Các tọa độ $x_i$ khác nhau và tăng dần.

## Subtasks

1. (30 điểm): $n \leq 1000$
2. (30 điểm): $n \leq 10^5$
3. (40 điểm): Không có ràng buộc gì thêm.

## Sample Input

    5
    2 5 6 8 11

## Sample Output

    4 0 4 4 0

## Giải thích

**Dạng nhảy của con cóc:**

- Nếu bắt đầu ở $s = 0$: Con cóc lần lượt nhảy từ điểm $2 \to 5 \to 6 \to 8 \to 11$. Kết quả cuối cùng là điểm $4$ (tọa độ $11$).
- Nếu bắt đầu ở $s = 1$: Con cóc lần lượt nhảy từ điểm $5 \to 6 \to 8 \to 11 \to 2$. Kết quả cuối cùng là điểm $0$ (tọa độ $2$).
- Nếu bắt đầu ở $s = 2$: Con cóc lần lượt nhảy từ điểm $6 \to 5 \to 2 \to 8 \to 11$. Kết quả cuối cùng là điểm $4$ (tọa độ $11$).
- Nếu bắt đầu ở $s = 3$: Con cóc lần lượt nhảy từ điểm $8 \to 6 \to 5 \to 2 \to 11$. Kết quả cuối cùng là điểm $4$ (tọa độ $11$).
- Nếu bắt đầu ở $s = 4$: Con cóc lần lượt nhảy từ điểm $11 \to 8 \to 6 \to 5 \to 2$. Kết quả cuối cùng là điểm $0$ (tọa độ $2$).

# G. Kiểm tra di chuyển

## Đề bài

Cho đồ thị **có hướng** $n$ đỉnh và $n - 1$ cạnh có dạng vô hướng tạo thành một cây. Cho $q$ truy vấn, mỗi truy vấn gồm hai đỉnh $s$ và $t$, bạn cần kiểm tra xem có thể di chuyển từ $s$ đến $t$ được hay không.

## Dữ liệu vào

- Dòng đầu chứa số nguyên $n$ $(1 \leq n \leq 3 \cdot 10^5)$.
- $n - 1$ dòng tiếp theo, mỗi dòng chứa hai số nguyên $u, v$ $(1 \leq u, v \leq n; u \neq v)$ mô tả cạnh nối từ $u$ đến $v$.
- Dòng tiếp theo chứa số nguyên $q$ $(1 \leq q \leq 3 \cdot 10^5)$.
- $q$ dòng tiếp theo, mỗi dòng chứa hai số nguyên $s, t$ $(1 \leq s, t \leq n)$ mô tả các truy vấn.

## Dữ liệu ra

- Ghi ra một xâu gồm $q$ kí tự `'0'` hoặc `'1'` tương ứng kết quả của $q$ truy vấn:
  - Ghi `'1'` nếu có thể di chuyển từ $s$ đến $t$.
  - Ngược lại ghi `'0'`.

## Giới hạn

- $1 \leq n \leq 3 \cdot 10^5$
- Mỗi cạnh là có hướng và nối giữa hai đỉnh.
- Đồ thị dạng vô hướng luôn là một cây.

## Subtasks

1. (25 điểm): $n, q \leq 1000$
2. (25 điểm): $t = 1$
3. (25 điểm): $\lvert u - v \rvert = 1$
4. (25 điểm): Không có ràng buộc gì thêm.

## Sample Input

    5
    4 2
    1 2
    2 3
    5 1
    3
    3 1
    4 3
    5 2

## Sample Output

    011

# H. Dãy lượn sóng

## Đề bài

Bạn được cho một dãy a độ dài $n$ đánh số từ $1$ tới $n$, là một hoán vị của các số nguyên từ $1$ tới $n$. Dãy con của một dãy là dãy nhận được khi xoá đi $0$ hoặc nhiều phần tử bất kỳ khỏi dãy đó.

Một dãy $b_1, b_2, \ldots, b_m$ được gọi là **lượn sóng** khi nó thoả mãn điều kiện sau:

- Với mọi $i$ sao cho $1 \leq i \leq m - 1$, nếu $s_{i+1} > s_i$ thì $s_{i+2} < s_{i+1}$; nếu $s_{i+1} < s_i$ thì $s_{i+2} > s_{i+1}$.

Với điều kiện nêu như trên, rõ ràng tất cả những dãy độ dài không quá $2$ cũng là dãy lượn sóng.

Ta gọi $f(x, l, r)$ là độ dài dãy con lượn sóng dài nhất của đoạn $a[l \ldots r]$ sao cho tất cả các phần tử có giá trị không lớn hơn $x$.

Đặt $h(x) = \sum_{l=1}^n \sum_{r=l}^n f(x, l, r)$. Nhiệm vụ của bạn là tính các giá trị $h(1), h(2), \ldots, h(n)$.

## Dữ liệu vào

- Dòng đầu tiên chứa số nguyên $n$ $(2 \leq n \leq 2 \cdot 10^5)$.
- Dòng thứ hai chứa $n$ số nguyên $a_i$ là hoán vị của $1$ đến $n$.

## Dữ liệu ra

- Ghi trên $n$ dòng, dòng thứ $i$ ghi một số nguyên là giá trị của $h(i)$.

## Giới hạn

- $2 \leq n \leq 2 \cdot 10^5$
- Dãy $a$ là một hoán vị của $1, 2, \ldots, n$.

## Subtasks

1. (15 điểm): $n \leq 15$
2. (20 điểm): $n \leq 100$
3. (15 điểm): $n \leq 500$
4. (25 điểm): $n \leq 5000$
5. (25 điểm): Không có ràng buộc gì thêm.

## Sample Input

    4
    1 3 4 2

## Sample Output

    4
    8
    14
    18

## Giải thích

- Với $x = 1$: Chỉ các phần tử không lớn hơn $1$ được xét, các đoạn $[l,r]$ với $l=1$ đều có độ dài dãy con lượn sóng là $1$, nên kết quả là $4$.

# I. Gộp phần tử

## Đề bài

Cho dãy số nguyên dương $a_1, a_2, \ldots, a_n$. Bạn có thể thực hiện nhiều lần thao tác chọn hai phần tử $a_i$ và $a_{i+1}$ có cùng giá trị $x$ bằng nhau, sau đó xóa $a_{i+1}$ khỏi dãy và tăng $a_i$ lên $1$ thành $x + 1$. Các phần tử còn lại của dãy sau đó được dồn lại. Hãy thực hiện các thao tác trên để số phần tử của dãy còn lại là ít nhất có thể.

## Dữ liệu vào

- Dòng đầu chứa một số nguyên $n$ $(1 \leq n \leq 10^6)$.
- Dòng thứ hai chứa $n$ số nguyên $a_i$ $(1 \leq a_i \leq 10^9)$.

## Dữ liệu ra

- Ghi ra số phần tử ít nhất có thể của dãy sau khi thực hiện các thao tác thay đổi dãy.

## Giới hạn

- $1 \leq n \leq 10^6$
- $1 \leq a_i \leq 10^9$

## Subtasks

1. (10 điểm): $n \leq 10; a_i \leq 30$
2. (15 điểm): $n \leq 200; a_i \leq 30$
3. (15 điểm): $n \leq 2000; a_i \leq 30$
4. (10 điểm): $n \leq 2000$
5. (30 điểm): $a_i \leq 30$
6. (20 điểm): Không có ràng buộc gì thêm.

## Sample Input

    5
    3 3 3 2 2

## Sample Output

    1

## Giải thích

- Dãy ban đầu: $[3, 3, 3, 2, 2]$.
- Bước 1: Chọn hai số $3$ đầu tiên, thực hiện thao tác $3 + 3 \to 4$, dãy trở thành $[4, 3, 2, 2]$.
- Bước 2: Chọn hai số $2$ cuối, thực hiện thao tác $2 + 2 \to 3$, dãy trở thành $[4, 3, 3]$.
- Bước 3: Chọn hai số $3$, thực hiện thao tác $3 + 3 \to 4$, dãy trở thành $[4, 4]$.
- Bước 4: Chọn hai số $4$, thực hiện thao tác $4 + 4 \to 5$, dãy trở thành $[5]$.

Kết quả: Dãy chỉ còn $1$ phần tử.

# J. Phủ đoạn

## Đề bài

Trên trục $Ox$ xét một đoạn $[l, r]$ và tập đoạn thẳng $S$ ban đầu rỗng. Thực hiện $n$ thao tác, mỗi thao tác thuộc một trong hai loại:

1. Thêm một đoạn $[s, t]$ có chỉ số là $idx$ vào tập $S$.
2. Loại bỏ đoạn có chỉ số $idx$ khỏi tập $S$.

Sau mỗi thao tác, hãy cho biết có tồn tại một đoạn nào trong tập $S$ mà phủ hoàn toàn đoạn $[l, r]$ hay không. Nếu không, cho biết có hai đoạn nào trong tập $S$ mà có thể hợp lại thành một đoạn phủ hoàn toàn đoạn $[l, r]$ hay không?

Một đoạn $[s, t]$ được gọi là **phủ hoàn toàn** đoạn $[l, r]$ nếu $s \leq l$ và $t \geq r$.

Hai đoạn $[s_1, t_1]$ và $[s_2, t_2]$ có thể **hợp lại** nếu $max(s_1, s_2) \leq min(t_1, t_2)$ và khi hợp lại thành đoạn $[min(s_1, s_2), max(t_1, t_2)]$ thì đoạn này phủ hoàn toàn $[l, r]$.

## Dữ liệu vào

- Dòng đầu chứa ba số nguyên $l, r, n$ $(1 \leq l < r \leq 10^9; 1 \leq n \leq 2 \cdot 10^5)$.
- $n$ dòng tiếp theo, mỗi dòng mô tả một trong hai thao tác:
    - Nếu là thao tác thêm đoạn, dòng bắt đầu là ký tự `+` sau đó là ba số nguyên $idx, s, t$ $(1 \leq idx \leq 10^6; 0 \leq s < t \leq 10^9)$. Dữ liệu đảm bảo chỉ số của mỗi đoạn là đôi một phân biệt.
    - Nếu là thao tác xóa đoạn, dòng bắt đầu là ký tự `-` sau đó là một số nguyên $idx$ $(1 \leq idx \leq 10^6)$. Dữ liệu đảm bảo đoạn có chỉ số $idx$ đã tồn tại trong tập $S$.

## Dữ liệu ra

- Sau mỗi thao tác, ghi kết quả trên một dòng:
  - In `1` nếu tồn tại một đoạn phủ hoàn toàn đoạn $[l, r]$.
  - In `2` nếu tồn tại hai đoạn hợp lại được với nhau để phủ hoàn toàn đoạn $[l, r]$.
  - Ngược lại, in ra `-1`.

## Giới hạn

- $1 \leq n \leq 2 \cdot 10^5$
- $1 \leq idx \leq 10^6$
- $0 \leq s < t \leq 10^9$

## Subtasks

1. (30 điểm): $n \leq 200$
2. (30 điểm): $n \leq 2000$
3. (40 điểm): Không có ràng buộc gì thêm.

## Sample Input

    2 6 5
    + 2 4 6
    + 1 2 3
    - 2
    + 3 3 7
    + 5 2 6

## Sample Output

    -1
    -1
    -1
    2
    1

# K. Cặp số hài hoà

## Đề bài

Một tập độc lập cực đại trong đồ thị là tập có kích thước lớn nhất chứa các đỉnh trong đồ thị sao cho không có hai đỉnh thuộc tập này có cạnh nối đến nhau.

Bạn được cho một cây đồ thị gồm $n$ đỉnh, đánh số từ $1$ đến $n$. Một cặp đỉnh $(x, y)$ được gọi là hài hoà nếu ta thêm cạnh nối giữa hai đỉnh $x$ và $y$ (cạnh này có thể là một cạnh nằm trên cây hoặc không), sao cho kích thước của tập độc lập cực đại là không đổi.

Nhiệm vụ của bạn là đếm số lượng cặp đỉnh hài hoà.

## Dữ liệu vào

- Dòng đầu tiên chứa số nguyên $n$ $(2 \leq n \leq 2.5 \cdot 10^5)$.
- Trong $n-1$ dòng tiếp theo, mỗi dòng chứa hai số nguyên $u_i, v_i$ mô tả các cạnh của cây.

## Dữ liệu ra

- Ghi trên một dòng một số nguyên duy nhất là số lượng cặp đỉnh hài hoà.

## Giới hạn

- $2 \leq n \leq 2.5 \cdot 10^5$

## Subtasks (có thể có)

1. (15 điểm): $n \leq 18$
2. (25 điểm): $n \leq 400$
3. (30 điểm): $n \leq 2000$
4. (30 điểm): Không có ràng buộc gì thêm.

## Sample Input

    4
    1 2
    1 3
    1 4

## Sample Output

    3

## Giải thích

Có ba cặp đỉnh hài hoà là $(1, 2)$, $(1, 3)$ và $(1, 4)$. Do tập độc lập cực đại là $(2, 3, 4)$. Nếu thêm cạnh nối giữa đỉnh $1$ và một trong ba đỉnh còn lại, ta vẫn có tập độc lập cực đại là $(2, 3, 4)$.

# L. Di chuyển vượt nguy hiểm

## Đề bài

Cho bảng $n \times m$ gồm $n$ hàng đánh số từ $1$ đến $n$ và $m$ cột đánh số từ $1$ đến $m$. Có $k$ ô nguy hiểm trên bảng. Bạn cần điều khiển một con robot di chuyển từ ô $(1, 1)$ đến ô $(n, m)$ tại thời bắt đầu là thời điểm $0$. Mỗi phút robot có thể di chuyển từ một ô sang một trong bốn ô kề cạnh (không được di chuyển ra ngoài bảng). Biết rằng với $k$ ô nguy hiểm đã cho, tại thời điểm $0$ mức độ nguy hiểm của các ô này là $1$, còn các ô còn lại có mức độ nguy hiểm là $0$. Cứ mỗi phút mức độ nguy hiểm của tất cả các ô sẽ được tăng lên, cụ thể với ô $(i, j)$ tại phút thứ $t$ sẽ được tăng mức độ nguy hiểm lên một lượng là số ô nguy hiểm $(u, v)$ trong $k$ ô nguy hiểm đã cho mà $|i - u| + |j - v| \leq t$. 

Hãy tìm đường đi để robot di chuyển sao cho tổng mức độ nguy hiểm của các ô di chuyển qua là nhỏ nhất có thể.

## Dữ liệu vào

- Dòng đầu chứa ba số nguyên $n, m, k$ $(1 \leq n, m \leq 1000; 1 \leq k \leq 50\,000)$.
- $k$ dòng tiếp theo, mỗi dòng chứa hai số nguyên $u, v$ $(1 \leq u \leq n; 1 \leq v \leq m)$ mô tả vị trí các ô nguy hiểm.

## Dữ liệu ra

- Ghi ra một số nguyên là tổng mức độ nguy hiểm nhỏ nhất của các ô di chuyển qua.

## Giới hạn

- $1 \leq n, m \leq 1000$
- $1 \leq k \leq 50\,000$

## Subtasks

1. (20 điểm): $n, m, k \leq 50$
2. (20 điểm): $n, m, k \leq 200$
3. (30 điểm): $n, m \leq 200$
4. (30 điểm): Không có ràng buộc gì thêm.

## Sample Input

    5 4 2
    2 3
    4 1

## Sample Output

    30

## Giải thích

Di chuyển theo kí tự `x`:

    0 0 0 0         x x x x         0 0 2 2
    0 0 1 0         0 0 1 x               4
    0 0 0 0   --->  0 0 0 x   --->        6
    1 0 0 0         1 0 0 x               8
    0 0 0 0         0 0 0 x               8

Tổng mức độ nguy hiểm là $0 + 0 + 2 + 2 + 4 + 6 + 8 + 8 = 30$.

# M. Thực hiện nhiệm vụ trên đồ thị

## Đề bài

Cho đồ thị có hướng $n$ đỉnh $m$ cạnh. Bạn cần thực hiện các nhiệm vụ được đặt lần lượt tại các đỉnh $t_1, t_2, \ldots, t_k$. Nhiệm vụ tại $t_i$ cần được hoàn thành trước $t_{i+1}$. Bắt đầu trò chơi bạn đứng ở $t_1$, sau đó đi đến các đỉnh tương ứng với các nhiệm vụ cần thực hiện thông qua các cạnh của đồ thị. Điểm của bạn sẽ được tính như sau:

- Ban đầu điểm của bạn là $0$.
- Nếu bạn đang đứng ở $t_i$ và có cạnh trực tiếp đến $t_{i+1}$, bạn được cộng thêm $2$ điểm.
- Nếu bạn từ $t_i$ cần đi qua một số cạnh trung gian để đến $t_{i+1}$, bạn được cộng thêm $1$ điểm.
- Nếu không thể di chuyển từ $t_i$ đến $t_{i+1}$ thì bạn kết thúc nhiệm vụ với số điểm đang có.

Hãy cho biết tổng điểm bạn đạt được là bao nhiêu.

## Dữ liệu vào

- Dòng đầu chứa ba số nguyên $n, m, k$ $(2 \leq n, k \leq 250\,000)$.
- Dòng thứ hai chứa $k$ số $t_i$ $(1 \leq t_i \leq n; t_i \neq t_{i+1})$.
- Dòng thứ ba chứa $m$ $(1 \leq m \leq 250\,000)$.
- $m$ dòng tiếp theo, mỗi dòng chứa hai số $u, v$ $(1 \leq u, v \leq n)$ mô tả có cạnh đi từ đỉnh $u$ đến đỉnh $v$.

## Dữ liệu ra

- Ghi ra số điểm đạt được.

## Giới hạn

- $2 \leq n, k \leq 250\,000$
- $1 \leq m \leq 250\,000$

## Subtasks

1. (20 điểm): $n, m, k \leq 200$
2. (50 điểm): $n \leq 50\,000; m \leq 100\,000$
3. (30 điểm): Không có ràng buộc gì thêm.

## Sample Input

    5 6
    1 3 4 2 5
    5
    1 3
    2 3
    3 4
    4 2
    4 5

## Sample Output

    7

## Giải thích

- Các nhiệm vụ cần thực hiện theo thứ tự $1 \to 3 \to 4 \to 2 \to 5$.
    - **Từ $1$ đến $3$**: Có cạnh trực tiếp. Cộng $2$ điểm.
    - **Từ $3$ đến $4$**: Có cạnh trực tiếp. Cộng $2$ điểm.
    - **Từ $4$ đến $2$**: Có cạnh trực tiếp. Cộng $2$ điểm.
    - **Từ $2$ đến $5$**: Không có cạnh trực tiếp, phải qua trung gian. Cộng $1$ điểm.
- Tổng điểm đạt được là $7$.

# N. Truy vấn đầy đủ số ngắn nhất

## Đề bài

Cho một dãy số nguyên $a$ độ dài $n$. Bạn cần trả lời $q$ truy vấn, truy vấn thứ $i$ đưa ra một số nguyên $x_i$, bạn cần chọn ra một đoạn các số liên tiếp trên dãy $a$ là $a_l, a_{l+1}, \ldots, a_r$ $(1 \leq l \leq r \leq n)$ sao cho với mỗi số nguyên $v$ thỏa mãn $0 \leq v \leq x_i$ xuất hiện ít nhất một lần trong đoạn đó, và độ dài của đoạn được chọn là nhỏ nhất có thể.

## Dữ liệu vào

- Dòng đầu tiên chứa hai số nguyên $n, q$ $(1 \leq n, q \leq 2 \cdot 10^5)$, tương ứng là độ dài dãy $a$ và số truy vấn bạn cần trả lời.
- Dòng tiếp theo chứa $n$ số nguyên, số nguyên thứ $i$ là giá trị của $a_i$ $(0 \leq a_i \leq 10^9)$.
- $q$ dòng tiếp theo, dòng thứ $i$ chứa một số nguyên $x_i$ $(0 \leq x_i \leq 10^9)$ tương ứng là thông tin của truy vấn thứ $i$.

## Dữ liệu ra

- Ghi ra trên $q$ dòng, dòng thứ $i$ là độ dài đoạn con liên tiếp ngắn nhất thỏa mãn truy vấn thứ $i$. Nếu không thể chọn ra đoạn thỏa mãn, ghi ra $-1$.

## Giới hạn

- $1 \leq n, q \leq 2 \cdot 10^5$
- $0 \leq a_i, x_i \leq 10^9$

## Subtasks

1. (10 điểm): $n, q, a_i, x_i \leq 200$
2. (10 điểm): $n \leq 200$
3. (10 điểm): $q = 1, x_i = 1$
4. (15 điểm): Các số $a_i$ đôi một phân biệt.
5. (15 điểm): $n \leq 2000$
6. (20 điểm): $q = 1$
7. (20 điểm): Không có ràng buộc gì thêm.

## Sample Input

    5 3
    0 0 1 3 2
    4
    3
    2

## Sample Output

    -1
    4
    4

## Giải thích

### Truy vấn 1: $x_1 = 4$
- Để thỏa mãn truy vấn, đoạn con phải chứa tất cả các số $v \in \{0, 1, 2, 3, 4\}$.
- Tuy nhiên, trong dãy không có phần tử $4$, do đó không thể chọn đoạn nào thỏa mãn.
- Kết quả: $-1$.

### Truy vấn 2: $x_2 = 3$
- Để thỏa mãn truy vấn, đoạn con phải chứa tất cả các số $v \in \{0, 1, 2, 3\}$.
- Đoạn nhỏ nhất thỏa mãn là $[0, 1, 3, 2]$ (từ vị trí $2$ đến $5$), độ dài là $4$.
- Kết quả: $4$.

### Truy vấn 3: $x_3 = 2$
- Để thỏa mãn truy vấn, đoạn con phải chứa tất cả các số $v \in \{0, 1, 2\}$.
- Đoạn nhỏ nhất thỏa mãn là $[0, 1, 3, 2]$ (từ vị trí $2$ đến $5$), độ dài là $4$.
- Kết quả: $4$.

# O. Truy vấn tập đoạn thẳng

## Đề bài

Xét một tập $S$ các đoạn thẳng $[l, r]$. Hãy chọn ít điểm nhất mà mỗi đoạn thẳng phủ ít nhất một điểm (điểm $p$ được gọi là **phủ** $[l, r]$ nếu $l \leq p \leq r$).

Ban đầu tập $S$ rỗng, có $q$ truy vấn thuộc một trong hai loại:

- `l r`: Thêm đoạn $[l, r]$ vào tập $S$
- `-i`: Xóa đoạn có chỉ số $i$ khỏi tập $S$:  

## Dữ liệu vào

- Dòng đầu chứa số $q$ $(1 \leq q \leq 3 \cdot 10^5)$.
- $q$ dòng tiếp theo, mỗi dòng chứa một trong 2 loại truy vấn trên.

## Dữ liệu ra

- Với mỗi truy vấn, ghi ra số điểm ít nhất cần chọn để phủ tất cả các đoạn trong tập $S$.

## Giới hạn

- $1 \leq q \leq 3 \cdot 10^5$
- $0 \leq l \leq r \leq 10^9$

## Sample Input

    11
    2 2
    2 4
    -2
    3 7
    0 0
    5 9
    2 5
    7 8
    -5
    -4
    6 10

## Sample Output

    1
    1
    1
    2
    3
    3
    3
    3
    3
    2
    2

## Giải thích

1. **Truy vấn 1**: Thêm đoạn $[2, 2]$. Chỉ cần chọn điểm $2$. Kết quả: `1`.
2. **Truy vấn 2**: Thêm đoạn $[2, 4]$. Chỉ cần chọn điểm $2$. Kết quả: `1`.
3. **Truy vấn 3**: Xóa đoạn $[2, 4]$. Tập còn lại là $[2, 2]$. Kết quả: `1`.
4. **Truy vấn 4**: Thêm đoạn $[3, 7]$. Chọn điểm $\{2, 3\}$. Kết quả: `2`.
5. **Truy vấn 5**: Thêm đoạn $[0, 0]$. Chọn điểm $\{0,2,3\}$. Kết quả: `3`.
6. **Truy vấn 6**: Thêm đoạn $[5, 9]$. Chọn điểm $\{0,2,5\}$. Kết quả: `3`.
7. **Truy vấn 7**: Thêm đoạn $[2, 5]$. Chọn điểm $\{0,2,5\}$. Kết quả: `3`.
8. **Truy vấn 8**: Thêm đoạn $[7, 8]$. Chọn điểm $\{0,2,7\}$. Kết quả: `3`.
9. **Truy vấn 9**: Xóa đoạn $[5, 9]$. Chọn điểm $\{0,2,7\}$. Kết quả: `3`.
10. **Truy vấn 10**: Xóa đoạn $[0, 0]$. Chọn điểm $\{2,7\}$. Kết quả: `2`.
11. **Truy vấn 11**: Thêm đoạn $[6, 10]$. Chọn điểm $\{2,7\}$. Kết quả: `2`.

# P. Đường đi chi phí nhỏ nhất

## Đề bài

Cho đồ thị $n$ đỉnh, các đỉnh đánh số từ $1$ đến $n$. Có $m$ cặp đỉnh không thể di chuyển trực tiếp đến nhau. Mỗi đỉnh $u$ có một trọng số $w_u$. Chi phí di chuyển từ đỉnh $u$ đến đỉnh $v$ là $\lvert w_u - w_v \rvert$.  

Cho phép thay đổi trọng số của không quá $k$ đỉnh $u$ mà $1 < u < n$. Hãy tìm đường đi có chi phí nhỏ nhất từ $1$ đến $n$ khi đã thay đổi trọng số của không quá $k$ đỉnh.

## Dữ liệu vào

- Dòng đầu chứa $n, m, k$ $(2 \leq n \leq 500; 0 \leq m \leq \frac{n(n-1)}{2}; 0 \leq k \leq n-2)$.
- Dòng thứ hai chứa $n$ số $w_u$ $(0 \leq w_u \leq 10^9)$.
- $m$ dòng tiếp theo, mỗi dòng chứa hai số $u, v$ $(1 \leq u \neq v \leq n)$ mô tả các cặp đỉnh không di chuyển trực tiếp được đến nhau.

## Dữ liệu ra

- Ghi ra một số là chi phí nhỏ nhất tìm được. Nếu không thể di chuyển từ $1$ đến $n$ thì in ra $-1$.

## Scoring

1. (20%): $k = 0$
2. (30%): $k = 1$
3. (50%): Không có ràng buộc gì thêm.

## Sample Input 1

    4 3 0
    1 7 4 2
    1 3
    1 4
    2 4

## Sample Output 1

    11

## Sample Input 2

    4 3 1
    1 7 4 2
    1 3
    1 4
    2 4

## Sample Output 2

    5

## Sample Input 3

    4 3 3
    1 7 4 2
    1 3
    1 4
    2 4

## Sample Output 3

    1

## Giải thích

### Ví dụ 1:

- **Không được thay đổi trọng số ($k = 0$)**:
    - Các trọng số ban đầu là $[1, 7, 4, 2]$.
    - Đường đi duy nhất từ $1$ đến $4$ là $1 \to 2 \to 3 \to 4$:
        - Chi phí: $\lvert 1 - 7 \rvert + \lvert 7 - 4 \rvert + \lvert 4 - 2 \rvert = 6 + 3 + 2 = 11$.

### Ví dụ 2:

- **Cho phép thay đổi tối đa $k = 1$ trọng số**:
    - Thay đổi trọng số của đỉnh $2$ từ $7$ thành $1$, các trọng số là $[1, 1, 4, 2]$.
    - Đường đi $1 \to 2 \to 3 \to 4$:
        - Chi phí: $\lvert 1 - 1 \rvert + \lvert 1 - 4 \rvert + \lvert 4 - 2 \rvert = 0 + 3 + 2 = 5$.
    - Đây là chi phí nhỏ nhất có thể tìm được.
    - Kết quả: $5$.