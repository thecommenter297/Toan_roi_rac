# Chương 2: Kỹ thuật đếm

[TOC]

## §1. Đệ quy và Hệ thức truy hồi

### 1. Định nghĩa bằng đệ quy (Recursive Definition)
Đệ quy là một kỹ thuật định nghĩa một đối tượng, một hàm, hoặc một quy trình thông qua chính nó.

> **Định nghĩa (Hàm đệ quy)**: Để định nghĩa một hàm `f(n)` xác định trên tập số nguyên không âm, ta cần cung cấp:
> 1.  **Trường hợp cơ sở (Base Case)**: Giá trị của hàm tại một hoặc một vài điểm ban đầu, thường là `f(0)`.
> 2.  **Bước đệ quy (Recursive Step)**: Một công thức để tính giá trị `f(n)` dựa trên các giá trị của hàm tại các số nguyên nhỏ hơn `n` (ví dụ: `f(n-1)`, `f(n-2)`...).

**Ví dụ 1:**
Giả sử hàm `f` được định nghĩa đệ quy như sau:
- $f(0) = 3$
- $f(n+1) = 2f(n) + 3$, với $n \in \mathbb{N}$

Ta có thể tính các giá trị của hàm như sau:
- $f(1) = 2f(0) + 3 = 2(3) + 3 = 9$
- $f(2) = 2f(1) + 3 = 2(9) + 3 = 21$
- $f(3) = 2f(2) + 3 = 2(21) + 3 = 45$
- $f(4) = 2f(3) + 3 = 2(45) + 3 = 93$

**Ví dụ 2: Định nghĩa đệ quy của hàm giai thừa**
Xét hàm $f(n) = n!$.
- **Trường hợp cơ sở**: $f(0) = 0! = 1$.
- **Bước đệ quy**: Ta có $(n+1)! = (n+1) \times n!$. Do đó, $f(n+1) = (n+1)f(n)$.

### 2. Giải hệ thức truy hồi (Solving Recurrence Relations)

> **Định nghĩa 1**: Một **hệ thức truy hồi** đối với dãy số $a_{n}$ là một công thức biểu diễn số hạng $a_{n}$ qua một hoặc nhiều số hạng đứng trước nó ($a_{n-1}$, $a_{n-2}$, ...), đúng với mọi $n ≥ n_{0}$, trong đó $n_{0}$ là một số nguyên không âm.
>
> **Nghiệm** của hệ thức truy hồi là một công thức tường minh cho $a_{n}$ (không phụ thuộc vào các số hạng khác của dãy) thỏa mãn hệ thức đó.

#### Hệ thức truy hồi tuyến tính thuần nhất với hệ số hằng
> **Định nghĩa 2**: Một hệ thức truy hồi tuyến tính thuần nhất bậc `k` với hệ số hằng có dạng:
> $$ a_n = c_1a_{n-1} + c_2a_{n-2} + \cdots + c_ka_{n-k} $$
> trong đó $c_1, c_2, ..., c_k$ là các hằng số thực và $c_k \neq 0$.

**Ví dụ:**
- $a_n = a_{n-1} + a_{n-2}$ (Dãy Fibonacci) là hệ thức truy hồi tuyến tính thuần nhất bậc 2.
- $a_n = 2a_{n-4}$ là hệ thức truy hồi tuyến tính thuần nhất bậc 4.
- $a_n = na_{n-1}$ không phải là hệ thức truy hồi tuyến tính thuần nhất vì hệ số `n` không phải là hằng số.

#### Phương pháp giải
**Bước 1: Tìm phương trình đặc trưng**
Ta tìm nghiệm của hệ thức truy hồi dưới dạng $a_n = \lambda^n$, với $\lambda$ là hằng số. Thay vào hệ thức truy hồi, ta có:
$\lambda^n = c_1\lambda^{n-1} + c_2\lambda^{n-2} + \cdots + c_k\lambda^{n-k}$
Chia cả hai vế cho $\lambda^{n-k}$ (với $\lambda \neq 0$), ta được **phương trình đặc trưng**:
$$ \lambda^k - c_1\lambda^{k-1} - c_2\lambda^{k-2} - \cdots - c_k = 0 $$

