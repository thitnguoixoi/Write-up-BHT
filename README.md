# Write-up-BHT
## Bài 1
### Đề bài:
  Đọc xong lú chả biết làm sao

 ![image](https://user-images.githubusercontent.com/93463752/139774107-1112139d-7008-42f2-90ac-c8245d0b92d4.png)

### Ý tưởng:
- Ta thấy rằng `x^11= x^8 * x^3`
- Để có `x^8` và `x^3` thì ban đầu ta phải có `x^2`
  - `x^8= x^4 * x^4` và `x^4= x^2 * x^2`
  - `x^3= x^2 * x`
  - `x^2= x * x`
 Ở đây ta có 5 phép nhân và đầy cũng là số phép nhân tối thiểu của bài toán
### Code:

```c
		#include <iostream>
		using namespace std;
		int main(){
			int x,x2,x4,x8,x11;
			cin>>x;
			x2=x*x;
			x4=x2*x2;
			x8=x4*x4;
			x11=x8*x2*x;
			cout << x11 << endl;
			return 0;
		}
```
## Bài 2
### Đề bài:
	Đề bài quen thuộc :))
	
![image](https://user-images.githubusercontent.com/93463752/139777206-86e9a5d1-0a75-42c8-bb5d-bc7daf421f76.png)

### Ý tưởng:
Giả sử ca có 1 sớ nguyên dương là abcd
- Nếu tính toán bình thường minh chỉ cần lấy các số cộng lại với nhau: `a+ b+ c+ d`.
- Trong lập trình ta không thể cộng trực tiếp mà ta phân tích được rằng abcd= a*(10^3)+ b*(10^2)+ c*(10^1)+ d*(10^0)
- C++ cung cấp cho ta 2 phép tính: chia lấy dư và chia lấy nguyên
	- Ta lấy số `n` chia lấy dư cho 10 và cộng nó vào 1 biến chứa tổng của các số: `s+= n%10`
	- Gán ngược lại cho n kết quả của phép tính n/10: `n=n/10`

### Code:

```c
	#include <iostream>
	int main(){
    int n;
    scanf("%d",&n);
    int s=0;
    while (n!=0) { 
        s+=n%10;
        n=n/10;
    }
    printf("%d\n",s); 
}
```
## Bài 3
### 
### Ý tưởng:
- T nhận thấy phép toán là một cấp số nhân bước nhảy là x chia cho cấp số cộng bước nhảy là 1
- Ta sẽ dùng vòng lặp để tính toán
	
