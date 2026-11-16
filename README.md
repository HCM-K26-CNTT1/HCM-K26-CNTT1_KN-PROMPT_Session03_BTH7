# **BÀI THỰC HÀNH 7: XÂY DỰNG HỆ THỐNG HỖ TRỢ TUYỂN DỤNG BẰNG AI**

## **PHẦN 1. XÂY DỰNG PROMPT THEO CREATE (FEW-SHOT)**

### **1.1. Quy tắc chấm điểm**

Tổng điểm tối đa: 100 điểm.

| Tiêu chí           | Điểm tối đa | Nội dung đánh giá                                                          |
| ------------------ | ----------- | -------------------------------------------------------------------------- |
| Kỹ năng chuyên môn | 70          | Java (20), OOP (15), SQL (15), PostgreSQL (10), Git (10).                  |
| Kinh nghiệm/dự án  | 30          | Dự án thực tế hoặc cá nhân, kinh nghiệm thực tập và làm việc có liên quan. |
| Tổng điểm          | 100         | Tổng điểm kỹ năng chuyên môn và kinh nghiệm/dự án.                         |

Quy tắc phân loại:

- Từ 80 điểm: PHÙ HỢP CAO.
- Từ 60 đến dưới 80 điểm: CẦN XEM XÉT.
- Dưới 60 điểm: CHƯA PHÙ HỢP.

Lưu ý: Không có thông tin về teamwork trong JD và CV nên không tự ý chấm điểm teamwork. Không tự suy diễn kỹ năng hoặc kinh nghiệm.

### **1.2. Prompt hoàn chỉnh**

```
[C - Context]
Bạn là chuyên viên tuyển dụng cấp cao tại công ty công nghệ, có kinh nghiệm đánh giá CV cho vị trí Junior Backend Developer.

[R - Request]
Hãy phân tích CV ứng viên, đối chiếu với mô tả công việc (JD), chấm điểm và phân loại mức độ phù hợp của từng ứng viên.

[E - Explanation]
Yêu cầu tuyển dụng (JD):
- Có kiến thức Java cơ bản.
- Biết lập trình hướng đối tượng (OOP).
- Có kiến thức SQL và PostgreSQL.
- Biết sử dụng Git.
- Ưu tiên ứng viên đã có dự án thực tế.

Quy tắc chấm điểm:
1. Kỹ năng chuyên môn: 70 điểm.
   - Java: 20 điểm.
   - OOP: 15 điểm.
   - SQL: 15 điểm.
   - PostgreSQL: 10 điểm.
   - Git: 10 điểm.

2. Kinh nghiệm/dự án: 30 điểm.
   - Đánh giá dựa trên kinh nghiệm làm việc, thực tập hoặc dự án được nêu trong CV.
   - Dự án cá nhân được tính điểm nhưng không mặc định tương đương kinh nghiệm làm việc thực tế.

3. Phân loại:
   - Từ 80 điểm: PHÙ HỢP CAO.
   - Từ 60 đến dưới 80: CẦN XEM XÉT.
   - Dưới 60: CHƯA PHÙ HỢP.

Ràng buộc:
- Không tự suy diễn kỹ năng hoặc kinh nghiệm không có trong CV.
- Nếu thiếu dữ liệu phải ghi "Chưa có thông tin".
- Không tự ý bổ sung thông tin cá nhân.
- Không tự động loại ứng viên chỉ vì thiếu một kỹ năng.
- Kết quả chỉ phục vụ sàng lọc sơ bộ, không thay thế quyết định của nhà tuyển dụng.

[A - Action]
Thực hiện lần lượt:
1. Đọc thông tin của từng ứng viên.
2. Đối chiếu từng kỹ năng với JD.
3. Chấm điểm từng tiêu chí kỹ thuật.
4. Chấm điểm kinh nghiệm/dự án.
5. Tính tổng điểm trên thang 100.
6. Phân loại theo ngưỡng điểm đã quy định.
7. Nêu điểm mạnh và thông tin còn thiếu của từng ứng viên.
8. Kiểm tra tổng điểm và tính nhất quán trước khi xuất kết quả.

Ví dụ mẫu 1:
Ứng viên: Nguyễn X
Kỹ năng: Java, OOP, SQL, PostgreSQL, Git.
Kinh nghiệm: 1 dự án Backend thực tế.

Đánh giá:
- technical: 70
- experience: 30
- totalScore: 100
- classification: PHÙ HỢP CAO
- strengths: Có đầy đủ kỹ năng theo JD và có dự án thực tế.
- missingInformation: Chưa có thông tin về kỹ năng làm việc nhóm.

Ví dụ mẫu 2:
Ứng viên: Trần Y
Kỹ năng: Java, SQL.
Kinh nghiệm: Chưa có dự án.

Đánh giá:
- technical: 35
- experience: 0
- totalScore: 35
- classification: CHƯA PHÙ HỢP
- strengths: Có kiến thức Java và SQL.
- missingInformation: Chưa có thông tin về OOP, PostgreSQL, Git và kinh nghiệm dự án.

Lưu ý: Điểm ví dụ chỉ minh họa cách trình bày, không được áp dụng mặc định cho ứng viên thực tế.

Dữ liệu CV cần đánh giá:

1. Nguyễn A
Kỹ năng: Java, OOP, SQL, Git.
Kinh nghiệm: 2 dự án cá nhân.

2. Trần B
Kỹ năng: Python, HTML, CSS.
Kinh nghiệm: Chưa có dự án.

3. Lê C
Kỹ năng: Java, OOP, PostgreSQL, Git.
Kinh nghiệm: 6 tháng thực tập.

4. Phạm D
Kỹ năng: Java, SQL.
Kinh nghiệm: 1 năm làm việc.

[T - Tone]
Sử dụng văn phong chuyên nghiệp, khách quan, chính xác và công bằng. Mọi nhận xét phải có căn cứ từ dữ liệu CV.

[E - Extras]
Chỉ xuất kết quả dưới dạng JSON hợp lệ, không sử dụng Markdown Code Fence.

Cấu trúc JSON:
{
  "candidates": [
    {
      "name": "Tên ứng viên",
      "scores": {
        "technical": 0,
        "experience": 0
      },
      "totalScore": 0,
      "classification": "NHÃN PHÂN LOẠI",
      "strengths": [],
      "missingInformation": []
    }
  ]
}

Yêu cầu bổ sung:
- Không bỏ sót ứng viên.
- Điểm technical tối đa 70.
- Điểm experience tối đa 30.
- totalScore phải bằng technical + experience.
- Chỉ sử dụng đúng 3 nhãn phân loại đã quy định.
- Không thêm trường teamwork vì đề bài không cung cấp tiêu chí chấm điểm này.
- Kiểm tra JSON hợp lệ trước khi xuất.
```

