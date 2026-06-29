# Korean-Bible-1961-KRV-Hanja (1961년 국한문 개역한글 성경)

[![Language](https://img.shields.io/badge/Language-Korean%20%2F%20Hanja-blue.svg)](https://en.wikipedia.org/wiki/Bible_translations_into_Korean)
[![License](https://img.shields.io/badge/License-KRV_Use_Permitted-green.svg)](https://www.bskorea.or.kr/bbs/board.php?bo_table=copyright_faq&wr_id=5)
[![Validation](https://img.shields.io/badge/Validation-Documented-brightgreen.svg)](docs/validation_report.md)
[![Status](https://img.shields.io/badge/Status-Release_Candidate-success.svg)](docs/cross_verification_report.md)

본 저장소는 **1961년 개역한글 성경**을 기준으로 국한문 혼용 본문과
한자 병기 표기를 정리한 **국한문 개역한글 성경 JSON 데이터셋**입니다.

이 데이터셋은 흩어지기 쉬운 국한문 성경 자료를 구조화된 형태로
보존하고, 개역한글 1961 국문 기준과의 대조 이력을 투명하게 남기기
위해 제작되었습니다.

---

## 데이터 개요 (Overview)

본 데이터셋은 국한문 성경의 특성을 보존하면서도 현대 개발 환경에서
활용할 수 있도록 두 가지 텍스트 형태를 함께 제공합니다.

- `text`: 한자 병기와 국한문 혼용 표기가 포함된 본문
- `hangulText`: 개역한글 1961 국문 기준 대조를 위해 한자를 한글로
  환원한 본문

2026년 6월 기준, **대한성서공회 개역한글 1961 국문 기준**과의 구조 및
국문 환원 대조를 수행하여 발견된 **7,762건의 차이점**을 분류 및
분석했습니다. 또한 **위키문헌 개역간이국한문한글판**을 공개 참고
자료로 사용하여 검수 후보 93건을 대조했습니다.

이후 승인된 보정과 공개 표기 정책을 반영하여 다음 검수 결과를
정리했습니다.

- 기본 본문 보정: 22건 승인 및 적용
- 추가 단어/절 보정: 12건 승인 및 적용
- 공개 표기 정책 결정: 66건 승인
- 공개 준비 관문 및 일관성 검증: `17/17 pass`

세부 검수 계보와 보정 근거는
[교차검증 상세 리포트](docs/cross_verification_report.md)를 참고하십시오.

---

## 주요 특징 (Key Features)

- **검증된 구조 정합성**: 공개 후보본 기준 66권, 1,189장, 31,101절
  구조를 검증했습니다.
- **국한문 표기 보존**: 한자 병기와 국한문 혼용 표기를 UTF-8 JSON
  데이터로 보존했습니다.
- **이중 텍스트 제공**: 국한문 본문(`text`)과 한글 환원문
  (`hangulText`)을 함께 제공하여 검색, 대조 뷰어, 한자 학습 도구 등에
  활용할 수 있습니다.
- **검수 이력 추적**: 주요 보정과 표기 정책을 `docs/` 문서로 남겨
  데이터가 어떤 기준으로 정리되었는지 확인할 수 있습니다.

---

## 검증 기준과 참고 자료

이 저장소의 검수 기준과 참고 자료는 다음과 같습니다.

1. **대한성서공회 개역한글판 1961**
   - 국문 본문 기준 확인에 사용했습니다.
   - 역본 정보:
     <https://www.bskorea.or.kr/prog/trans_feature2.php>
   - 성경읽기:
     <https://www.bskorea.or.kr/bible/korbibReadpage.php>

2. **위키문헌 개역간이국한문한글판**
   - 국한문/한자 병기 문구와 일부 표기 후보를 대조하기 위한 공개 참고
     자료로 사용했습니다.
   - <https://ko.wikisource.org/wiki/개역간이국한문한글판>

대한성서공회 자료는 국문 개역한글 기준 확인에 사용했으며, 위키문헌
자료는 국한문 대조 참고 자료로 사용했습니다. 위키문헌 자료를 공식
국한문 정본으로 단정하지 않습니다.

---

## 파일 구조 (File Structure)

본 저장소는 성경 보존을 위한 핵심 데이터와 검증 문서로 구성되어
있습니다.

```text
.
├── README.md
├── bible_1961_krv_hanja.json   # 성경 전체 통합 JSON 데이터
├── data/                       # 권별 개별 JSON 데이터 (66개 파일)
│   ├── Genesis.json
│   ├── Exodus.json
│   └── ...
├── search_index.json           # 검색 엔진 및 인덱스용 절 단위 매핑 데이터
├── checksums.sha256            # 공개 파일 체크섬
└── docs/                       # 공개 검수 문서
    ├── validation_report.md
    ├── source_notes.md
    ├── cross_verification_report.md
    ├── normalization_rules.md
    └── preservation_notes.md
```

---

## 데이터 형식 (Data Format)

`bible_1961_krv_hanja.json` 및 `data/*.json` 파일은 다음과 같은 구조로
작성되어 있습니다.

```json
{
  "book": "Genesis",
  "koreanTitle": "창세기",
  "hanjaTitle": "創世記",
  "chapters": [
    {
      "chapter": 1,
      "verses": [
        {
          "verse": 1,
          "text": "태초(太初)에 하나님이 천지(天地)를 창조(創造)하시니라",
          "hangulText": "태초에 하나님이 천지를 창조하시니라"
        }
      ]
    }
  ]
}
```

---

## 성경 통계 요약 (Bible Statistics Summary)

| 구분 | 권 수 (Books) | 장 수 (Chapters) | 절 수 (Verses) |
| --- | :---: | :---: | :---: |
| 구약 (Old Testament) | 39 | 929 | 23,144 |
| 신약 (New Testament) | 27 | 260 | 7,957 |
| **전체 (Total)** | **66** | **1,189** | **31,101** |

---

## 저작권 및 이용 안내 (Copyright & License)

대한성서공회는 『성경전서 개역한글판』의 저작재산권 보호기간이 만료되어
저작권료 지급 없이 사용할 수 있다고 안내하고 있습니다.

- 대한성서공회 저작권 FAQ:
  <https://www.bskorea.or.kr/bbs/board.php?bo_table=copyright_faq&wr_id=5>

사용 시에는 대한성서공회가 안내하는 성명표시권과 동일성유지권을 함께
존중해야 합니다. 본 저장소의 국한문 데이터는 개역한글 1961 국문 기준과
공개 국한문 참고 자료를 대조하여 정리한 보존용 데이터셋입니다.

---

## 기여 및 문의 (Contribution)

이 데이터셋은 디지털 환경에서의 국한문 성경 보존과 활용을 목적으로
구축되었습니다. 데이터 파싱 오류, 오타, 표기상 검토가 필요한 항목을
발견하신 경우 이슈 등록을 통해 제보해 주십시오.

- 최종 검증일: 2026년 6월 29일
- 검수 협력: SoftPinkCat, AI 도구 보조 검수
