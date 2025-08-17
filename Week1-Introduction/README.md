# Module 1: Introduction to LLMs and RAG - Cornell Notes

---

## Ghi chú chính (Notes)

### 1. Tổng quan về LLM và RAG
- **LLM (Large Language Models)**: Mô hình ngôn ngữ lớn có khả năng hiểu và sinh văn bản
- **RAG (Retrieval-Augmented Generation)**: Kỹ thuật kết hợp tìm kiếm thông tin với sinh văn bản
- Kiến trúc RAG: Retrieval → Context → Generation

### 2. Thiết lập môi trường
- Cài đặt Python libraries: `requests`, `elasticsearch`, `openai`
- ElasticSearch 8.17.6 cho text search
- OpenAI API cho language model
- Docker để chạy các services

### 3. Xây dựng hệ thống Q&A
- **Data preparation**: Load FAQ documents từ JSON
- **Indexing**: Sử dụng ElasticSearch để index documents
  ```python
  # Mapping settings
  "course": {"type": "keyword"}  # Exact match
  "text": {"type": "text"}       # Full-text search
  "question": {"type": "text"}
  ```

### 4. Search Implementation
- **Query types**: `multi_match` với `best_fields`
- **Boosting**: Tăng trọng số cho field `question` (boost = 4)
- **Filtering**: Lọc theo course cụ thể
- **Scoring**: ElasticSearch `_score` để ranking kết quả

### 5. Prompt Engineering
- **Context template**:
  ```
  Q: {question}
  A: {text}
  ```
- **Prompt template**: Structured instruction cho LLM
- **Token counting**: Quan trọng cho cost management

---

## Từ khóa quan trọng (Cue Column)

**RAG Pipeline**
- Retrieval
- Context building  
- Generation

**ElasticSearch**
- Indexing function: `index()`
- Multi-match query
- Best fields type
- Score ranking

**OpenAI API**
- Rate limits (429 error)
- Quota management
- Cost optimization
- API key setup

**Search Strategies**
- Text search
- Semantic search
- Hybrid approach
- Filtering & boosting

**Evaluation Metrics**
- Search relevance
- Response quality
- Token usage
- Response time

---

## Tóm tắt (Summary)

Module 1 giới thiệu nền tảng để xây dựng hệ thống RAG cơ bản:

1. **Mục tiêu**: Tạo AI assistant có thể trả lời câu hỏi từ knowledge base
2. **Tech Stack**: ElasticSearch + OpenAI API + Python
3. **Core Components**: 
   - Document preprocessing và indexing
   - Search query optimization
   - Prompt engineering cho LLM
4. **Key Skills**: 
   - Setup và config ElasticSearch
   - Thiết kế search queries hiệu quả
   - Xử lý API errors và rate limits
   - Đo đạc performance metrics

**Next Steps**: Vector search và semantic embeddings (Module 2)

---

## Câu hỏi cần làm rõ (Questions for Review)

1. Làm thế nào để optimize search relevance?
2. Khi nào dùng text search vs semantic search?
3. Cách handle OpenAI rate limits trong production?
4. Best practices cho prompt design?
5. Metrics nào quan trọng nhất để evaluate RAG system?

---

## Bài tập thực hành (Homework Notes)

- **Q1**: ElasticSearch cluster info - `version.build_hash`
- **Q2**: Indexing function - `index()`  
- **Q3**: Search với boost=4 cho question field
- **Q4**: Filtering theo course, return top 3
- **Q5**: Prompt construction và length calculation
- **Q6**: Token counting với tiktoken

**Solution**: [homework_solution.ipynb](https://github.com/DataTalksClub/llm-zoomcamp/blob/main/cohorts/2025/01-intro/homework_solution.ipynb)