## **PHẦN 2. KẾT QUẢ ĐÁNH GIÁ ỨNG VIÊN**

### **2.1. Kết quả JSON**

Điểm được chấm theo những thông tin thực tế có trong CV. Đối với tiêu chí không có dữ liệu, không tự động xem là ứng viên không có kỹ năng; ghi nhận là chưa có thông tin và không cộng điểm.

```

{
  "candidates": [
    {
      "name": "Nguyễn A",
      "scores": {
        "technical": 60,
        "experience": 20
      },
      "totalScore": 80,
      "classification": "PHÙ HỢP CAO",
      "strengths": [
        "Có Java, OOP, SQL và Git.",
        "Có 2 dự án cá nhân."
      ],
      "missingInformation": [
        "Chưa có thông tin về PostgreSQL.",
        "Chưa có thông tin về kinh nghiệm làm việc thực tế."
      ]
    },
    {
      "name": "Trần B",
      "scores": {
        "technical": 0,
        "experience": 0
      },
      "totalScore": 0,
      "classification": "CHƯA PHÙ HỢP",
      "strengths": [
        "Có kiến thức Python, HTML và CSS."
      ],
      "missingInformation": [
        "Chưa có thông tin về Java, OOP, SQL, PostgreSQL và Git.",
        "Chưa có dự án hoặc kinh nghiệm thực tế."
      ]
    },
    {
      "name": "Lê C",
      "scores": {
        "technical": 60,
        "experience": 20
      },
      "totalScore": 80,
      "classification": "PHÙ HỢP CAO",
      "strengths": [
        "Có Java, OOP, PostgreSQL và Git.",
        "Có 6 tháng kinh nghiệm thực tập."
      ],
      "missingInformation": [
        "Chưa có thông tin về SQL.",
        "Chưa có thông tin chi tiết về dự án thực tập."
      ]
    },
    {
      "name": "Phạm D",
      "scores": {
        "technical": 35,
        "experience": 20
      },
      "totalScore": 55,
      "classification": "CHƯA PHÙ HỢP",
      "strengths": [
        "Có kiến thức Java và SQL.",
        "Có 1 năm kinh nghiệm làm việc."
      ],
      "missingInformation": [
        "Chưa có thông tin về OOP, PostgreSQL và Git.",
        "Chưa có thông tin về vị trí và nội dung công việc đã thực hiện."
      ]
    }
  ]
}

```

Lưu ý: Điểm kinh nghiệm và điểm kỹ thuật trên là mức đánh giá minh họa theo dữ liệu giới hạn của đề bài. Khi triển khai thực tế cần có thang điểm chi tiết hơn để tránh đánh giá thiếu nhất quán.

## **PHẦN 3. KIỂM TRA VÀ ĐÁNH GIÁ KẾT QUẢ**

### **3.1. Bảng tổng hợp kết quả**

| Ứng viên | Technical | Experience | Tổng điểm | Phân loại    |
| -------- | --------- | ---------- | --------- | ------------ |
| Nguyễn A | 60        | 20         | 80        | PHÙ HỢP CAO  |
| Trần B   | 0         | 0          | 0         | CHƯA PHÙ HỢP |
| Lê C     | 60        | 20         | 80        | PHÙ HỢP CAO  |
| Phạm D   | 35        | 20         | 55        | CHƯA PHÙ HỢP |


Việc sử dụng ví dụ mẫu và các ràng buộc giúp kết quả có tính nhất quán, hạn chế suy diễn thông tin. Tuy nhiên, kết quả chỉ mang tính sàng lọc sơ bộ, nhà tuyển dụng vẫn cần kiểm tra CV và phỏng vấn trực tiếp trước khi đưa ra quyết định tuyển dụng.
