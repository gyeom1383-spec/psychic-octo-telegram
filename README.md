# 주장하는 글쓰기 연습 ⑥ 피드백 앱

학생이 5자리 학번으로 로그인해 한 문단(주장·이유·근거·마무리)과 예상 반론·재반박을 쓰면 Gemini가 피드백을 주고, 글과 피드백이 구글 스프레드시트에 저장됩니다. 교사는 비밀번호로 로그인해 저장된 기록을 확인합니다.

## 파일 구성

| 파일 | 역할 | GitHub 업로드 |
|---|---|---|
| `app.py` | 앱 본체 | O |
| `requirements.txt` | 필요한 패키지 목록 | O |
| `README.md` | 이 안내 문서 | O |
| `secrets_예시.toml` | Secrets 입력 형식 예시 | **X (올리지 않음)** |

## Secrets에 넣을 값

| 이름 | 내용 |
|---|---|
| `GEMINI_API_KEY` | Google AI Studio에서 발급한 키 |
| `TEACHER_PASSWORD` | 교사 로그인 비밀번호 |
| `SHEET_URL` | 기록을 저장할 구글 시트 주소 |
| `GCP_JSON` | 서비스 계정 JSON 키 파일 내용 전체 |
| `GEMINI_MODEL` (선택) | 사용할 모델 이름을 직접 정할 때 |

## 구글 시트

- 시트를 서비스 계정 이메일(`...@....iam.gserviceaccount.com`)에 **편집자**로 공유해야 저장됩니다.
- 앱이 처음 저장할 때 `기록` 탭을 만들고 첫 줄에 제목을 씁니다.
- 열: 제출 시각, 학번, 과제, 사용 자료, 학생 글, 점검 결과, 잘한 점, 고쳐 볼 점, 다음 단계

## 고치고 싶을 때

- 연습 주제, 자료 → `TOPIC`, `MATERIALS`
- 점검 항목, 피드백 말투 → `COMMON_RULES`, `PARAGRAPH_TASK`, `REBUTTAL_TASK`
- 글자 수 제한, 재요청 대기 시간 → `MAX_CHARS`, `COOLDOWN_SEC`

GitHub에서 파일을 고쳐 Commit하면 Streamlit 앱에 자동으로 반영됩니다.
