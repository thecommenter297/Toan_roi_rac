# Chương 4: Lý thuyết đồ thị (Graph Theory)

[TOC]

## Phần 1: Những khái niệm và tính chất cơ bản

Lý thuyết đồ thị là một công cụ toán học quan trọng dùng để mô hình hóa các hệ thống có cấu trúc mạng lưới, như mạng giao thông, mạng máy tính, cấu trúc phân tử, hay các mối quan hệ xã hội.

### 1. Đồ thị vô hướng (Undirected Graph)

#### 1.1. Định nghĩa cơ bản
![image](https://hackmd.io/_uploads/HkpecTJsZg.png)


> **Định nghĩa 1**: Một **đồ thị vô hướng** $G = (V, E)$ bao gồm hai tập hợp:
> - $V$: Tập hợp hữu hạn khác rỗng. Các phần tử của $V$ được gọi là các **đỉnh** (Vertex).
> - $E$: Tập hợp các cặp không có thứ tự gồm hai phần tử của $V$. Các phần tử của $E$ được gọi là các **cạnh** (Edge).

**Các khái niệm liên quan:**


- Giả sử $e = \{u, v\}$ (ký hiệu đơn giản là $uv$) là một cạnh của đồ thị. Ta nói:
  - Cạnh $uv$ **nối** hai đỉnh $u$ và $v$.
  - Cạnh $uv$ **kề** với đỉnh $u$ và đỉnh $v$.
  - Hai đỉnh $u$ và $v$ **kề nhau** (liền kề).
- **Cạnh song song**: Hai hay nhiều cạnh cùng nối một cặp đỉnh được gọi là các cạnh song song.
- **Khuyên (Loop)**: Một cạnh có hai đầu mút trùng nhau (tức là nối một đỉnh với chính nó) được gọi là một khuyên.
![image](https://hackmd.io/_uploads/BJl756ysbe.png)
#### 1.2. Phân loại đồ thị vô hướng
Dựa vào sự xuất hiện của cạnh song song và khuyên, đồ thị vô hướng được chia thành ba loại:
> **Định nghĩa 2**: **Đơn đồ thị vô hướng** là đồ thị vô hướng không có cạnh song song và không có khuyên.
> ![image](https://hackmd.io/_uploads/ry7MsTJibl.png)

> **Định nghĩa 3**: **Đa đồ thị vô hướng** là đồ thị vô hướng cho phép có cạnh song song nhưng không có khuyên.
> ![image](https://hackmd.io/_uploads/HkXkjTkiZl.png)

> **Định nghĩa 4**: **Giả đồ thị** là đồ thị vô hướng cho phép có cả cạnh song song và khuyên.
> ![image](https://hackmd.io/_uploads/ByxMmsT1ibe.png)


### 2. Đồ thị có hướng (Directed Graph / Digraph)

#### 2.1. Định nghĩa cơ bản
> **Định nghĩa 5**: Một **đồ thị có hướng** $G = (V, E)$ bao gồm:
> - $V$: Tập hợp hữu hạn khác rỗng các **đỉnh**.
> - $E$: Tập hợp các cặp **có thứ tự** của hai đỉnh. Mỗi phần tử của $E$ được gọi là một **cung** (Arc) hoặc cạnh có hướng.
![image](https://hackmd.io/_uploads/rJFOipkobl.png)

**Các khái niệm liên quan:**
![image](https://hackmd.io/_uploads/S16hjpJoWe.png)

- Giả sử $e = (u, v)$ (ký hiệu đơn giản là $uv$) là một cung. Ta nói:
  - Cung $uv$ đi từ đỉnh $u$ đến đỉnh $v$.
  - Đỉnh $u$ là **đỉnh đầu** (gốc).
  - Đỉnh $v$ là **đỉnh cuối** (ngọn).
  - Đỉnh $v$ là đỉnh đi sau của đỉnh $u$.
  - Hai đỉnh $u$ và $v$ kề nhau.
- **Cung song song**: Hai hay nhiều cung có cùng đỉnh đầu và cùng đỉnh cuối.
- **Khuyên**: Một cung có đỉnh đầu và đỉnh cuối trùng nhau.

#### 2.2. Phân loại đồ thị có hướng
> **Định nghĩa 6**:
> - **Đơn đồ thị có hướng**: Là đồ thị có hướng không chứa các cung song song.
> - **Đa đồ thị có hướng**: Là đồ thị có hướng cho phép chứa các cung song song và khuyên.
![image](https://hackmd.io/_uploads/Skj-n6ko-e.png)

### 3. Bậc của đỉnh

Khái niệm bậc dùng để đếm số lượng các liên kết gắn với một đỉnh cụ thể.
![image](https://hackmd.io/_uploads/rJQbaTyjZg.png)


#### 3.1. Bậc trong đồ thị vô hướng
> **Định nghĩa 7**: Cho đồ thị vô hướng $G = (V, E)$ và $v \in V$.
> **Bậc của đỉnh $v$**, ký hiệu là $\deg(v)$, là số lượng cạnh kề với đỉnh $v$. 
> *Quy ước*: Một khuyên tại một đỉnh được tính là **2** lần khi tính bậc của đỉnh đó.

- Đỉnh có bậc bằng $0$ ($\deg(v) = 0$) gọi là **đỉnh cô lập** (Isolated vertex).
- Đỉnh có bậc bằng $1$ ($\deg(v) = 1$) gọi là **đỉnh treo** (Pendant vertex).

#### 3.2. Bậc trong đồ thị có hướng
Cho đồ thị có hướng $G = (V, E)$ và đỉnh $v \in V$. Do các cung có chiều, ta phân biệt hai loại bậc:
1.  **Bậc vào (In-degree)**: Ký hiệu là $\deg^-(v)$, là số lượng các cung đi vào đỉnh $v$ (số cung có đỉnh cuối là $v$).
2.  **Bậc ra (Out-degree)**: Ký hiệu là $\deg^+(v)$, là số lượng các cung đi ra từ đỉnh $v$ (số cung có đỉnh đầu là $v$).
3.  **Tổng bậc**: Bậc của đỉnh $v$ là tổng của bậc vào và bậc ra.
   $$\deg(v) = \deg^-(v) + \deg^+(v)$$
![image](https://hackmd.io/_uploads/rkMuRa1jZl.png)
![image](https://hackmd.io/_uploads/SJVnRpkiWe.png)

> Tóm lại, dương là số mũi tên đi ra, âm là số mũi tên đi vào

### 4. Các định lý cơ bản về bậc (Bổ đề bắt tay)

Mối liên hệ giữa tổng các bậc của các đỉnh và số lượng cạnh (hoặc cung) trong đồ thị được phát biểu qua các định lý sau. Giả sử đồ thị $G = (V, E)$ có tập đỉnh $V$ và $m$ cạnh (hoặc cung), tức là $|E| = m$.

**Định lý 1 (Cho đồ thị vô hướng):**
Tổng bậc của tất cả các đỉnh trong đồ thị bằng hai lần số cạnh của đồ thị. 
> Cạnh ở đây tính cả cạnh cong nhé

$$\sum_{v \in V} \deg(v) = 2m$$

**Định lý 2 (Cho đồ thị có hướng):**
Tổng các bậc vào của tất cả các đỉnh bằng tổng các bậc ra của tất cả các đỉnh, và bằng số lượng cung của đồ thị.
$$\sum_{v \in V} \deg^-(v) = \sum_{v \in V} \deg^+(v) = m$$

**Hệ quả (Định lý 3):**
Trong mọi đồ thị vô hướng, số lượng các đỉnh có bậc lẻ luôn luôn là một số chẵn.

## Phần 2: Biểu diễn, cấu trúc và phân loại đồ thị

### 5. Biểu diễn đồ thị bằng ma trận

Để xử lý đồ thị trên máy tính, ta cần chuyển đồ thị về các cấu trúc dữ liệu dạng số. Cách phổ biến nhất là sử dụng **ma trận kề** (Adjacency Matrix).

> **Định nghĩa**: Cho đồ thị $G = (V,E)$ với tập đỉnh $V = \{v_1, v_2, ..., v_n\}$. Ma trận kề của $G$ là ma trận vuông cấp $n$, ký hiệu $A = (a_{ij})_{n \times n}$, trong đó phần tử $a_{ij}$ được xác định như sau:
>$$a_{ij} = \text{số lượng cạnh (hoặc cung) đi từ đỉnh } v_i \text{ đến đỉnh } v_j$$

**Ví dụ 1: Tìm ma trận kề của đồ thị vô hướng**
Xét đồ thị vô hướng có 4 đỉnh $V = \{a, b, c, d\}$. Các cạnh là: $ab, ac, bc, bd, cd$.
Ma trận kề $A$ có cấp $4 \times 4$ là:
$$
\begin{bmatrix}
 & a & b & c & d \\
a & 0 & 1 & 1 & 0 \\
b & 1 & 0 & 1 & 1 \\
c & 1 & 1 & 0 & 1 \\
d & 0 & 1 & 1 & 0
\end{bmatrix}
$$
![image](https://hackmd.io/_uploads/SyYbZRyoWe.png)

**Ví dụ 2: Tìm ma trận kề của đồ thị có hướng (đa đồ thị)**
Xét một đa đồ thị có hướng gồm 6 đỉnh $V = \{a, b, c, d, e, f\}$. Từ đỉnh $a$ có 2 cung song song đi tới $b$, có 1 cung đi tới $c$. Từ đỉnh $b$ có 2 cung song song đi về $a$... Đỉnh $e$ có 1 khuyên.
Ma trận kề tương ứng được lập như sau:
$$
\begin{bmatrix}
 & a & b & c & d & e & f \\
a & 0 & 2 & 1 & 0 & 0 & 0 \\
b & 2 & 0 & 1 & 0 & 1 & 1 \\
c & 1 & 1 & 0 & 0 & 0 & 1 \\
d & 0 & 0 & 0 & 0 & 0 & 0 \\
e & 0 & 1 & 0 & 0 & 1 & 0 \\
f & 0 & 1 & 1 & 0 & 0 & 0
\end{bmatrix}
$$
![image](https://hackmd.io/_uploads/BJCdWR1obe.png)

### 6. Đẳng cấu đồ thị (Graph Isomorphism)

Hai đồ thị có thể được vẽ khác nhau nhưng về mặt cấu trúc toán học (số đỉnh, số cạnh, cách nối) lại hoàn toàn giống nhau.

> **Định nghĩa**: Cho hai đơn đồ thị $G = (V,E)$ và $G' = (V',E')$. Ta nói rằng $G$ **đẳng cấu** với $G'$, ký hiệu là $G \cong G'$, nếu tồn tại một song ánh $f: V \to V'$ sao cho:
>$$uv \text{ là cạnh của } G \iff f(u)f(v) \text{ là cạnh của } G'$$

**Chú ý**: Nếu $G$ và $G'$ đẳng cấu thì chúng bắt buộc phải có chung các tính chất bất biến sau:
1.  Cùng số đỉnh.
2.  Cùng số cạnh.
3.  Cùng dãy bậc (ví dụ: số lượng đỉnh có bậc 2 của đồ thị này phải bằng số lượng đỉnh có bậc 2 của đồ thị kia).
4.  Bậc của một đỉnh được bảo toàn qua phép ánh xạ: $\deg(v) = \deg(f(v))$.

**Các ví dụ về kiểm tra đẳng cấu:**
- **Ví dụ 1 (Đẳng cấu)**: Đồ thị hình vuông với các đỉnh sắp xếp theo thứ tự vòng tròn $(a,b,c,d)$ đẳng cấu với đồ thị hình vuông vẽ dưới dạng hai tam giác đan chéo có chung đỉnh. Cấu trúc kề của chúng hoàn toàn khớp nhau.
- **Ví dụ 2 (Không đẳng cấu)**: Đồ thị $G$ có 5 đỉnh hình ngôi nhà và đồ thị $G'$ có 5 đỉnh hình tam giác nối với 2 đỉnh bên dưới. $G$ và $G'$ **không đẳng cấu** vì trong $G'$ có một đỉnh treo (bậc 1), trong khi $G$ không có đỉnh nào bậc 1.
- **Ví dụ 3 (Không đẳng cấu)**: Hai đồ thị đều có 5 đỉnh, nhưng một đồ thị có các đỉnh mang bậc lần lượt là $(3, 3, 3, 2, 1)$ trong khi đồ thị kia có các bậc $(4, 2, 2, 1, 1)$. Vì dãy bậc khác nhau nên chúng không đẳng cấu.

### 7. Đường đi, chu trình, đồ thị liên thông

#### 7.1. Sự liên thông
Cho đồ thị vô hướng $G = (V,E)$. Trên tập đỉnh $V$, ta định nghĩa một quan hệ: $u \sim v \iff u = v$ hoặc tồn tại một đường đi từ $u$ đến $v$. Đây là một quan hệ tương đương.
![image](https://hackmd.io/_uploads/rk3zQAkiWg.png)

- Nếu $u \sim v$, ta nói hai đỉnh $u$ và $v$ **liên thông** với nhau.
- Mỗi lớp tương đương được gọi là một **thành phần liên thông** của $G$.
- Đồ thị $G$ được gọi là **liên thông** (Connected) nếu nó chỉ có đúng $1$ thành phần liên thông (tức là giữa hai đỉnh bất kỳ luôn có đường đi).

**Các phần tử cắt đứt sự liên thông:**
- **Đỉnh khớp (Articulation point)**: Đỉnh $v$ là đỉnh khớp nếu khi xóa $v$ và các cạnh kề với nó, đồ thị mất đi sự liên thông (tăng số thành phần liên thông).
- **Cầu (Bridge)**: Cạnh $e$ là cầu nếu khi xóa cạnh $e$, đồ thị mất đi sự liên thông.

#### 7.2. Đường đi và Chu trình
Xét đồ thị vô hướng $G = (V,E)$ và $u, v \in V$:
- **Đường đi (Dây chuyền)**: Một dãy luân phiên các đỉnh và cạnh liên tiếp nhau $v_0 e_1 v_1 e_2 ... v_{k-1} e_k v_k$ sao cho $v_0 = u$, $v_k = v$ và cạnh $e_i$ nối hai đỉnh $v_{i-1}$ và $v_i$. Chiều dài đường đi là số cạnh $k$.
- **Đường đi đơn**: Đường đi không có **cạnh** nào lặp lại.
- **Đường đi sơ cấp**: Đường đi không có **đỉnh** nào lặp lại.
- **Chu trình**: Một đường đi có đỉnh bắt đầu và đỉnh kết thúc trùng nhau ($v_0 = v_k$). Chu trình sơ cấp là chu trình không có đỉnh nào lặp lại (ngoại trừ đỉnh đầu/cuối).

**Ví dụ**: Cho một đồ thị, dãy $(a, e_1, b, e_2, c, e_3, d, e_4, b)$ là một đường đi từ $a$ đến $b$ có chiều dài 4.
![image](https://hackmd.io/_uploads/SyQScR1sWg.png)

(Trong đơn đồ thị, ta chỉ cần viết dãy đỉnh: $a-b-c-d-b$).
- Đường đi trên chứa các **chu trình sơ cấp** là: $(b, c, d, b)$ hoặc $(b, f, e, b)$.

### 8. Một số đồ thị đặc biệt

1.  **Đồ thị đầy đủ $K_n$ (Complete Graph)**: Là đơn đồ thị cấp $n$ (có $n$ đỉnh), trong đó hai đỉnh bất kỳ đều được nối với nhau bởi đúng 1 cạnh.
    - Số cạnh của $K_n$ là: $\sum_{i=1}^{n} i = \frac{n(n-1)}{2}$.

![image](https://hackmd.io/_uploads/ryHVaCkobl.png)

2.  **Đồ thị $k$-đều (Regular Graph)**: Là đồ thị mà mọi đỉnh đều có cùng bậc bằng $k$.
3.  **Đồ thị lưỡng phân (Bipartite Graph)**: Là đồ thị $G=(V,E)$ có thể chia tập đỉnh $V$ thành hai tập con $V_1, V_2$ rời nhau ($V_1 \cup V_2 = V$, $V_1 \cap V_2 = \emptyset$) sao cho mọi cạnh của $G$ đều nối một đỉnh thuộc $V_1$ với một đỉnh thuộc $V_2$.
4.  **Đồ thị lưỡng phân đầy đủ $K_{m,n}$**: Là đồ thị lưỡng phân mà mỗi đỉnh trong $V_1$ đều nối với mọi đỉnh trong $V_2$.
5.  **Đồ thị bù $\overline{G}$ (Complement Graph)**: Cho $G = (V, E_1)$ là đồ thị con của $K_n = (V,E)$. Đồ thị bù của $G$ là $\overline{G} = (V, E \setminus E_1)$. Hai đỉnh kề nhau trong đồ thị này thì không kề nhau trong đồ thị kia và ngược lại. Đồ thị tự bù nếu $G \cong \overline{G}$.
6.  **Đồ thị vòng $C_n$ (Cycles)**: Đồ thị tạo thành một vòng khép kín qua $n$ đỉnh ($n \ge 3$). Số cạnh của $C_n$ là $n$.
7.  **Đồ thị bánh xe $W_n$ (Wheels)**: Bổ sung thêm 1 đỉnh vào tâm của đồ thị vòng $C_n$ và nối đỉnh tâm đó với toàn bộ $n$ đỉnh trên vòng. Số cạnh của $W_n$ là $2n$.
8.  **Đồ thị siêu lập phương $Q_n$ (n-cubes)**: Đồ thị có $2^n$ đỉnh.

### 9. Đồ thị phẳng (Planar Graphs)

> Một đồ thị được gọi là **đồ thị phẳng** nếu ta có thể vẽ nó trên mặt phẳng sao cho các cạnh của nó không cắt nhau tại bất kỳ điểm nào khác ngoài các đỉnh. Cách vẽ như vậy gọi là biểu diễn phẳng.

- **Ví dụ**: Đồ thị đầy đủ $K_4$ là đồ thị phẳng. Đồ thị $K_5$ và $K_{3,3}$ là những đồ thị không phẳng cơ bản nhất.
- **Công thức Euler**: Giả sử một đồ thị phẳng liên thông có $n$ đỉnh, $m$ cạnh, chia mặt phẳng thành $r$ miền (bao gồm cả miền vô hạn nằm ngoài đồ thị). Khi đó ta có hệ thức:
 $$r = m - n + 2$$

## Phần 3: Tô màu đồ thị và ứng dụng

### 1. Bài toán tô màu đỉnh

**Bài toán**: Tìm số màu tối thiểu cần thiết để tô màu cho tất cả các đỉnh của một đồ thị sao cho không có hai đỉnh nào kề nhau lại được tô cùng một màu. Một cách tô màu thỏa mãn điều kiện này gọi là **cách tô đúng**.

> **Định nghĩa**:
> - Một đồ thị gọi là **$k$-sắc số** nếu nó có thể tô đúng bằng $k$ màu.
> - Số màu tối thiểu cần thiết để tô đúng một đồ thị $G$ gọi là **Sắc số** (Chromatic number) của đồ thị đó, ký hiệu là $S(G)$ hoặc $\chi(G)$.

### 2. Các định lý về Sắc số

1.  **Định lý 1**: Một đồ thị chu trình có độ dài lẻ ($C_{2k+1}$) luôn có sắc số bằng $3$.
2.  **Định lý 2**: Một đồ thị có ít nhất một cạnh là đồ thị $2$-sắc (sắc số bằng $2$) khi và chỉ khi nó không chứa bất kỳ chu trình nào có độ dài lẻ.
    - *Hệ quả*: Tất cả các chu trình độ dài chẵn ($C_{2k}$) đều có sắc số bằng $2$. Đồ thị lưỡng phân là đồ thị $2$-sắc.
3.  **Định lý 3**: Đồ thị đầy đủ với $n$ đỉnh ($K_n$) luôn có sắc số bằng $n$.
4.  **Định lý 4 (Định lý bốn màu)**: Mọi đồ thị phẳng đều có sắc số không vượt quá $4$. ($S(G) \le 4$).

### 3. Thuật toán tô màu đồ thị đơn (Tham lam / Welsh-Powell)

Để tìm cách tô màu thực tế cho một đồ thị, ta sử dụng thuật toán sau:

- **Bước 1**: Liệt kê và sắp xếp các đỉnh $v_1, v_2, ..., v_n$ theo thứ tự giảm dần của bậc: $\deg(v_1) \ge \deg(v_2) \ge ... \ge \deg(v_n)$.
- **Bước 2**: Gán **Màu 1** cho đỉnh $v_1$. Duyệt danh sách tiếp theo, gán Màu 1 cho đỉnh đầu tiên không kề với $v_1$, tiếp tục gán Màu 1 cho đỉnh tiếp theo không kề với *tất cả* các đỉnh đã mang Màu 1.
- **Bước 3**: Tìm đỉnh đầu tiên trong danh sách chưa được tô màu, gán **Màu 2** cho nó. Áp dụng lại quy tắc duyệt như Bước 2 (tô màu cho các đỉnh không kề với nhóm Màu 2).
- **Bước 4**: Tiếp tục lặp lại quá trình với **Màu 3, Màu 4,...** cho đến khi tất cả các đỉnh đều được tô màu.

### 4. Ứng dụng thực tế của tô màu đồ thị

#### Ví dụ: Bài toán xếp kho hóa chất
Giả sử một nhà hóa học cần cất giữ 5 loại hóa chất $a, b, c, d, e$ trong kho. Các hóa chất có tương tác mạnh không thể được để chung trong cùng một khu vực. Dấu `*` trong bảng dưới đây biểu diễn các cặp hóa chất không được để gần nhau:

| | a | b | c | d | e |
|:-:|:-:|:-:|:-:|:-:|:-:|
| **a** | - | * | * | * | - |
| **b** | * | - | * | * | * |
| **c** | * | * | - | * | - |
| **d** | * | * | * | - | * |
| **e** | - | * | - | * | - |

**Hỏi**: Cần ít nhất bao nhiêu khu vực (nơi) trong kho để cất giữ an toàn?
**Giải**:
Mô hình hóa bài toán thành đồ thị: Các đỉnh là hóa chất $\{a, b, c, d, e\}$. Hai đỉnh có cạnh nối nếu chúng tương tác nhau (có dấu `*`).
Bài toán phân khu vực chính là bài toán **tô màu đồ thị** (các hóa chất cùng màu sẽ vào chung một khu vực). Số khu vực ít nhất cần thiết chính là **Sắc số** của đồ thị này.

#### Các ứng dụng khác
- **Tô màu bản đồ**: Dùng ít màu nhất để tô các quốc gia trên bản đồ sao cho hai quốc gia có chung biên giới không trùng màu (Định lý 4 màu đảm bảo chỉ cần tối đa 4 màu).
- **Lập lịch thi**: Xếp lịch thi cho trường đại học sao cho không có sinh viên nào bị trùng 2 môn thi cùng lúc. (Đỉnh là môn thi, cạnh nối là có sinh viên thi chung 2 môn đó; màu là ca thi).
- **Phân chia tần số**: Cấp phát kênh/tần số vô tuyến cho các đài phát thanh/truyền hình sao cho các đài ở gần nhau (khoảng cách $\le 240$ km) không bị nhiễu sóng (không dùng chung kênh).
- **Cấp phát thanh ghi (Compiler)**: Phân bổ các thanh ghi (registers) trong CPU cho các biến trong quá trình biên dịch mã nguồn máy tính, giúp tối ưu hóa tốc độ vòng lặp.

## Phần 4: Đường đi Euler và Đường đi Hamilton

### 1. Đường đi và Chu trình Euler

#### 1.1. Bài toán mở đầu: Bảy cây cầu Königsberg
Vào thế kỷ 18, thành phố Königsberg (thuộc Phổ, nay là Kaliningrad, Nga) bị chia cắt bởi sông Pregel thành 4 khu vực đất liền. Các khu vực này được nối với nhau bởi 7 cây cầu.

**Câu hỏi đặt ra**: Liệu có thể xuất phát từ một điểm, đi qua đúng 7 cây cầu, mỗi cây cầu **chỉ đi qua đúng một lần**, và quay trở lại điểm xuất phát?

Leonhard Euler đã mô hình hóa bài toán này bằng lý thuyết đồ thị:
- 4 khu vực đất liền được biểu diễn bởi 4 **đỉnh**: $A, B, C, D$.
- Mỗi cây cầu được biểu diễn bởi 1 **cạnh** nối hai đỉnh.
- Bài toán trở thành: Tìm một chu trình trên đồ thị đi qua mọi cạnh, mỗi cạnh đúng một lần. Euler chứng minh điều này là không thể.

#### 1.2. Định nghĩa
> **Đường đi Euler** là một đường đi trên đồ thị đi qua **tất cả các cạnh**, mỗi cạnh đúng một lần.
>
> **Chu trình Euler** là một chu trình đi qua **tất cả các cạnh** của đồ thị, mỗi cạnh đúng một lần (điểm bắt đầu và kết thúc trùng nhau).
>
> Một đồ thị được gọi là **Đồ thị Euler** nếu nó có chứa một chu trình Euler.

#### 1.3. Điều kiện tồn tại
**Đối với đồ thị vô hướng (liên thông):**
- **Chu trình Euler**: Tồn tại khi và chỉ khi **mọi đỉnh** của đồ thị đều có **bậc chẵn**.
- **Đường đi Euler** (không phải chu trình): Tồn tại khi và chỉ khi đồ thị có **đúng hai đỉnh** có **bậc lẻ**, tất cả các đỉnh còn lại có bậc chẵn. Đường đi này sẽ bắt đầu tại một đỉnh bậc lẻ và kết thúc tại đỉnh bậc lẻ kia.

**Đối với đồ thị có hướng (liên thông yếu):**
- **Chu trình Euler**: Tồn tại khi và chỉ khi đồ thị **cân bằng**, tức là tại mọi đỉnh $v$, bậc vào bằng bậc ra: $\deg^-(v) = \deg^+(v)$.

#### 1.4. Thuật toán Fleury tìm Chu trình Euler
Để tìm một chu trình Euler trên một đồ thị Euler (đồ thị vô hướng, mọi đỉnh bậc chẵn), ta sử dụng thuật toán Fleury:
1.  Bắt đầu từ một đỉnh $v$ bất kỳ.
2.  Di chuyển theo một cạnh nối với đỉnh hiện tại. Tuân theo nguyên tắc: **Không bao giờ đi qua một "cầu"** (cạnh mà nếu xóa đi sẽ làm đồ thị mất liên thông), trừ khi đó là cách duy nhất để đi tiếp.
3.  Sau khi đi qua cạnh nào, **xóa** cạnh đó đi. Nếu thao tác xóa cạnh tạo ra một đỉnh cô lập, xóa luôn đỉnh đó.
4.  Tiếp tục quá trình cho đến khi không còn cạnh nào để đi. Dãy các đỉnh và cạnh vừa đi qua chính là một chu trình Euler.

### 2. Đường đi và Chu trình Hamilton

Khác với Euler tập trung vào cạnh, Hamilton tập trung vào đỉnh.

#### 2.1. Định nghĩa
> **Đường đi Hamilton** là một đường đi trên đồ thị đi qua **tất cả các đỉnh**, mỗi đỉnh đúng **một lần**.
>
> **Chu trình Hamilton** (mạch Hamilton) là một chu trình đi qua **tất cả các đỉnh**, mỗi đỉnh đúng **một lần** (ngoại trừ đỉnh xuất phát cũng là đỉnh kết thúc).
>
> Một đồ thị được gọi là **Đồ thị Hamilton** nếu nó chứa một chu trình Hamilton.

#### 2.2. Điều kiện tồn tại (Cho đồ thị đơn vô hướng)
Không có tiêu chuẩn cần và đủ đơn giản để kiểm tra một đồ thị bất kỳ có phải là đồ thị Hamilton hay không (đây là bài toán NP-đầy đủ). Tuy nhiên, có một số định lý nêu lên **điều kiện đủ**:

1.  **Định lý Ore (1960)**:
    Cho đơn đồ thị $G$ có $n$ đỉnh ($n \ge 3$). Nếu với mọi cặp đỉnh $i, j$ không kề nhau, ta luôn có $\deg(i) + \deg(j) \ge n$, thì $G$ là đồ thị Hamilton.
2.  **Định lý Dirac (1952)** (Hệ quả của định lý Ore):
    Cho đơn đồ thị $G$ có $n$ đỉnh ($n \ge 3$). Nếu mọi đỉnh $v$ đều có bậc $\deg(v) \ge \frac{n}{2}$, thì $G$ là đồ thị Hamilton.

#### 2.3. Điều kiện tồn tại (Cho đơn đồ thị có hướng)
Các định lý sau cung cấp điều kiện đủ cho đồ thị có hướng:

1.  **Định lý Meyniel (1973)**: Nếu $G$ là đồ thị liên thông mạnh (có đường đi có hướng giữa mọi cặp đỉnh) và với mọi cặp đỉnh $i, j$ không có cung nối trực tiếp ($ij \notin E$ và $ji \notin E$) thỏa mãn $\deg(i) + \deg(j) \ge 2n - 1$, thì $G$ là đồ thị Hamilton.
2.  **Định lý Camion (1959)**: Mọi đơn đồ thị có hướng, đầy đủ (giữa hai đỉnh bất kỳ luôn có đúng 1 cung nối) và liên thông mạnh đều là đồ thị Hamilton.
3.  **Định lý Ghouila-Houri (1960)**: Nếu $G$ là đơn đồ thị có hướng, liên thông mạnh và mọi đỉnh đều có tổng bậc (bậc vào + bậc ra) không nhỏ hơn $n$, thì $G$ là đồ thị Hamilton.
4.  **Định lý Woodall (1972)**: Nếu $G$ là đơn đồ thị có hướng sao cho với mọi cặp đỉnh $i, j$ mà không có cung $i \to j$ ($ij \notin E$) ta có $\deg^+(i) + \deg^-(j) \ge n$, thì $G$ là đồ thị Hamilton.

#### 2.4. Quy tắc xây dựng hoặc bác bỏ đồ thị Hamilton
Để tìm chu trình Hamilton $H$ hoặc chứng minh nó không tồn tại, ta áp dụng 4 quy tắc sau:

- **Quy tắc 1**: Bắt buộc phải chọn: Nếu một đỉnh có bậc đúng bằng 2, thì hai cạnh kề với nó bắt buộc phải nằm trong chu trình Hamilton $H$.
- **Quy tắc 2**: Chống chu trình con: Không được phép tạo ra bất kỳ chu trình con nào có độ dài nhỏ hơn số đỉnh $n$ trong quá trình xây dựng $H$.
- **Quy tắc 3**: Loại bỏ cạnh thừa: Khi chu trình $H$ đang xây dựng đã sử dụng đúng 2 cạnh kề với đỉnh $v$ nào đó, ta phải "xóa" (bỏ qua) tất cả các cạnh còn lại kề với $v$ (vì một đỉnh trong chu trình chỉ nối với đúng 2 đỉnh khác). Thao tác này có thể tạo ra các đỉnh bậc 2 mới, ta lại quay lại áp dụng Quy tắc 1.
- **Quy tắc 4**: Bác bỏ: Sau khi áp dụng Quy tắc 3 (xóa các cạnh không dùng), nếu xuất hiện một đỉnh bị cô lập (bậc 0) hoặc một đỉnh treo (bậc 1), thì kết luận ngay đồ thị đó không có chu trình Hamilton.

## Phần 5: Bài toán đường đi ngắn nhất (Shortest Path Problem)

### 1. Đồ thị có trọng số (Weighted Graph)

> **Định nghĩa**:
> 1.  Một đồ thị $G=(V, E)$ được gọi là **đồ thị có trọng số** (hoặc chiều dài, trọng lượng) nếu mỗi cạnh (hoặc cung) $e \in E$ được gán với một số thực, ký hiệu là $w(e)$, gọi là **trọng số** của cạnh.
> 2.  **Độ dài** của một đường đi trong đồ thị có trọng số là tổng trọng số của các cạnh tạo nên đường đi đó.
> 3.  **Khoảng cách** giữa hai đỉnh $u$ và $v$, ký hiệu là $d(u,v)$, là độ dài ngắn nhất của tất cả các đường đi có thể có từ $u$ đến $v$.

#### Ma trận khoảng cách (Ma trận trọng số)
Đối với một đồ thị có trọng số $G=(V, E)$ với $V=\{v_1, ..., v_n\}$, ta có thể biểu diễn các trọng số dưới dạng ma trận khoảng cách (hoặc ma trận trọng số) $D = (d_{ij})_{n \times n}$:
$$
d_{ij} =
\begin{cases}
0 & \text{nếu } i = j \\
w(v_i v_j) & \text{nếu } v_i \text{ và } v_j \text{ kề nhau} \\
\infty & \text{nếu } v_i \text{ và } v_j \text{ không kề nhau}
\end{cases}
$$

**Ví dụ:** Cho đồ thị có hướng, có trọng số với 7 đỉnh như hình vẽ.
Ma trận khoảng cách $D$ tương ứng là:
$$
D =
\begin{bmatrix}
0 & 5 & 31 & 40 & \infty & \infty & \infty \\
\infty & 0 & \infty & \infty & 73 & \infty & \infty \\
\infty & 26 & 0 & 8 & 49 & 25 & 38 \\
\infty & \infty & \infty & 0 & \infty & 16 & \infty \\
\infty & 70 & \infty & \infty & 0 & \infty & 9 \\
\infty & \infty & \infty & \infty & 23 & 0 & 12 \\
\infty & \infty & \infty & \infty & 10 & \infty & 0
\end{bmatrix}
$$

### 2. Thuật toán Dijkstra (Tìm đường đi ngắn nhất từ một đỉnh)

**Bài toán**: Cho đồ thị $G=(V,E)$ (có hướng hoặc vô hướng) có trọng số **không âm** ($w(e) \ge 0$). Tìm đường đi ngắn nhất từ một đỉnh xuất phát $u_0$ đến tất cả các đỉnh còn lại trong đồ thị.

**Ý tưởng thuật toán**:
Thuật toán xây dựng tập các đỉnh đã tìm được đường đi ngắn nhất một cách "tham lam". Tại mỗi bước, thuật toán sẽ tìm đỉnh `v` chưa được xét mà có khoảng cách tạm thời đến $u_0$ là ngắn nhất, sau đó "kết nạp" đỉnh `v` này vào tập đã xét.

**Các bước thực hiện:**
- **Khởi tạo**:
  - Gán nhãn khoảng cách cho đỉnh xuất phát $u_0$ là $L(u_0) = 0$.
  - Gán nhãn khoảng cách cho tất cả các đỉnh khác là $L(v) = \infty$.
  - Khởi tạo tập $S$ chứa tất cả các đỉnh của đồ thị (tập các đỉnh chưa được xét).

- **Lặp**: Trong khi $S$ chưa rỗng:
  1.  Chọn đỉnh $u \in S$ có nhãn khoảng cách $L(u)$ là nhỏ nhất.
  2.  Loại $u$ ra khỏi $S$.
  3.  Với mỗi đỉnh $v$ kề với $u$ (và $v$ vẫn còn trong $S$):
      - Cập nhật lại nhãn khoảng cách cho $v$ nếu tìm được đường đi ngắn hơn thông qua $u$:
       $$L(v) = \min(L(v), L(u) + w(uv))$$
      - Nếu $L(v)$ được cập nhật, ghi nhớ rằng đỉnh trước của $v$ trên đường đi ngắn nhất là $u$.

- **Kết thúc**: Khi $S$ rỗng, nhãn $L(v)$ của mỗi đỉnh $v$ chính là khoảng cách ngắn nhất $d(u_0, v)$. Ta có thể truy vết lại các đỉnh trước để xây dựng đường đi cụ thể.

**Lưu ý quan trọng**: Thuật toán Dijkstra chỉ hoạt động đúng khi tất cả các trọng số của cạnh đều **không âm**.

**Ví dụ**: Áp dụng thuật toán Dijkstra để tìm đường đi ngắn nhất từ đỉnh `u` đến các đỉnh còn lại.

| Bước | Đỉnh xét | $L(r)$ | $L(s)$ | $L(t)$ | $L(x)$ | $L(y)$ | $L(z)$ | $L(w)$ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | - | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ | $\infty$ |
| 1 | u(0) | 4 | $\infty$ | $\infty$ | $\infty$ | **1** | $\infty$ | $\infty$ |
| 2 | y(1) | **3** | $\infty$ | $\infty$ | $\infty$ | - | **4** | $\infty$ |
| 3 | r(3) | - | 10 | **6** | $\infty$ | - | 4 | $\infty$ |
| 4 | z(4) | - | 10 | 6 | **7** | - | - | **9** |
| 5 | t(6) | - | **9** | - | 7 | - | - | 9 |
| 6 | x(7) | - | **8** | - | - | - | - | 9 |
| 7 | s(8) | - | - | - | - | - | - | 9 |
| 8 | w(9) | - | - | - | - | - | - | - |

- **Kết quả cuối cùng**:
  - $d(u,y) = 1$ (đường đi: u-y)
  - $d(u,r) = 3$ (đường đi: u-y-r)
  - $d(u,z) = 4$ (đường đi: u-y-z)
  - $d(u,t) = 6$ (đường đi: u-y-r-t)
  - $d(u,x) = 7$ (đường đi: u-y-r-t-x)
  - $d(u,s) = 8$ (đường đi: u-y-r-t-x-s)
  - $d(u,w) = 9$ (đường đi: u-y-z-w)

### 3. Thuật toán Ford-Bellman (Bellman-Ford)

**Bài toán**: Cho đồ thị có hướng $G=(V,E)$ với trọng số có thể **âm**, nhưng **không có chu trình âm** (chu trình có tổng trọng số là một số âm). Tìm đường đi ngắn nhất từ đỉnh xuất phát $u_0$ đến các đỉnh khác. Thuật toán này cũng có thể phát hiện sự tồn tại của chu trình âm.

**Ý tưởng thuật toán**:
Thuật toán dựa trên nguyên lý "thư giãn" (relaxation). Nó lặp lại quá trình cập nhật khoảng cách cho tất cả các cung của đồ thị. Sau $k$ lần lặp, thuật toán sẽ tìm được đường đi ngắn nhất có tối đa $k$ cạnh. Vì đường đi ngắn nhất không có chu trình sẽ có tối đa $|V|-1$ cạnh, thuật toán sẽ lặp lại $|V|-1$ lần.

**Các bước thực hiện:**
- **Bước 1: Khởi tạo**
  - Gán nhãn khoảng cách cho đỉnh xuất phát $u_0$ là $L(u_0) = 0$.
  - Gán nhãn khoảng cách cho tất cả các đỉnh khác là $L(v) = \infty$.

- **Bước 2: Lặp**
  - Lặp lại $|V|-1$ lần:
    - Với mỗi cung $(u, v) \in E$:
      - Thực hiện phép "thư giãn": Nếu $L(u) + w(uv) < L(v)$, thì cập nhật $L(v) = L(u) + w(uv)$ và ghi nhận đỉnh trước của $v$ là $u$.

- **Bước 3: Kiểm tra chu trình âm**
  - Sau khi hoàn thành $|V|-1$ lần lặp, thực hiện thêm một lần lặp nữa:
    - Với mỗi cung $(u, v) \in E$:
      - Nếu vẫn còn có thể "thư giãn" (tức là $L(u) + w(uv) < L(v)$), điều này chứng tỏ đồ thị có chứa một **chu trình âm** có thể đi đến được từ $u_0$. Trong trường hợp này, không tồn tại đường đi ngắn nhất (vì ta có thể đi vòng qua chu trình âm vô hạn lần để giảm độ dài).
      - Nếu không có sự cập nhật nào, thì các giá trị $L(v)$ là kết quả cuối cùng.

**Ví dụ có chu trình âm**:
Xét đồ thị có 3 đỉnh $a,b,c$ và các cung $a \to b$ (trọng số 5), $a \to c$ (trọng số 4), $c \to b$ (trọng số -3).
1. Dijkstra sẽ chọn đường $a \to c$ (độ dài 4), rồi kết thúc. Kết quả $d(a,b)=5, d(a,c)=4$.
2. Bellman-Ford sẽ tìm ra đường $a \to c \to b$ có độ dài $4 + (-3) = 1$, ngắn hơn đường $a \to b$ trực tiếp.

**So sánh Dijkstra và Bellman-Ford:**
| Tiêu chí | Thuật toán Dijkstra | Thuật toán Bellman-Ford |
|---|---|---|
| **Điều kiện trọng số** | Không âm ($w \ge 0$) | Có thể âm, không có chu trình âm |
| **Độ phức tạp** | Nhanh hơn: $O(E \log V)$ | Chậm hơn: $O(V \cdot E)$ |
| **Khả năng** | Không phát hiện được chu trình âm | Phát hiện được chu trình âm |

