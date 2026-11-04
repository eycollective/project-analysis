# project-analysis

시작 단계나 개발 중인 프로젝트(또는 아이디어)의 **사업성을 검증하고 더 돈이 되는 방향을 찾는** Claude Code 스킬입니다. 본문은 「시작·개발 단계 프로젝트 사업성 검증 및 방향 재설계 프롬프트 (v2)」입니다.

Claude가 하는 일은 다음과 같습니다.

1. 현재 폴더의 코드와 문서를 읽고 이미 있는 자산을 정리합니다.
2. 고객 불만, 이미 돈이 오가는 흔적, 경쟁·대안, 법·규제를 웹에서 조사합니다.
3. 방향 후보를 6~10개 만든 뒤 좁혀서 숫자로 비교합니다.
4. 반대 검토를 거쳐 보고서를 씁니다.

보고서는 비개발자도 읽기 쉬운 한국어로, 프로젝트 폴더의 `docs/project-analysis-YYYY-MM-DD.md`에 저장됩니다. 분석하는 동안 프로젝트 코드는 고치지 않습니다.

## 한 번만 쓰기 (설치 없이, 가장 간단)

분석할 프로젝트 폴더에서 Claude Code를 열고 아래 문장을 그대로 보내면 됩니다. 아무것도 설치하지 않고, 그때그때 최신 원문을 받아 분석만 합니다.

```
https://raw.githubusercontent.com/eycollective/project-analysis/main/SKILL.md 의 원문을 설치하지 말고 curl로 그대로 받아 읽은 뒤, 그 지시를 그대로 따라 이 폴더의 프로젝트를 분석해 줘.
```

창업자 개인 정보는 묻지 않고 **프로젝트 자체를** 분석합니다. 모든 프로젝트에 다음 기본 조건을 똑같이 적용합니다.

- 프로젝트 하나에 주 20~40시간
- 예산은 극초반 월 10~100만 원에서 시작해, 수익이 나는 만큼 월 수백만~수천만 원까지 늘릴 수 있음
- 기본 목표: 6개월 안에 월 운영이익 100만 원
- 본업은 유지(전업이 필요한 방향은 감점)

팀 규모는 "1~2명의 소규모 팀"으로 가정합니다. 기본 조건을 바꾸려면 `SKILL.md`의 "분석 범위" 문단을 고칩니다.

## 설치해서 쓰기 (자주 쓸 때)

설치해 두면 `/project-analysis`나 "프로젝트 분석해줘" 같은 말로 바로 시작할 수 있습니다. 아래 명령 하나로 설치와 업데이트를 모두 합니다. 스킬 폴더가 없으면 새로 설치하고, 있으면 최신 내용을 받습니다. 몇 번을 실행해도 안전합니다.

PowerShell:

```powershell
if (Test-Path "$HOME\.claude\skills\project-analysis") { git -C "$HOME\.claude\skills\project-analysis" pull } else { git clone https://github.com/eycollective/project-analysis "$HOME\.claude\skills\project-analysis" }
```

Git Bash:

```bash
if [ -d ~/.claude/skills/project-analysis ]; then git -C ~/.claude/skills/project-analysis pull; else git clone https://github.com/eycollective/project-analysis ~/.claude/skills/project-analysis; fi
```

설치한 뒤에는 Claude Code 세션을 새로 열어야 명령 목록에 `/project-analysis`가 나타납니다.

## 사용

이미 설치된 PC에서는 프로젝트 폴더에서 다음 중 하나로 시작합니다.

- `/project-analysis` (뒤에 목표 매출, 예산, 주당 가용 시간 같은 정보를 덧붙여도 됩니다)
- "프로젝트 분석해줘", "이거 돈 될까", "사업성 검토해줘", "방향 다시 잡아줘"처럼 말로 요청

모르는 정보는 비워 두어도 됩니다. Claude가 가정을 세우고 분석을 이어 가며, 결론을 바꿀 만한 질문만 보고서 끝에 최대 5개로 모아 줍니다.

## 참고

- 웹 조사와 여러 서브에이전트를 쓰기 때문에 시간과 사용량이 꽤 듭니다.
- 같은 폴더에 이전 보고서(`docs/project-analysis-*.md`)가 있으면 먼저 읽고, 무엇이 바뀌었는지 따로 적습니다.
- 법률·세무·상장 관련 내용은 위험 지도일 뿐, 전문가 자문을 대신하지 않습니다.
