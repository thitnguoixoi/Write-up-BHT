# Write-up-BHT
## Bài 1
### Đề bài:

`Đọc xong lú chả biết làm sao`

 ![image](https://user-images.githubusercontent.com/93463752/139774107-1112139d-7008-42f2-90ac-c8245d0b92d4.png)

### Ý tưởng:

- Ta thấy rằng `x^11= x^8 * x^3`
- Để có `x^8` và `x^3` thì ban đầu ta phải có `x^2`
  - `x^8= x^4 * x^4` và `x^4= x^2 * x^2`
  - `x^3= x^2 * x`
  - `x^2= x * x`
 Ở đây ta có 5 phép nhân và đầy cũng là số phép nhân tối thiểu của bài toán
 
### Code:

```c++
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

```c++
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
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139791109-57115a12-1c19-4ae3-9f8a-00ab8ab7df6e.png)

### Ý tưởng:

- T nhận thấy phép toán là một cấp số nhân bước nhảy là x chia cho cấp số cộng bước nhảy là 1
- Ta sẽ dùng vòng lặp để tính toán và sử dụng biến phụ để tính tử và mẫu: `tu*=x` và `mau+=i`

### code:

```c++
#include <iostream>
using namespace std;
int main(){
    int x,n;
    cin>>x>>n;
    int tu=1,mau=0;
    double s=0;
    for (int i=1;i<=n;i++){
        tu=tu*x;
        mau=mau+i;
        s=s+double(tu)/mau;
    }
    cout<<s;
}
```
## Bài 4
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139791321-2d2e0e55-b5e6-46b2-8018-7096d428ba30.png)

### Ý tưởng: 

- Sử dụng vòng lặp để tính toán
- sau mỗi lần lặp thì phần tử sẽ đổi dấu

### Code

```c++
#include <iostream>
using namespace std;
int main(){
   int x,n;
   cin>>x>>n;
   int a=1,b=1,s=0;
   for(int i=0;i<n;i++){
       a*=-1;
       b*=x;
       s+=a*b*b;
   }
   cout << "s = " << s << endl;
}
```
## Bài 5
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139800495-64e25333-12bd-4f2a-ae42-7532b76b5953.png)

### Ý tưởng:

- Bài toán có dạng Sn= căn ( x^n + Sn-1)
- Sử dụng vòng lặp

### Code:

```c++
#include <iostream>
#include <math.h> 
using namespace std;
int main(){
    int x,n,a=1;
    cin>>x>>n;
    double sum=0;
    for (int i=1;i<=n;i++){
        a*=x;
        sum=sqrt(a+sum);
    }
    cout<< sum;
}
```
## Bài 6
### Đề bài:
`Đề bị sai nên đọc xong lú 😢`

![image](https://user-images.githubusercontent.com/93463752/139803825-a4b44367-fd94-4bda-93c2-46f11f9649a2.png)

### Ý tưởng:

- Ví dụ: ta có số 1,1234= 1 + 0,1 + 0,02 + 0,003 + 0,0004 thì độ chính xác của số này là 10^-4
- Để kết quả có độ chính xác là 10^-6 thì số hạng cuối cùng phải có dạng: 1/n <= 10^-6

### Code:

```c++
#include <iostream>
using namespace std;
int main(){
    double s = 0.0, e=1, i=1;
    while (e>=0.000001){ 
        e=1/i;
        s+=e;
        i++;
    }
    cout<<s;
}
```
## Bài 7
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139806058-b8d2c113-7b48-4840-8c18-94483c2c7518.png)

### Ý tưởng:

- Sử dụng vòng lặp
- Dùng biến phụ để tính mũ của 3 và 7
- Sử dụng kết quả của vòng lặp trước đó để tính

### Code:

```c++
#include <iostream>
using namespace std;
int main(){
    int a=-2,n,b=1,c=1;
    cin>>n;
    for (int i=2;i<=n;i++){
        b*=3;
        c*=7;
        a=5*a+2*b-6*c+12;
    }
    cout<<"a= "<<a<<endl;
}
```
## Bài 8:
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139810042-2c106435-1324-46cc-ad06-547c34387de2.png)

### Ý tưởng:

- Sử dụng các tính chất của các loại tam giác

### Code:

```c++
#include <iostream>
using namespace std;
int main(){
    int x,y,z;
    cin>>x>>y>>z;
    if (x*x+y*y==z*z || x*x+z*z==y*y || z*z+y*y==x*x) {
        if (x==y|| x==z|| z==y){ 
            cout<<"tam giac vuong can";
        }
        else{ 
            cout<<"tam giac vuong";
        }
    }
    else if (x==y && x==z && z==y)
        cout<<"tam giac deu";
    else if (x==y || x==z || z==y)
        cout<<"tam giac can";
    else
        cout<<"tam giac thuong"; 
}
```
## Bài 9
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139810252-a0fd7ff0-9e3f-4b03-82c7-583e7f350a31.png)

### Ý tưởng:

- Căn của n có phải là một số nguyên hay không

### Code: 

```c++
#include <iostream>
#include <math.h>
using namespace std;
int main(){
    int n,a;
    cin>>n;
    a=int(sqrt(n));
    if (sqrt(n)==a){
        cout<<"so chinh phuong";
    }
    else{ 
        cout<<"khong la so chinh phuong";
    }
}
```
## Bài 10
### Đề bài:

![image](https://user-images.githubusercontent.com/93463752/139810736-d1152661-1c55-43d8-9c8c-4887e451d9e7.png)

### Ý tưởng:

- Trường hợp 1: n=0 thì xuất ra kết quả rồi đóng trương trình tại đó
- Trường hợp 2: sử dụng vòng lặp: kết quả của mỗi vòng lặp phải chia hết cho 5 hoặc bằng 1

### Code: 

```c++
#include <iostream>
using namespace std;
int main(){
   int n;
   cin>>n;
   if (n==0){
       cout << "co dang 5^m ";
       return 0;
   }
   while (n%5==0){
       n=n/5;
   }
   if (n==1)
       cout << "co dang 5^m ";
   else
       cout<<"khong phai dang 5^m";
}
```
