# Ước chung lớn nhất
1. <strong>Khái niệm:</strong>
  Trong toán học, nếu số nguyên a chia hết cho số nguyên b thì số b được gọi là ước của số nguyên a, a được gọi là bội của b. Số nguyên dương b lớn nhất là ước của cả hai số nguyên a, b được gọi là ước số chung lớn nhất (ƯCLN) của a và b. Trong trường hợp cả hai số nguyên a và b đều bằng 0 thì chúng không có ƯCLN vì khi đó mọi số tự nhiên khác không đều là ước chung của a và b. Nếu chỉ một trong hai số a hoặc b bằng 0, số kia khác 0 thì ƯCLN của chúng bằng giá trị tuyệt đối của số khác 0.
2. <strong>Ký hiệu :</strong> ƯCLN(a,b), (a,b), GCD(a,b), GCF(a,b)
3. <strong> Mục đích:</strong> đưa phân số về dạng tối giản
4. <strong> Tính chất </strong><br>
  - mọi ước chung của a,b đều là ước của (a,b)
  - 
2. Tìm ước chung lớn nhất của 2 số a,b
3. Tìm ước chung lớn nhất của 2013^2+2^2013 và 2013

-![Bài Toán](https://scontent.fvca1-1.fna.fbcdn.net/v/t1.15752-9/60028846_328269527862150_6232530242699788288_n.png?_nc_cat=108&_nc_oc=AQlMfdMqhzC39IriG-0TRoWFz9FeETe0IwabMeXa2G0ejqNdE-a49czq4dujnga3hk0&_nc_ht=scontent.fvca1-1.fna&oh=51b020f6f8b6ca096c8b4b8ea2ef1a0a&oe=5D6A7074)

```pascal
{Thuật toán Euclide: a, b không đồng thời bằng 0, trả về gcd(a, b)}
function gcd(a, b);
begin
  while b ≠ 0 do
    begin
      r:= a mod b; a:= b; b:= r;
    end;
  Result:= a;
end;
{Thuật toán Euclide mở rộng: a, b không đồng thời bằng 0, trả về cặp (x, y) sao cho a * x + b * y = gcd(a, b)
Về tư tưởng là ghép quá trình tính cặp số (x, y) vào trong vòng lặp chính của thuật toán Euclide.}
function Extended_gcd(a, b); 
begin
  (xa, ya):= (1, 0);
  (xb, yb):= (0, 1);
  while b ≠ 0 do
    begin
      q:= a div b;
      r:= a mod b; a:= b; b:= r; //Đoạn này giống thuật toán Euclide.
      (xr, yr):= (xa, ya) - q * (xb, yb); //Hiểu là: (xr, yr):= (xa, ya) "mod" (xb, yb);
      (xa, ya):= (xb, yb);
      (xb, yb):= (xr, yr);
    end;
  Result:= (xa, ya);
end;

```

```pascal
//a, m > 0. Trả về a^-1 mod m, gcd(a, m) phải bằng 1, chú ý là ta không cần quan tâm y khi giải pt diophante a * x + m * y = 1
function ModuloInverse(a, m);
begin
  xa:= 1; xm:= 0;
  while m ≠ 0 do
    begin
      q:= a div m;
      xr:= xa - q * xm;
      xa:= xm;
      xm:= xr;
      r:= a mod m;
      a:= m;
      m:= r;
    end;
  Result:= xa;
end;
```
