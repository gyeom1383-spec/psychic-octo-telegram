# 주장하는 글쓰기 연습 ⑥ 피드백 앱

학생이 쓴 한 문단(주장·이유·근거·마무리)과 예상 반론·재반박에 Gemini가 피드백을 주는 Streamlit 앱입니다.

## 파일 구성

| 파일 | 역할 |
|---|---|
| `app.py` | 앱 본체 (화면, 자료, AI 지시문, 피드백 표시) |
| `requirements.txt` | 앱에 필요한 파이썬 패키지 목록 |
| `README.md` | 이 안내 문서 |

## 배포 순서 요약

1. Google AI Studio에서 Gemini API 키 발급
2. GitHub에 새 저장소를 만들고 파일 3개 업로드
3. Streamlit Community Cloud에서 저장소 연결 → Secrets에 API 키 입력 → Deploy
4. 직접 테스트한 뒤 학생들에게 주소 공유

## Secrets 입력 형식 (Streamlit Cloud → App settings → Secrets)

```toml
GEMINI_API_KEY = "발급받은_API_키"
# 모델을 바꾸고 싶을 때만 아래 줄의 # 을 지우고 모델 이름을 적습니다.
# GEMINI_MODEL = "gemini-3.6-flash"
```

API 키는 절대 GitHub 파일에 직접 적지 마세요.

## 고치고 싶을 때

- 연습 주제, 자료 → `app.py`의 `TOPIC`, `MATERIALS`
- 점검 항목, 피드백 말투 → `COMMON_RULES`, `PARAGRAPH_TASK`, `REBUTTAL_TASK`
- 글자 수 제한, 재요청 대기 시간 → `MAX_CHARS`, `COOLDOWN_SEC`

GitHub에서 파일을 고쳐 저장(Commit)하면 Streamlit 앱에 자동으로 반영됩니다.
