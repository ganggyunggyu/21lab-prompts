# 21lab-prompts

LLM 기반 콘텐츠 생성을 위한 프롬프트 템플릿 저장소.

다양한 카테고리별 프롬프트와 LLM 제공업체별 시스템 프롬프트를 관리합니다.

---

## 프로젝트 구조

```
21lab-prompts/
├── category/           # 카테고리별 프롬프트 템플릿
├── llm/                # LLM 관련 시스템 프롬프트
├── system/             # LLM 제공업체별 프롬프트
│   ├── gemini/
│   ├── gpt/
│   ├── claude/
│   ├── grok/
│   ├── deepseek/
│   └── common/
├── service/            # 서비스 템플릿
├── rules/              # 작성 규칙
└── private/            # 개인 프롬프트
```

---

## 기술 스택

| 구분 | 기술 |
|------|------|
| 템플릿 엔진 | Jinja2 (.j2) |
| 버전 관리 | Git |

---

## 디렉토리 설명

### category/

주제별 콘텐츠 생성 프롬프트. 건강, 뷰티, 음식, 서비스 등 다양한 카테고리 포함.

- 건강: 마운자로, 무지외반증, 족저근막염, 영양제 등
- 뷰티: 미용학원, 리쥬란, 울쎄라, 리들샷 등
- 음식: 맛집, 김장, 서브웨이다이어트 등
- 생활: 인테리어, 정기청소, 캐리어, 커피머신 등
- 리뷰: 영화리뷰, 노래리뷰, 애니메이션 등
- 기타: 웨딩, 호텔, 외국어교육 등

### llm/

LLM 활용 목적별 시스템 프롬프트.

- `clean_system.j2` - 정보 추출용
- `review_system.j2` - 리뷰 작성용
- `news_system.j2` - 뉴스 콘텐츠용
- `story_analysis_system.j2` - 스토리 분석용
- `synonym_system.j2` - 유의어 처리용
- `translation_compare_system.j2` - 번역 비교용
- `deep_search_system.j2` - 심층 검색용

### system/

LLM 제공업체별 시스템/유저 프롬프트.

- **gemini/** - Google Gemini용
- **gpt/** - OpenAI GPT용
- **claude/** - Anthropic Claude용
- **grok/** - xAI Grok용
- **deepseek/** - DeepSeek용
- **common/** - 공통 템플릿

### rules/

콘텐츠 작성 규칙 정의.

- `write_rule.txt` - 기본 작성 규칙
- `output_rule.txt` - 출력 형식 규칙
- `line_break_rules.txt` - 줄바꿈 규칙
- `human_writing_style.txt` - 인간 문체 규칙
- `taboo_rules.txt` - 금지 표현 규칙
- `emphasis_rules.txt` - 강조 규칙
- `length_rule.txt` - 길이 규칙

### service/

서비스 로직 관련 템플릿.

- `get_category_tone_rules.j2` - 카테고리별 톤 규칙 조회
- `get_mongo_prompt.j2` - MongoDB 프롬프트 조회
- `template_*.j2` - 템플릿 버전별 파일
- `human_writing_style.j2` - 인간 문체 스타일
- `anti_ai_writing_patterns.j2` - AI 문체 방지 패턴

---

## 템플릿 사용법

Jinja2 템플릿 문법을 사용합니다.

### 변수 치환

```jinja2
{{mongo_data}}
{{category_tone_rules}}
{{output_structure}}
```

### 활용 예시

```python
from jinja2 import Environment, FileSystemLoader

env = Environment(loader=FileSystemLoader('system/gemini'))
template = env.get_template('system.j2')

result = template.render(
    mongo_data=mongo_data,
    category_tone_rules=tone_rules,
    output_structure=output_format
)
```

---

## 파일 명명 규칙

| 접미사 | 용도 |
|--------|------|
| `_system.j2` | 시스템 프롬프트 |
| `_user.j2` | 유저 프롬프트 |
| `.txt` | 규칙/가이드 문서 |

---

## 라이선스

Private Repository
