# 🎨 Designer — 초반 애니메이션에서 메인 화면으로 전환될 때 적용할 자연스러운 트랜지션 효과(예: 슬라이드, 페이드 인/아웃, 패럴랙스)의 시각적 가이드라인(Easing, 속도, 전환 유형)을 정의하고 디자인 브리프를 작성해줘.

🎨 Designer: 작업 시작합니다.

먼저 요청하신 웹사이트 주소 `http://localhost:3000/#marketplace`를 디자인 시스템 지식 메모리에 영구 저장했습니다. 향후 디자인 및 기능 구현 시 이 URL을 기준으로 프로젝트 맥락을 유지하겠습니다.

요청하신 "초반 애니메이션이 꺼지는 것이 아니라, 스크롤/클릭 시 현재 화면으로 자연스럽게 변환되는" 트랜지션 효과에 대한 시각적 가이드라인과 디자인 브리프를 아래와 같이 정의합니다. 이는 단순한 `fade-out`이 아닌, **'Transformation Reveal'** 메커니즘을 통해 구현되어야 합니다.

---

### 📄 디자인 브리프: Intro-to-Main Transition (Transformation Reveal)

**목표:** 초기 로딩 애니메이션(Intro State)이 갑자기 사라지는 것이 아니라, 메인 콘텐츠 영역(Main State)으로 자연스럽게 **변형(Morph)**되며 시퀀스를 이어가는 듯한 사용자 경험을 제공합니다.
**적용 범위:** 초기 로딩 뷰에서 메인 페이지(`/`)로 진입하는 시퀀스.

#### 1. 기술적 가이드라인 (Visual System)

| 요소 | 상세 가이드라인 | 기술적 정의 | 목적 |
| :--- | :--- | :--- | :--- |
| **전환 유형** | **Scale & Fade Morph (확대 및 페이드 변형)** | `transform: scale(X)` + `opacity: Y` | 애니메이션 요소를 메인 콘텐츠의 일부로 흡수시키거나, 메인 콘텐츠가 애니메이션 영역을 덮으며 등장하는 느낌을 부여합니다. |
| **Easing (가속도)** | **Outward Deceleration** | `cubic-bezier(0.25, 1, 0.5, 1)` (Ease-Out) | 전환 시작은 빠르게, 끝날 때는 부드럽게 감속하여 사용자에게 '완성'의 느낌과 세련됨을 전달합니다. (급격함 방지) |
| **속도 (Duration)** | **Moderate Flow** | `600ms` ~ `800ms` | 너무 빠르면 뚝 끊기는 느낌이, 너무 느리면 지루한 느낌이 듭니다. 0.6초~0.8초 사이에서 콘텐츠 복잡도에 따라 미세 조정이 필요합니다. |
| **트리거** | **Scroll/CTA Trigger** | `Intersection Observer` 또는 `onClick` | 사용자의 능동적 행동(스크롤, 클릭)을 감지하여 전환을 시작합니다. |

#### 2. 상태별 시각적 정의 (State Definition)

| 상태 | 초기 (Intro State) | 전환 중 (Transition) | 최종 (Main State) |
| :--- | :--- | :--- | :--- |
| **애니메이션 영역** | `opacity: 1`, `transform: scale(0.9)` (약간 작게 시작) | `opacity: 0` (점차 사라짐), `transform: scale(1.0)` (확대됨) | `display: none` (메인 콘텐츠로 대체) |
| **메인 콘텐츠 영역** | `opacity: 0`, `transform: scale(1.0)` (정지 상태) | `opacity: 1` (점차 나타남), `transform: scale(1.0)` (완전 크기로 확장) | `opacity: 1`, `transform: scale(1.0)` (정지 상태) |

#### 3. 구현 가이드 (Developer Directive)

이 트랜지션을 구현하기 위해, 개발팀은 CSS 애니메이션과 JavaScript 이벤트 리스너를 결합해야 합니다.

1.  **HTML 구조:** 초기 애니메이션 뷰와 메인 뷰를 오버레이(Overlay) 방식으로 배치합니다.
2.  **CSS:** 두 뷰에 정의된 `Transition` 속성을 적용하고, `scale`과 `opacity`를 변경하는 클래스를 정의합니다.
3.  **JS Logic:**
    *   사용자가 최초 스
