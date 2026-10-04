# Reflection

Anti-pattern tôi dễ gặp nhất là coi object storage như một thư mục dump file vô hạn, chỉ append dữ liệu thô rồi để downstream tự đoán schema, lineage và quyền sử dụng. Với log/trace từ LLM hoặc hệ thống RAG, dữ liệu thay đổi liên tục: prompt, output, embeddings, provenance và delete events có vòng đời khác nhau. Nếu không ghi schema, version, partition và provenance ngay từ ingest, việc debug model, tái lập training set hoặc xử lý yêu cầu xóa dữ liệu sẽ thành truy vết thủ công rất rủi ro.

Cách phòng tránh là thiết kế lakehouse theo medallion: Bronze giữ dữ liệu gốc, Silver chuẩn hóa và dedup, Gold phục vụ metric cụ thể. Với dữ liệu AI, tôi sẽ lưu version bảng, provenance bucket, metadata về generator/license, và đồng bộ delete events bằng CDF thay vì chỉ upsert vào external index. Tôi dùng AI để đọc yêu cầu, lập kế hoạch chạy lab, hỗ trợ kiểm tra lỗi môi trường và chuẩn bị hồ sơ nộp; mọi output trong notebook được chạy cục bộ trong repo này.
