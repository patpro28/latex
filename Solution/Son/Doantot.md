## Kiến thức cần biết  
Fenwick Tree

## Chi tiết  

### Ý tưởng chính  
- Đưa các truy vấn về $OFFLINE$ để xử lý.  
- Gọi $cnt[j]$ là số lượng đoạn tốt kết thúc tại $j$.  

### Cài đặt  
1. Với mỗi giá trị $L$, dùng một mảng lưu lại danh sách cặp ($R$, $index$), trong đó, $R$ là giới hạn phải và $index$ là chỉ số của truy vấn tương ứng.
```cpp
    vector<pair<int, int> > query[N + 5];
    ...
    for (int i = 1; i <= q; i++) {
        int l, r;
        cin >> l >> r;
        query[l].push_back({i, r});    
    }
```
2. Ta dùng một vòng lặp đi từ phần tử cuối về đầu. Khi xét vị trí $l$:  
   - Dùng một vòng lặp kiểm tra đoạn tốt từ vị trí $l$ (đảm bảo tổng độ phức tạp không quá $O(\log(10^{18}) \approx 60)$) để cập nhật các vị trí $i$ thỏa mãn đoạn tốt bắt đầu từ $l$ và kết thúc từ $i$.  
    ```cpp
    for (int i = l; i <= n; i++) {
        if (a[i] % (i - l + 1) == 0) cnt[i]++;
        else break;
    }
    ```
   - Xử lí truy vấn tại $l$.
    ```cpp  
    for (pair<int, int> i : query[l]) {
        res[i.fi] = 0;
        for (int j = l; j <= i.se; j++) {
            res[i.fi] += cnt[j];
        }
    }
    query[l].clear();
    ```
### Tối ưu: 
- Sử dụng cấu trúc dữ liệu như Fenwick Tree hoặc Segment Tree để tính nhanh tổng $cnt[j]$ trong đoạn $[l, r]$.
```cpp
for (int l = n; l >= 1; l--) {
    for (int i = l; i <= n; i++) {
        if (a[i] % (i - l + 1) == 0) {
            updateRange(i, i, 1);
        }
        else break;
    }
    for (auto& i : query[l]) {
        res[i.fi] = rangeSum(l, i.se);
    }
    query[l].clear();
}
```

### Độ phức tạp: $O(N \cdot \log N)$