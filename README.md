# MMU TALK

목포해양대학교 학사 안내 챗봇입니다. 계절학기·성적·수강신청·수업·시험 안내 문서를 벡터 검색해 Gemini로 답변합니다.

<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white">
<img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white">
<img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white">
<img src="https://img.shields.io/badge/FAISS-0467DF?style=flat-square&logo=meta&logoColor=white">
<img src="https://img.shields.io/badge/Gemini%20API-8E75B2?style=flat-square&logo=googlegemini&logoColor=white">

## 프로젝트 개요

| 항목 | 내용 |
|---|---|
| 개발 기간 | 2024.10 ~ 2024.11 |
| 인원 | 4명 |
| 담당 (정의찬) | Gemini 프롬프트 설계 — 이전 질문에서 찾은 담당부서 정보를 세션에 유지해 "연락처는?" 같은 후속 질문에도 답하도록 하고, 검색 문서 기반 답변·담당부서·URL 출력 규칙을 프롬프트에 고정해 답변 형식을 일관되게 유지 (`mmu_talk.py` `process_question`, `get_enhanced_rag_chain`) |
| 수상 | 2024.11 교내 공학작품 경진대회 장려상 |
| 원본 저장소 | [Baekbanjang/mmu_talk](https://github.com/Baekbanjang/mmu_talk) |

## 구조

```
data/                      — 학사 안내 원문 (계절학기, 성적, 수강신청, 수업, 시험)
faiss_index/               — 문서 임베딩 인덱스 (embedding-001)
modules/
  mmu_config.py            — 모델·검색 설정
  mmu_vector_store.py      — FAISS 벡터 저장소 생성·검색
  mmu_response_generator.py — 검색 문서 + 질문으로 Gemini 답변 생성
  mmu_response_formatter.py — 답변 포맷 정리
mmu_talk_app.py            — Streamlit 채팅 화면
```

## 로컬 실행

```bash
pip install streamlit langchain langchain-google-genai faiss-cpu python-dotenv google-generativeai
echo GOOGLE_API_KEY=your-key > .env
streamlit run mmu_talk_app.py
```
