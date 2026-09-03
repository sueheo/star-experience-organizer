# ⭐ star-experience-organizer

**두서없이 늘어놓는 취업 경험 이야기를, 자소서·면접에 바로 쓸 수 있는 STAR 항목으로.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-6b5bd6)](https://claude.com/claude-code)
[![Made for](https://img.shields.io/badge/Made%20for-취업준비생-orange)](#)

[Claude Code](https://claude.com/claude-code)에서 동작하는 skill입니다. 경험을 정리해달라고
자유롭게 말하면, 이야기 속 정량화 가능한 수치를 뽑아내고, 애매한 부분은 되물어서
구체화하고, 완성된 경험을 STAR 형식으로 누적 저장해줍니다.

---
## 왜 필요한가요?

자소서를 쓸 때 대부분의 경험은 이렇게 시작합니다.

> "팀플했는데 열심히 해서 결과가 잘 나왔어요."

이 문장만으로는 아무 역량도 증명되지 않습니다. 채용 담당자가 궁금한 건
**무슨 상황에서, 정확히 뭘 했고, 얼마나 나아졌는지**입니다. 하지만 막상
그걸 스스로 되짚어 숫자로 표현하는 건 생각보다 어렵습니다. 이 skill은
그 되짚는 과정을 대신 진행해줍니다.

## 무엇을 하는가

- 📝 **자유 서술 인식** — 형식 없이 편하게 이야기해도 됨
- 🔢 **정량 정보 자동 추출** — 이미 말한 숫자(기간, 인원, %, 금액 등)를 놓치지 않고 뽑아냄
- ❓ **정확한 지점만 되묻기** — Result가 애매하면 최우선으로, 그다음 Action 순으로, 한 번에 1~2개씩만 질문
- 🧭 **맥락 유도** — 상황(S)·역할(T) 자체를 못 잡을 땐 정량화보다 먼저 배경부터 정리하도록 도움
- 🏷️ **역량 자동 태깅** — 완성된 경험에 리더십/문제해결/협업 등 역량 키워드 부여
- 🗂️ **경험 뱅크 누적** — `experiences.md`에 계속 쌓아서, 자소서 문항이나 면접 질문에 맞는 경험을 나중에 검색·재사용

> 정보를 지어내지 않습니다. 말하지 않은 숫자는 절대 임의로 채우지 않고, 없으면 없다고 그대로 기록합니다.

## 예시

<table>
<tr><th>Before (사용자의 날것 이야기)</th><th>After (정리된 STAR 항목)</th></tr>
<tr valign="top">
<td>

"학교 마케팅 동아리에서 SNS 운영을 맡았는데, 콘텐츠를 꾸준히 올렸더니 팔로워가 꽤 늘었어요."

</td>
<td>

**S** 마케팅 동아리(8명) SNS 운영 담당, 팔로워 정체 상태에서 시작<br>
**T** 3개월간 인스타그램 콘텐츠 기획·발행 전담<br>
**A** 주 3회 카드뉴스 정기 발행, 반응 좋은 게시물 유형 분석 후 포맷 표준화<br>
**R** 팔로워 320명 → 890명 (178% 증가), 게시물 평균 도달 3배 증가<br>
🏷️ `#콘텐츠기획` `#데이터기반의사결정` `#실행력`

</td>
</tr>
</table>

이 정도로 구체화되기까지, 스킬이 "팔로워가 몇 명에서 몇 명으로 늘었나요?", "꾸준히 올렸다는 게 주에 몇 번인가요?" 같은 질문 1~2개를 순서대로 던져서 답을 유도합니다.

## 설치

**프로젝트 전용으로 쓰기** (해당 프로젝트에서만 인식):

```bash
git clone https://github.com/sueheo/star-experience-organizer.git
mkdir -p .claude/skills
cp -r star-experience-organizer/.claude/skills/star-experience-organizer .claude/skills/
```

**모든 프로젝트에서 쓰기** (전역 설치):

```bash
git clone https://github.com/sueheo/star-experience-organizer.git
cp -r star-experience-organizer/.claude/skills/star-experience-organizer ~/.claude/skills/
```

## 사용법

Claude Code에서 아래처럼 말을 걸면 스킬이 자동으로 인식됩니다.

```
/star-experience-organizer

또는 그냥:
"이 경험 STAR로 정리해줘 — [경험 이야기 붙여넣기]"
```

정리된 경험은 작업 중인 디렉터리의 `experiences.md`에 계속 쌓입니다.
이후 "이 자소서 문항에 맞는 경험 찾아줘"처럼 요청하면 쌓인 경험 중에서 태그·키워드로 매칭해줍니다.

## 작동 방식

1. **날것의 이야기 받기** — 형식 요구 없이 자유롭게
2. **S/T/A/R 초안 분류 + 이미 있는 수치 추출**
3. **맥락 공백 확인** — 상황/역할이 안 잡히면 배경 질문부터
4. **정량화 공백 확인** — Result 우선, 그다음 Action. 한 번에 1~2개만 되묻기
5. **역량 태깅 확인**
6. **`experiences.md`에 저장**

## 구성 파일

| 파일 | 역할 |
|---|---|
| `SKILL.md` | 전체 워크플로우 정의 |
| `references/quantification-questions.md` | 모호 표현 체크리스트 + 상황별(팀플/영업/개발/CS/리더십) 정량화 질문 패턴 |
| `assets/star_entry_template.md` | 경험 뱅크 저장용 항목 템플릿 |

> `experiences.md`(실제로 정리한 개인 경험 데이터)는 `.gitignore`에 포함되어 저장소에 올라가지 않습니다.

## 라이선스

[MIT](LICENSE)
