# 🤖 So sánh Machine Learning và Deep Learning trong Phân tích Logfile Server

## 📌 Giới thiệu
Logfile là nguồn dữ liệu quan trọng để:
- Phát hiện bất thường trong hệ thống mạng  
- Phân tích sự cố & bảo mật  
- Giám sát hiệu suất hoạt động  

Trong đề tài này, chúng tôi triển khai **các mô hình Machine Learning và Deep Learning** để phân tích logfile, từ đó so sánh hiệu quả giữa hai hướng tiếp cận.

---

## 🧩 Quy trình nghiên cứu
1. **Chuẩn bị dữ liệu**
   - Dataset: *Internet Firewall Dataset* (12 đặc trưng, 4 nhãn: `allow`, `deny`, `drop`, `reset-both`)  
   - Tiền xử lý: loại bỏ trùng lặp, xử lý giá trị null, chuẩn hóa dữ liệu  
   - Giải quyết mất cân bằng dữ liệu bằng **SMOTE**

2. **Machine Learning (ML)**
   - 🔹 Random Forest  
   - 🔹 XGBoost  
   - 🔹 Support Vector Machine (SVM)  

3. **Deep Learning (DL)**
   - 🔹 Convolutional Neural Network (CNN)  
   - 🔹 Long Short-Term Memory (LSTM)  

4. **Đánh giá mô hình**
   - Accuracy, Precision, Recall, F1-score  
   - Ma trận nhầm lẫn (Confusion Matrix)  
   - ROC & AUC  

---

## 📊 Kết quả so sánh

### 🏗️ Machine Learning
| Mô hình          | Accuracy | F1-score | Precision | Recall |
|------------------|----------|----------|-----------|--------|
| Random Forest    | 0.9962   | 0.8227   | 0.8007    | 0.8809 |
| XGBoost          | **0.9970** | **0.8239** | **0.8021** | **0.8819** |
| SVM              | 0.9474   | 0.7044   | 0.7439    | 0.8501 |

👉 **XGBoost tốt nhất trong nhóm ML**, vượt trội hơn SVM rõ rệt.

---

### 🧠 Deep Learning
| Mô hình | Accuracy | Nhận xét |
|---------|----------|----------|
| CNN     | 0.99     | Phân loại tốt các lớp phổ biến (`allow`, `deny`, `drop`), yếu hơn ở lớp hiếm `reset-both` |
| LSTM    | 0.99     | Xử lý lớp hiếm (`reset-both`) tốt hơn CNN, nhưng nhầm lẫn nhiều ở lớp `deny` |

👉 **CNN có độ khái quát hóa tốt hơn, LSTM mạnh hơn khi xử lý chuỗi và lớp hiếm.**

---

## 🚀 Kết luận
- **ML vs DL**
  - ML (Random Forest, XGBoost) cho kết quả **rất cao và ổn định**, dễ triển khai hơn.  
  - DL (CNN, LSTM) mạnh khi xử lý dữ liệu dạng chuỗi, nhưng yêu cầu nhiều tài nguyên hơn.  

- **So sánh**
  - Với dữ liệu log tĩnh → **XGBoost** là lựa chọn tối ưu.  
  - Với log chuỗi thời gian & ngữ cảnh dài → **LSTM** cho hiệu quả tốt hơn.  