**Bước 2: Tìm nghiệm của phương trình đặc trưng và xây dựng nghiệm tổng quát**
Giả sử phương trình đặc trưng có các nghiệm $\lambda_1, \lambda_2, ..., \lambda_k$.
- **Trường hợp các nghiệm phân biệt**: Nếu phương trình có `k` nghiệm thực phân biệt $\lambda_1, \lambda_2, ..., \lambda_k$, thì nghiệm tổng quát của hệ thức truy hồi là:
  $$ a_n = \alpha_1\lambda_1^n + \alpha_2\lambda_2^n + \cdots + \alpha_k\lambda_k^n $$
- **Trường hợp có nghiệm bội**: Nếu $\lambda_1$ là một nghiệm bội bậc `m`, các nghiệm còn lại là phân biệt, thì nghiệm tổng quát có dạng:
  $$ a_n = (\alpha_1 + \alpha_2n + \cdots + \alpha_mn^{m-1})\lambda_1^n + \alpha_{m+1}\lambda_{m+1}^n + \cdots $$

**Bước 3: Tìm các hằng số $\alpha_i$**
Sử dụng các điều kiện ban đầu (giá trị của $a_0, a_1, ...$) để lập một hệ phương trình tuyến tính và giải tìm các hằng số $\alpha_1, \alpha_2, ...$.

**Ví dụ (Trường hợp 2 nghiệm phân biệt):**
Giải hệ thức $a_n = a_{n-1} + 2a_{n-2}$ với $a_0 = 2, a_1 = 7$.
1.  **Phương trình đặc trưng**: $\lambda^2 - \lambda - 2 = 0$.
2.  **Nghiệm đặc trưng**: Phương trình có 2 nghiệm phân biệt $\lambda_1 = 2$ và $\lambda_2 = -1$.
3.  **Nghiệm tổng quát**: $a_n = \alpha_1(2)^n + \alpha_2(-1)^n$.
4.  **Tìm hằng số**:
    - Với $n=0: a_0 = \alpha_1 + \alpha_2 = 2$.
    - Với $n=1: a_1 = 2\alpha_1 - \alpha_2 = 7$.
    Giải hệ, ta được $\alpha_1 = 3, \alpha_2 = -1$.
5.  **Nghiệm cuối cùng**: $a_n = 3 \cdot 2^n - (-1)^n$.

**Ví dụ (Trường hợp nghiệm kép):**
Giải hệ thức $a_n = 6a_{n-1} - 9a_{n-2}$ với $a_0 = 1, a_1 = 6$.
1.  **Phương trình đặc trưng**: $\lambda^2 - 6\lambda + 9 = 0$.
2.  **Nghiệm đặc trưng**: Phương trình có nghiệm kép $\lambda = 3$.
3.  **Nghiệm tổng quát**: $a_n = (\alpha_1 + \alpha_2n)3^n$.
4.  **Tìm hằng số**:
    - Với $n=0: a_0 = \alpha_1 = 1$.
    - Với $n=1: a_1 = (\alpha_1 + \alpha_2) \cdot 3 = 6 \implies \alpha_1 + \alpha_2 = 2 \implies \alpha_2 = 1$.
5.  **Nghiệm cuối cùng**: $a_n = (1 + n)3^n$.

## §2. Các quy tắc đếm cơ bản

### 1. Quy tắc cộng
> **Phát biểu**: Nếu một công việc có thể được thực hiện theo một trong `k` phương án $T_1, T_2, ..., T_k$ (loại trừ lẫn nhau), trong đó phương án $T_i$ có $n_i$ cách thực hiện, thì tổng số cách để hoàn thành công việc là:
> $$ n_1 + n_2 + \cdots + n_k $$

### 2. Quy tắc nhân
> **Phát biểu**: Nếu một công việc được chia thành `k` giai đoạn nối tiếp $T_1, T_2, ..., T_k$, trong đó giai đoạn $T_i$ có $n_i$ cách thực hiện (sau khi các giai đoạn trước đã hoàn thành), thì tổng số cách để hoàn thành toàn bộ công việc là:
> $$ n_1 \times n_2 \times \cdots \times n_k $$

### 3. Chỉnh hợp và Tổ hợp (Suy rộng)

#### 3.1. Chỉnh hợp lặp
> Một **chỉnh hợp lặp** chập `k` của một tập `n` phần tử là một cách sắp xếp có thứ tự `k` phần tử, trong đó các phần tử có thể được lặp lại.
>
> Số chỉnh hợp lặp chập `k` từ `n` phần tử là: **$n^k$**

