# DS201 - Lab 2: Convolutional Neural Networks

**MSSV:** 24521157  
**Họ tên:** Lương Trần Kim Ngọc  
**Môn học:** DS201 - Deep Learning trong Khoa học Dữ liệu  
**Dataset:** VinaFood21

## Nội dung bài làm

Notebook `24521157_Lab2.ipynb` thực hiện đầy đủ các nội dung của Lab 2:

- **Bài 1 - LeNet-5:** so sánh `AvgPool` và `MaxPool` trên ảnh `64x64`.
- **Bài 2 - MiniGoogLeNet:** xây dựng mô hình rút gọn với 3 Inception blocks.
- **Bài 3* - ResNet-18:** huấn luyện từ đầu trên ảnh `96x96`, so sánh có và không data augmentation.
- **Bài 4* - ResNet-50 pretrained:** so sánh Feature Extraction và Fine-tuning với `microsoft/resnet-50`.

Các mô hình được đánh giá bằng Accuracy, Precision Macro, Recall Macro và Macro-F1. Notebook cũng bao gồm loss curve, classification report, confusion matrix và phần nhận xét/kết luận cho từng thí nghiệm.

## Cấu trúc repository

```text
DS201_Lab2_24521157/
├── 24521157_Lab2.ipynb        # Bài làm chính
├── README.md                  # Mô tả repository và hướng dẫn chạy
├── requirements.txt           # Các thư viện cần thiết
├── .gitignore                 # Loại bỏ dataset/cache/checkpoint khỏi Git
└── reference/
    └── assignments.ipynb      # File đề bài gốc
```

## Cài đặt

Có thể chạy notebook trên Google Colab, Kaggle hoặc môi trường Python cục bộ.

```bash
pip install -r requirements.txt
```

Khuyến nghị sử dụng GPU cho ResNet-18 và ResNet-50.

## Dataset

Bài sử dụng **VinaFood21**. Dataset không được commit lên repository để tránh làm repo quá lớn.

## Cách chạy

1. Mở `24521157_Lab2.ipynb` bằng Google Colab hoặc Jupyter Notebook.
2. Chạy các cell theo thứ tự từ trên xuống.
3. Notebook sẽ kiểm tra/cài các thư viện còn thiếu và tải dataset khi cần.
4. Các mô hình nặng, đặc biệt ResNet-18 và ResNet-50, nên chạy trên GPU.

> Notebook đã lưu output của các lần chạy chính để có thể xem kết quả mà không cần huấn luyện lại toàn bộ mô hình.

## Kết quả tổng hợp

| Model | Setting | Resize | Parameters | Accuracy | Macro-F1 |
|---|---|---:|---:|---:|---:|
| LeNet | AvgPool | 64x64 | 339,421 | 0.2929 | 0.2657 |
| LeNet | MaxPool | 64x64 | 339,421 | 0.3251 | 0.2986 |
| MiniGoogLeNet | 3 Inception blocks | 64x64 | 84,117 | 0.3861 | 0.3608 |
| ResNet-18 | No augmentation | 96x96 | 11,187,285 | 0.3911 | 0.3650 |
| ResNet-18 | Augmentation | 96x96 | 11,187,285 | 0.4454 | 0.4256 |
| ResNet-50 pretrained | Feature Extraction | 224x224 | 23,551,061 | 0.6118 | 0.6100 |
| ResNet-50 pretrained | Fine-tuning | 224x224 | 23,551,061 | **0.8589** | **0.8581** |

## Kết luận chính

- Với LeNet, **MaxPool** cho kết quả tốt hơn AvgPool trên tập test.
- MiniGoogLeNet đạt kết quả tốt hơn LeNet dù có ít tham số hơn đáng kể.
- Data augmentation giúp ResNet-18 giảm overfitting và cải thiện Macro-F1 từ `0.3650` lên `0.4256`.
- ResNet-50 pretrained cho kết quả vượt trội so với các mô hình huấn luyện từ đầu.
- **ResNet-50 Fine-tuning** đạt kết quả tốt nhất với Accuracy `85.89%` và Macro-F1 `0.8581`.



