# Chương 1: Mệnh đề Logic và Đại số Boole

[TOC]

## Phần 1: Mệnh Đề Logic

### 1. Giới thiệu và khái niệm cơ bản

#### 1.1. Mở đầu: Bài toán mạch điện
Xét một mạch điện đơn giản có các công tắc (cầu dao) A, B, C và dòng điện đi từ điểm M đến N.

![image](https://hackmd.io/_uploads/Hkq0iLpK-l.png)


Trạng thái của dòng điện tại MN (có hoặc không) phụ thuộc hoàn toàn vào trạng thái đóng/mở của các công tắc A, B, C. Ta quy ước:
- **`1`**: Công tắc đóng hoặc có dòng điện.
- **`0`**: Công tắc mở hoặc không có dòng điện.

Ta có thể lập bảng mô tả tất cả các trường hợp có thể xảy ra, gọi là bảng giá trị (hay bảng chân trị):

| A | B | C | MN |
| :-: | :-: | :-: | :--: |
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

**Câu hỏi đặt ra**: Khi một hệ thống có nhiều thành phần (nhiều công tắc hơn), làm thế nào để kiểm soát và biểu diễn nó một cách hệ thống?
**Giải pháp**: Xây dựng các công thức logic, trong đó mỗi biến đại diện cho một thành phần (công tắc), và các phép toán logic đại diện cho cách chúng được kết nối.

#### 1.2. Mệnh đề logic (Proposition)
> **Định nghĩa**: Một **mệnh đề** là một phát biểu (khẳng định) có giá trị chân lý xác định, hoặc là **Đúng (True)** hoặc là **Sai (False)**, nhưng không thể đồng thời vừa đúng vừa sai.
>
> Giá trị chân lý của mệnh đề được ký hiệu là `1` (Đúng) hoặc `0` (Sai).

**Ví dụ về các mệnh đề:**
- "6 là một số nguyên tố." (Mệnh đề này có giá trị chân lý là Sai).
- "5 là một số nguyên tố." (Mệnh đề này có giá trị chân lý là Đúng).
- "-3 < 2" (Mệnh đề này có giá trị chân lý là Đúng).

**Ví dụ về các phát biểu *không phải* là mệnh đề:**
- "Ai đang đọc sách?" (Đây là câu hỏi, không có giá trị đúng/sai).
- "Hãy đóng cửa lại đi!" (Đây là câu mệnh lệnh).
- "Cho x là một số nguyên dương." (Đây là mệnh đề chứa biến, giá trị đúng/sai phụ thuộc vào giá trị của `x`).

#### 1.3. Mệnh đề chứa biến (Predicate)
> **Định nghĩa**: Một **mệnh đề chứa biến** là một phát biểu chứa một hoặc nhiều biến, và nó sẽ trở thành một mệnh đề logic khi các biến được gán giá trị cụ thể hoặc được ràng buộc bởi các lượng từ.

**Ví dụ:**
- `P(n) = "n chia hết cho 2"`
- `Q(x) = "x > 2"`

`P(n)` và `Q(x)` không phải là mệnh đề vì giá trị chân lý của chúng chưa xác định. Tuy nhiên, `P(4)` ("4 chia hết cho 2") là một mệnh đề Đúng, và `Q(1)` ("1 > 2") là một mệnh đề Sai.

#### 1.4. Lượng từ (Quantifiers)
Để biến một mệnh đề chứa biến thành mệnh đề logic, ta có thể sử dụng các lượng từ.
- **Lượng từ phổ dụng (với mọi)**, ký hiệu: $\forall$
- **Lượng từ tồn tại**, ký hiệu: $\exists$

Khi một mệnh đề chứa biến được đi kèm với lượng từ, nó trở thành một mệnh đề logic hoàn chỉnh.

**Ví dụ:**
- `A = "∃n ∈ N | n > 3"` ("Tồn tại số tự nhiên n sao cho n lớn hơn 3"). Đây là một mệnh đề Đúng.
- `B = "∀a ∈ R | a² < 0"` ("Với mọi số thực a, a bình phương nhỏ hơn 0"). Đây là một mệnh đề Sai.

### 2. Các phép toán trên mệnh đề

Ta có thể kết hợp các mệnh đề đơn giản (sơ cấp) để tạo thành các mệnh đề phức hợp bằng cách sử dụng các phép toán logic.

#### 2.1. Phép Phủ định (Negation)
> Phủ định của mệnh đề $X$, ký hiệu là $\neg X$ hoặc $\overline{X}$, là mệnh đề nhận giá trị đúng khi $X$ sai, và nhận giá trị sai khi $X$ đúng.

**Bảng chân trị:**
| X | ¬X |
| :-: | :--: |
| 0 | 1 |
| 1 | 0 |

**Ví dụ:**
- Nếu `A = "3 > 5"` (Sai), thì `¬A = "3 ≤ 5"` (Đúng).
- Phủ định của `∀` là `∃`. Ví dụ: `¬(∀x, P(x))` tương đương với `∃x, ¬P(x)`.
- Phủ định của `∃` là `∀`. Ví dụ: `¬(∃x, P(x))` tương đương với `∀x, ¬P(x)`.
- Phép phủ định hai lần: $\overline{\overline{A}} \equiv A$.

#### 2.2. Phép Hội (Conjunction)
> Phép hội của hai mệnh đề `X` và `Y`, ký hiệu là `X ∧ Y` (đọc là "X và Y"), là mệnh đề chỉ đúng khi cả `X` và `Y` đều đúng.

**Bảng chân trị:**
| X | Y | X ∧ Y |
| :-: | :-: | :-----: |
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 0 |

#### 2.3. Phép Tuyển (Disjunction)
> Phép tuyển của hai mệnh đề `X` và `Y`, ký hiệu là `X ∨ Y` (đọc là "X hoặc Y"), là mệnh đề chỉ sai khi cả `X` và `Y` đều sai.

**Bảng chân trị:**
| X | Y | X ∨ Y |
| :-: | :-: | :-----: |
| 1 | 1 | 1 |
| 1 | 0 | 1 |
| 0 | 1 | 1 |
| 0 | 0 | 0 |

#### 2.4. Phép Kéo theo (Implication)
> Phép kéo theo `X → Y` (đọc là "Nếu X thì Y" hoặc "X suy ra Y"), là mệnh đề chỉ sai trong trường hợp `X` đúng nhưng `Y` sai.
> - `X`: Giả thiết, tiền đề.
> - `Y`: Kết luận, hệ quả.

**Bảng chân trị:**
| X | Y | X → Y |
| :-: | :-: | :-----: |
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 1 |
| 0 | 0 | 1 |

#### 2.5. Phép Tương đương (Biconditional)
> Phép tương đương `X ↔ Y` (đọc là "X khi và chỉ khi Y"), là mệnh đề đúng khi `X` và `Y` có cùng giá trị chân lý.

**Bảng chân trị:**
| X | Y | X ↔ Y |
| :-: | :-: | :-----: |
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 1 |

### 3. Công thức và các đẳng thức logic

#### 3.1. Công thức logic (Well-Formed Formula - WFF)
1. Mọi mệnh đề sơ cấp (X, Y, Z,...) là một công thức.
2. Nếu A, B là hai công thức, thì `(¬A)`, `(A ∧ B)`, `(A ∨ B)`, `(A → B)`, `(A ↔ B)` cũng là các công thức.

#### 3.2. Công thức đồng nhất
- **Đồng nhất đúng (Tautology)**: Một công thức `A` được gọi là đồng nhất đúng nếu nó luôn nhận giá trị `1` với mọi giá trị của các biến mệnh đề. Ký hiệu: `A ≡ 1`.
- **Đồng nhất sai (Contradiction)**: Một công thức `A` được gọi là đồng nhất sai nếu nó luôn nhận giá trị `0` với mọi giá trị của các biến mệnh đề. Ký hiệu: `A ≡ 0`.
- **Đồng nhất bằng nhau (Logical Equivalence)**: Hai công thức `A` và `B` được gọi là đồng nhất bằng nhau (tương đương logic) nếu chúng luôn có cùng giá trị chân lý với mọi giá trị của các biến. Ký hiệu: `A ≡ B`.

#### 3.3. Các công thức đồng nhất bằng nhau cơ bản (Luật logic)

Dưới đây là các luật logic quan trọng:
1.  **Luật phủ định kép**: $\overline{\overline{A}} \equiv A$
2.  **Luật giao hoán**:
$A \lor B \equiv B \lor A$;
$A \land B \equiv B \land A$
4.  **Luật kết hợp**:
$(A \lor B) \lor C \equiv A \lor (B \lor C)$;
$(A \land B) \land C \equiv A \land (B \land C)$
5.  **Luật phân phối**:
$A \land (B \lor C) \equiv (A \land B) \lor (A \land C)$;
$A \lor (B \land C) \equiv (A \lor B) \land (A \lor C)$
6.  **Luật De Morgan**:
$\overline{A \lor B} \equiv \overline{A} \land \overline{B}$;
$\overline{A \land B} \equiv \overline{A} \lor \overline{B}$
8.  **Luật Lũy đẳng**:
$A \lor A \equiv A$;
$A \land A \equiv A$
10.  **Luật trung hòa**: $A \lor 0 \equiv A$; $A \land 1 \equiv A$
11.  **Luật thống trị/nuốt**: $A \lor 1 \equiv 1$; $A \land 0 \equiv 0$
12.  **Luật phần bù**: $A \lor \overline{A} \equiv 1$; $A \land \overline{A} \equiv 0$
13. **Luật hấp thụ**: $A \lor (A \land B) \equiv A$; $A \land (A \lor B) \equiv A$
14. **Tương đương của phép kéo theo**: $A \to B \equiv \overline{A} \lor B$
15. **Tương đương của phép tương đương**: $A \leftrightarrow B \equiv (A \to B) \land (B \to A)$

> **Chú ý**: Thứ tự ưu tiên thực hiện các phép toán logic là: `Phủ định (¬)` → `Hội (∧)` → `Tuyển (∨)` → `Kéo theo (→)` → `Tương đương (↔)`.

### 4. Suy diễn logic

Suy diễn logic là quá trình đi từ một tập các mệnh đề ban đầu (giả thiết) để đến một mệnh đề mới (kết luận).

#### Mô hình suy diễn:
```
  A₁
  A₂
  ...
  Aₙ
-----
∴ B
```
Mô hình này được gọi là một suy diễn **hợp lệ** nếu mệnh đề $(A_1 \land A_2 \land ... \land A_n) \to B$ là một hằng đúng (tautology).

#### Các quy tắc suy diễn cơ bản:
1.  **Luật cộng (Addition)**
    - Công thức: $A \to (A \lor B) \equiv 1$
    - Mô hình: $\frac{A}{\therefore A \lor B}$

2.  **Luật rút gọn (Simplification)**
    - Công thức: $(A \land B) \to A \equiv 1$
    - Mô hình: $\frac{A \land B}{\therefore A}$

3.  **Modus Ponens (Luật khẳng định)**
    - Công thức: $(A \land (A \to B)) \to B \equiv 1$
    - Mô hình: $\frac{A, A \to B}{\therefore B}$

4.  **Modus Tollens (Luật phủ định)**
    - Công thức: $(\overline{B} \land (A \to B)) \to \overline{A} \equiv 1$
    - Mô hình: $\frac{\overline{B}, A \to B}{\therefore \overline{A}}$

5.  **Tam đoạn luận rời (Disjunctive Syllogism)**
    - Công thức: $((A \lor B) \land \overline{A}) \to B \equiv 1$
    - Mô hình: $\frac{A \lor B, \overline{A}}{\therefore B}$

6.  **Tam đoạn luận bắc cầu (Hypothetical Syllogism)**
    - Công thức: $((A \to B) \land (B \to C)) \to (A \to C) \equiv 1$
    - Mô hình: $\frac{A \to B, B \to C}{\therefore A \to C}$

## Phần 2: Đại số Boole

### 1. Định nghĩa Đại số Boole

> **Định nghĩa**: Một **đại số Boole** là một tập hợp `A` khác rỗng, cùng với hai phép toán hai ngôi `∧` (hội, nhân logic) và `∨` (tuyển, cộng logic), ký hiệu là `(A, ∧, ∨)`, thỏa mãn 5 tính chất sau:

#### 1.1. Tính giao hoán (Commutative Property)
Với mọi $x, y \in A$:
- $x \land y = y \land x$
- $x \lor y = y \lor x$

#### 1.2. Tính kết hợp (Associative Property)
Với mọi $x, y, z \in A$:
- $(x \land y) \land z = x \land (y \land z)$
- $(x \lor y) \lor z = x \lor (y \lor z)$

#### 1.3. Tính phân phối (Distributive Property)
Với mọi $x, y, z \in A$:
- $x \land (y \lor z) = (x \land y) \lor (x \land z)$
- $x \lor (y \land z) = (x \lor y) \land (x \lor z)$

#### 1.4. Có phần tử trung hòa (Identity Elements)
Tồn tại các phần tử `0` và `1` trong `A` sao cho với mọi $x \in A$:
- $x \land 1 = 1 \land x = x$
- $x \lor 0 = 0 \lor x = x$

#### 1.5. Có phần tử bù (Complement Element)
Với mỗi phần tử $x \in A$, tồn tại một phần tử bù $\overline{x} \in A$ sao cho:
- $x \land \overline{x} = \overline{x} \land x = 0$
- $x \lor \overline{x} = \overline{x} \lor x = 1$

### 2. Các ví dụ về Đại số Boole

#### Ví dụ 1: Đại số mệnh đề
Tập hợp `F` gồm tất cả các dạng mệnh đề logic, trong đó các mệnh đề tương đương được xem là một. Với phép toán `∧` (hội) và `∨` (tuyển), tập hợp này tạo thành một đại số Boole.
- **Phần tử 1**: Là hằng đúng `1` (Tautology).
- **Phần tử 0**: Là hằng sai `0` (Contradiction).
- **Phần tử bù** của mệnh đề `E` là mệnh đề phủ định $\overline{E}$.

#### Ví dụ 2: Đại số Boole trên tập {0, 1}
Xét tập hợp `B = {0, 1}`. Ta định nghĩa hai phép toán `∧` và `∨` qua các bảng sau:

**Phép toán ∧ (AND)**
| ∧ | 0 | 1 |
| :-: | :-: | :-: |
| **0** | 0 | 0 |
| **1** | 0 | 1 |

**Phép toán ∨ (OR)**
| ∨ | 0 | 1 |
| :-: | :-: | :-: |
| **0** | 0 | 1 |
| **1** | 1 | 1 |

Khi đó, `(B, ∧, ∨)` là một đại số Boole. Đây là đại số Boole cơ bản và được sử dụng phổ biến nhất trong khoa học máy tính và mạch số.

### 3. Hàm Boole (Boolean Function)

#### 3.1. Định nghĩa
> Một **hàm Boole** `n` biến là một ánh xạ `f` từ `Bⁿ` vào `B`, trong đó `B = {0, 1}`.
> $$f: B^n \to B$$
>
> Như vậy, hàm Boole có dạng `f(x₁, x₂, ..., xₙ)`, trong đó mỗi biến `xᵢ` và giá trị của hàm `f` đều chỉ nhận một trong hai giá trị là `0` hoặc `1`.
> 
> Tập hợp tất cả các hàm Boole n biến được ký hiệu là **Fₙ**.

#### 3.2. Bảng chân trị
Một hàm Boole `n` biến có `2ⁿ` bộ giá trị đầu vào khác nhau. Ta có thể mô tả hoàn toàn một hàm Boole bằng cách lập một bảng liệt kê tất cả các giá trị đầu ra tương ứng với từng bộ đầu vào. Bảng này được gọi là **bảng chân trị** của hàm.

#### 3.3. Ví dụ: Hàm biểu quyết đa số
Xét một hệ thống quyết định dựa trên 3 phiếu bầu `x, y, z`. Mỗi phiếu có giá trị `1` (tán thành) hoặc `0` (bác bỏ). Kết quả `f` là `1` (thông qua) nếu đa số phiếu tán thành, và là `0` (không thông qua) nếu đa số phiếu bác bỏ.

Hàm `f(x, y, z)` được mô tả bằng bảng chân trị sau:

| x | y | z | f |
| :-: | :-: | :-: | :-: |
| 1 | 1 | 1 | **1** |
| 1 | 1 | 0 | **1** |
| 1 | 0 | 1 | **1** |
| 1 | 0 | 0 | 0 |
| 0 | 1 | 1 | **1** |
| 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 |

Từ bảng trên, ta có thể biểu diễn hàm `f` dưới dạng công thức bằng cách lấy tổng (phép `∨`) của các tích (phép `∧`) tương ứng với các hàng mà `f=1`:
$f(x, y, z) = (x \land y \land z) \lor (x \land y \land \overline{z}) \lor (x \land \overline{y} \land z) \lor (\overline{x} \land y \land z)$

### 4. Các dạng biểu diễn Hàm Boole

#### 4.1. Thuật ngữ cơ bản
- **Từ đơn (Literal)**: Một biến Boole hoặc phủ định của nó (ví dụ: `x` hoặc $\overline{x}$).
- **Đơn thức (Product Term)**: Tích của một hoặc nhiều từ đơn (ví dụ: $x\overline{y}z$).
- **Từ tối tiểu (Minterm)**: Một đơn thức chứa tất cả `n` biến của hàm (ví dụ: với hàm 3 biến x, y, z, thì $x\overline{y}z$ là một từ tối tiểu).
- **Công thức đa thức**: Tổng của các đơn thức.
- **Dạng nối rời chính tắc (Disjunctive Normal Form - DNF)**: Một công thức biểu diễn hàm Boole dưới dạng tổng của các từ tối tiểu. Đây chính là dạng công thức được suy ra trực tiếp từ bảng chân trị như ví dụ 3.3.

#### 4.2. Công thức đa thức tối tiểu
Mục tiêu của việc tối tiểu hóa một hàm Boole là tìm một công thức đa thức tương đương với hàm Boole ban đầu nhưng chứa ít từ đơn và đơn thức hơn.
> Một công thức `F` được gọi là **tối tiểu** nếu không tồn tại một công thức `G` nào khác tương đương với `F` mà "đơn giản hơn" `F`.

### 5. Ứng dụng: Mạch Logic (Mạng các cổng logic)

Hàm Boole là nền tảng toán học để thiết kế các mạch logic kỹ thuật số. Mỗi phép toán Boole cơ bản tương ứng với một **cổng logic**.

- **Input**: Các biến Boole ($x_1, x_2, ..., x_n$).
- **Output**: Giá trị của hàm Boole `f(x₁, ..., xₙ)`.

#### 5.1. Các cổng logic cơ bản
- **Cổng NOT**:
![image](https://hackmd.io/_uploads/HJ1QWvTYbl.png)

  - Biểu thức: $F(x) = \overline{x}$
  - Mô tả: Đảo ngược tín hiệu đầu vào.
- **Cổng AND**:
![image](https://hackmd.io/_uploads/rkE4GwaFWl.png)


  - Biểu thức: $F(x, y) = x \land y$ (hoặc `xy`)
  - Mô tả: Đầu ra là `1` chỉ khi tất cả đầu vào đều là `1`.
- **Cổng OR**:
![image](https://hackmd.io/_uploads/BJI9bwTKWl.png)

  - Biểu thức: $F(x, y) = x \lor y$ (hoặc `x+y`)
  - Mô tả: Đầu ra là `1` nếu có ít nhất một đầu vào là `1`.

#### 5.2. Các cổng logic kết hợp
- **Cổng NAND**:
![image](https://hackmd.io/_uploads/rJggGw6KWx.png)

  - Biểu thức: $F(x, y) = \overline{xy}$ (là cổng AND kết hợp với NOT)
  - Mô tả: Đầu ra là `0` chỉ khi tất cả đầu vào đều là `1`.
- **Cổng NOR**:
![image](https://hackmd.io/_uploads/SkH8MP6FWl.png)

  - Biểu thức: $F(x, y) = \overline{x+y}$ (là cổng OR kết hợp với NOT)
  - Mô tả: Đầu ra là `1` chỉ khi tất cả đầu vào đều là `0`.

### 6. Cực tiểu hóa Hàm Boole: Biểu đồ Karnaugh (K-map)

Biểu đồ Karnaugh là một phương pháp đồ họa dùng để đơn giản hóa (tối tiểu hóa) các hàm Boole.

- **Nguyên tắc**: Các ô liền kề trong biểu đồ chỉ khác nhau giá trị của một biến duy nhất. Điều này cho phép nhóm các ô chứa giá trị `1` lại với nhau để loại bỏ các biến.
- **Quy tắc nhóm**:
  - Nhóm các ô `1` liền kề theo các hình chữ nhật có số ô là lũy thừa của 2 (1, 2, 4, 8,...).
  - Nhóm càng lớn càng tốt.
  - Mỗi ô `1` phải thuộc ít nhất một nhóm.

**6.1. Biểu đồ Karnaugh 2 biến**
$f(x,y) = \bar{x}y + xy$

| | $\bar{y}$ (0) | **$y$ (1)** |
| :---: | :---: | :---: |
| **$\bar{x}$ (0)** | 0 | **1** |
| **$x$ (1)** | 0 | **1** |

*Nhóm 1 cột bên phải (cột y), ta được $f(x,y) = y$*

**6.2. Biểu đồ Karnaugh 3 biến**
$f(x,y,z) = \bar{x}y\bar{z} + \bar{x}yz + xyz + xy\bar{z}$

| | $\bar{y}\bar{z}$ (00) | $\bar{y}z$ (01) | **$yz$ (11)** | **$y\bar{z}$ (10)** |
| :---: | :---: | :---: | :---: | :---: |
| **$\bar{x}$ (0)** | 0 | 0 | **1** | **1** |
| **$x$ (1)** | 0 | 0 | **1** | **1** |

*Nhóm 4 ô (một hình vuông 2x2 ở nửa bên phải). Trong khối này $x$ thay đổi (từ 0 lên 1), $z$ thay đổi (từ 1 về 0), chỉ có $y$ giữ nguyên giá trị 1. Vậy $f(x,y,z) = y$.*