#### 3.2. Tổ hợp lặp
> Một **tổ hợp lặp** chập `k` của một tập `n` phần tử là một cách chọn không có thứ tự `k` phần tử, trong đó các phần tử có thể được lặp lại.
>
> Số tổ hợp lặp chập `k` từ `n` phần tử là: **$C_{n+k-1}^k = \frac{(n+k-1)!}{k!(n-1)!}$**

**Ví dụ (Tổ hợp lặp):**
Có bao nhiêu cách chọn 5 tờ tiền từ một két có 7 loại tiền khác nhau (mỗi loại có ít nhất 5 tờ)?
- Đây là bài toán chọn `k=5` phần tử từ `n=7` loại, có lặp lại và không phân biệt thứ tự.
- Số cách chọn là: $C_{7+5-1}^5 = C_{11}^5 = \frac{11!}{5!6!} = 462$ cách.

### 4. Hoán vị lặp
> Số hoán vị của `n` phần tử, trong đó có $n_1$ phần tử loại 1 giống nhau, $n_2$ phần tử loại 2 giống nhau, ..., $n_k$ phần tử loại `k` giống nhau ($n_1 + n_2 + ... + n_k = n$) là:
> $$ \frac{n!}{n_1! n_2! \cdots n_k!} $$

**Ví dụ:**
Có bao nhiêu xâu khác nhau có thể tạo thành bằng cách sắp xếp lại các chữ cái của từ "SUCCESS"?
- Từ "SUCCESS" có `n=7` chữ cái.
- Gồm: `S` (3 lần), `U` (1 lần), `C` (2 lần), `E` (1 lần).
- Số xâu khác nhau là: $\frac{7!}{3! \cdot 1! \cdot 2! \cdot 1!} = \frac{5040}{6 \cdot 2} = 420$ xâu.

## §3. Nguyên lý Dirichlet (Nguyên lý chuồng bồ câu)

### 1. Nguyên lý Dirichlet cơ bản
> **Phát biểu**: Nếu đặt `k+1` (hoặc nhiều hơn) đồ vật vào `k` cái hộp, thì tồn tại ít nhất một hộp chứa ít nhất hai đồ vật.

### 2. Nguyên lý Dirichlet tổng quát
> **Phát biểu**: Nếu đặt `N` đồ vật vào `k` cái hộp, thì sẽ tồn tại ít nhất một hộp chứa ít nhất $\lceil \frac{N}{k} \rceil$ đồ vật.
> 
> (Trong đó, $\lceil x \rceil$ là hàm trần, là số nguyên nhỏ nhất lớn hơn hoặc bằng `x`).
>
> **Lưu ý**: Trong một số tài liệu (như slide bổ sung), nguyên lý này được phát biểu là tồn tại một hộp chứa ít nhất $\lfloor \frac{N-1}{k} \rfloor + 1$ hoặc $[N/k]+1$ (nếu $[x]$ là phần nguyên). Các cách phát biểu này là tương đương với $\lceil N/k \rceil$.

**Chứng minh (bằng phản chứng):**
Giả sử không có hộp nào chứa nhiều hơn $\lceil \frac{N}{k} \rceil - 1$ đồ vật. Khi đó, tổng số đồ vật trong `k` hộp sẽ không vượt quá:
$$ k \times \left( \lceil \frac{N}{k} \rceil - 1 \right) $$
Ta biết rằng $\frac{N}{k} \le \lceil \frac{N}{k} \rceil < \frac{N}{k} + 1$.
Suy ra $\lceil \frac{N}{k} \rceil - 1 < \frac{N}{k}$.
Do đó, tổng số vật nhỏ hơn $k \times \frac{N}{k} = N$. Điều này mâu thuẫn với giả thiết ban đầu là có `N` đồ vật. Vậy giả sử là sai.

**Ví dụ:**
Trong 100 người (`N=100`), có ít nhất bao nhiêu người sinh cùng một tháng?
- Coi 100 người là 100 đồ vật.
- Coi 12 tháng là 12 cái hộp (`k=12`).
- Theo nguyên lý Dirichlet tổng quát, sẽ có ít nhất một tháng chứa $\lceil \frac{100}{12} \rceil = \lceil 8.33 \rceil = 9$ người.
