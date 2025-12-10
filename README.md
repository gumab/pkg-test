# 접근성 lint rule 가이드

## <span style="color: red;">[ERROR]</span> [alt-text](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/alt-text.html)

> img 태그 등에 alt 속성이 없음

### 해결

- img 태그에 alt 속성을 입력

### 설정 사유

- 이미지에 alt 속성이 없으면 스크린 리더 사용자가 이미지 내용을 전혀 알 수 없어 매우 심각한 접근성 문제
- WCAG 2.1 레벨 A 요구사항으로 반드시 준수해야 함
- 조치 난이도 낮음

## <span style="color: red;">[ERROR]</span> [anchor-has-content](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/anchor-has-content.html)

> a 태그 내 스크린 리더가 읽을 Text Content 가 없음

### 해결

- a 태그 내 Text 형태의 content 사용
- a 태그에 aria-label 등의 속성 추가

### 설정 사유

- 링크에 접근 가능한 텍스트가 없으면 스크린 리더 사용자가 링크 목적지를 알 수 없음
- 키보드 사용자가 링크를 탐색할 때 의미 없는 링크로 인식되어 사용성 저하
- 조치 난이도 낮음

## <span style="color: red;">[ERROR]</span> [aria-props](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/aria-props.html)

> ARIA 속성이 올바르지 않거나 존재하지 않는 속성 사용

### 해결

- 올바른 ARIA 속성명 사용 (aria-label, aria-labelledby, aria-describedby 등)
- 존재하지 않는 ARIA 속성 제거

### 설정 사유

- 존재하지 않는 aria 속성 or 오타 방지

## <span style="color: red;">[ERROR]</span> [aria-role](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/aria-role.html)

> role 속성에 올바르지 않은 값 사용

### 해결

- 올바른 ARIA role 값 사용 (button, navigation, dialog, alert 등)
- 존재하지 않는 role 값 제거

### 설정 사유

- 존재하지 않는 role or 오타 방지

## <span style="color: red;">[ERROR]</span> [aria-unsupported-elements](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/aria-unsupported-elements.html)

> ARIA 속성을 지원하지 않는 요소(meta, html 등)에 ARIA 속성 사용

### 해결

- ARIA 속성을 지원하는 요소로 변경
- 또는 해당 ARIA 속성 제거

## <span style="color: orange;">[WARN]</span> [click-events-have-key-events](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/click-events-have-key-events.html)

> @click 이벤트에 키보드 이벤트 핸들러가 없음

### 해결

- @click과 함께 @keydown 또는 @keyup 이벤트 핸들러 추가
- 또는 버튼, 링크 등 네이티브 키보드 지원 요소 사용

### 설정 사유

- 기존 코드베이스에 div/span에 @click을 사용한 패턴이 많아 일괄 수정이 어려움
- 점진적으로 시맨틱 요소(button, a)로 변경하거나 키보드 이벤트를 추가하도록 권고

## <span style="color: orange;">[WARN]</span> [form-control-has-label](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/form-control-has-label.html)

> 폼 컨트롤(input, select, textarea 등)에 label이 없음

### 해결

- label 태그와 연결 (for 속성 사용)
- 또는 aria-label, aria-labelledby 속성 추가

### 설정 사유

- 기존 코드에서 플레이스홀더나 주변 텍스트로만 라벨을 표현한 경우가 많음, 디자인 요구사항과 충돌 가능성
- 시각적으로는 명확하지만 스크린 리더 사용자에게는 문제가 될 수 있어 점진적 개선 필요

## <span style="color: red;">[ERROR]</span> [heading-has-content](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/heading-has-content.html)

> h1~h6 태그에 스크린 리더가 읽을 콘텐츠가 없음

### 해결

- heading 태그 내 텍스트 콘텐츠 추가
- 또는 aria-label 속성 추가

### 설정 사유

- 제목에 내용이 없으면 스크린 리더 사용자가 문서 구조를 이해할 수 없음
- 제목 네비게이션 기능을 사용하는 사용자에게 빈 제목은 혼란을 줌
- 문서의 계층 구조를 표현하는 핵심 요소이므로 반드시 수정 필요

## <span style="color: red;">[ERROR]</span> [iframe-has-title](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/iframe-has-title.html)

> iframe 태그에 title 속성이 없음

### 해결

- iframe 태그에 title 속성 추가

### 설정 사유

- iframe에 title이 없으면 스크린 리더 사용자가 iframe의 목적이나 내용을 알 수 없음
- iframe 내부로 포커스가 이동할 때 사용자가 맥락을 잃을 수 있음
- WCAG 2.1 레벨 A 요구사항

## <span style="color: red;">[ERROR]</span> [interactive-supports-focus](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/interactive-supports-focus.html)

> 인터랙티브 요소(role="button" 등)가 포커스 가능하지 않음

### 해결

- tabindex="0" 추가하여 키보드 포커스 가능하게 설정
- 또는 네이티브 포커스 가능 요소(button, a 등) 사용

### 설정 사유

- 인터랙티브 요소가 포커스 불가능하면 키보드 사용자가 완전히 접근할 수 없어 매우 심각한 문제
- 마우스만 사용 가능한 UI는 접근성 위반으로 WCAG 2.1 레벨 A 요구사항 미준수

## <span style="color: orange;">[WARN]</span> [label-has-for](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/label-has-for.html)

> label 태그가 관련된 컨트롤과 연결되지 않음

### 해결

- label의 for 속성에 input의 id 값 연결
- 또는 input을 label 태그 내부에 중첩

### 설정 사유

- 기존 코드에서 플레이스홀더나 주변 텍스트로만 라벨을 표현한 경우가 많음, 디자인 요구사항과 충돌 가능성
- id/nesting 중 하나만 있어도 허용하도록 설정하여 점진적 개선 가능

## <span style="color: red;">[ERROR]</span> [media-has-caption](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/media-has-caption.html)

> audio, video 태그에 캡션이나 트랜스크립트가 없음

### 해결

- track 태그로 캡션 추가
- 또는 aria-label, aria-describedby로 설명 추가

### 설정 사유

- 캡션이 없으면 청각 장애인이나 소음 환경 사용자가 미디어 내용을 이해할 수 없음
- WCAG 2.1 레벨 A 요구사항으로 오디오/비디오 콘텐츠에 반드시 필요
- 현재 오류코드 없음. 적용 불가시 WARN 처리

## <span style="color: orange;">[WARN]</span> [mouse-events-have-key-events](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/mouse-events-have-key-events.html)

> 마우스 이벤트(@mouseover, @mouseout 등)에 키보드 이벤트 핸들러가 없음

### 해결

- 마우스 이벤트와 함께 키보드 이벤트 핸들러 추가
- 또는 포커스 가능한 요소 사용

### 설정 사유

- hover 효과나 툴팁 등 비핵심 상호작용에서 마우스 이벤트만 사용하는 경우가 많음
- 모든 마우스 이벤트에 키보드 이벤트를 추가하는 것이 항상 적절하지 않을 수 있음
- 핵심 기능이 아닌 경우 점진적으로 개선하도록 경고

## <span style="color: red;">[ERROR]</span> [no-access-key](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-access-key.html)

> accesskey 속성 사용 (키보드 단축키 충돌 가능)

### 해결

- accesskey 속성 제거

### 설정 사유

- accesskey는 브라우저나 보조 기술의 기본 키보드 단축키와 충돌할 수 있음
- 플랫폼마다 다른 키 조합이 필요하여 일관성 없는 사용자 경험 제공
- 현대 웹에서는 키보드 네비게이션과 ARIA 패턴으로 대체 가능

## <span style="color: red;">[ERROR]</span> [no-aria-hidden-on-focusable](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-aria-hidden-on-focusable.html)

> 포커스 가능한 요소에 aria-hidden="true" 사용

### 해결

- aria-hidden="true" 제거
- 또는 포커스 불가능한 요소로 변경

### 설정 사유

- 포커스 가능한 요소를 숨기면 키보드 사용자가 접근할 수 없어 매우 심각한 접근성 문제
- 스크린 리더 사용자도 해당 요소를 인식하지 못함
- tabindex가 있는 요소나 네이티브 포커스 가능 요소에 aria-hidden을 사용하면 안 됨

## <span style="color: orange;">[WARN]</span> [no-autofocus](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-autofocus.html)

> autofocus 속성 사용 (사용자 경험 저하)

### 해결

- autofocus 속성 제거

### 설정 사유

- autofocus는 키보드 사용자의 예상치 못한 포커스 이동을 야기할 수 있음
- 스크린 리더 사용자가 페이지 상단의 중요한 정보를 놓칠 수 있음
- 하지만 로그인 페이지의 아이디 입력 필드처럼 사용자 경험 향상에 도움이 되는 경우도 있어 경고로 설정

## <span style="color: red;">[ERROR]</span> [no-distracting-elements](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-distracting-elements.html)

> blink, marquee 태그 사용 (접근성 저하)

### 해결

- blink, marquee 태그를 다른 요소로 대체

### 설정 사유

- 깜빡이는 요소는 광과민성 발작을 유발할 수 있어 매우 위험
- 움직이는 요소는 주의력 결핍 장애나 인지 장애가 있는 사용자에게 방해가 됨
- HTML5에서 blink, marquee는 deprecated되어 사용하지 않아야 함

## <span style="color: black;">[OFF]</span> [no-onchange](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-onchange.html)

> @change 이벤트 사용 (select 요소에서 접근성 문제)

### 해결

- @change 대신 @blur 이벤트 사용

### 설정 사유

- 이 규칙은 deprecated되어 더 이상 권장되지 않음
- 현대 브라우저와 스크린 리더에서 @change 이벤트는 접근성 문제를 일으키지 않음
- Vue 3의 양방향 바인딩 패턴과도 충돌할 수 있어 비활성화

## <span style="color: red;">[ERROR]</span> [no-redundant-roles](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-redundant-roles.html)

> HTML 요소에 이미 암시된 role을 중복으로 지정

### 해결

- 중복된 role 속성 제거 (예: button 태그에 role="button" 제거)

### 설정 사유

- 중복된 role은 불필요한 코드이며 유지보수 시 혼란을 줄 수 있음
- 일부 스크린 리더에서 중복 role이 예상치 못한 동작을 일으킬 수 있음
- 코드 품질과 접근성 모두를 위해 명확하게 수정 필요

## <span style="color: red;">[ERROR]</span> [no-role-presentation-on-focusable](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-role-presentation-on-focusable.html)

> 포커스 가능한 요소에 role="presentation" 사용

### 해결

- role="presentation" 제거
- 또는 포커스 불가능한 요소로 변경

### 설정 사유

- role="presentation"은 요소를 장식용으로만 사용한다는 의미인데, 포커스 가능하면 모순
- 키보드 사용자가 포커스할 수 있지만 스크린 리더는 무시하여 매우 혼란스러운 상황
- 접근성 API에 잘못된 정보를 제공하여 보조 기술이 올바르게 동작하지 않음

## <span style="color: red;">[ERROR]</span> [no-static-element-interactions](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/no-static-element-interactions.html)

> 정적 요소(div, span 등)에 인터랙티브 이벤트 핸들러 사용

### 해결

- 버튼, 링크 등 시맨틱 요소로 변경
- 또는 role과 tabindex 추가하여 키보드 접근 가능하게 설정

### 설정 사유

- div/span에 클릭 이벤트를 사용하면 키보드 사용자가 접근할 수 없어 매우 심각한 문제
- 스크린 리더도 해당 요소를 인터랙티브 요소로 인식하지 못함
- 시맨틱 HTML을 사용하거나 적절한 ARIA 속성을 추가해야 함

## <span style="color: red;">[ERROR]</span> [role-has-required-aria-props](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/role-has-required-aria-props.html)

> ARIA role에 필요한 필수 속성이 없음

### 해결

- role에 필요한 필수 ARIA 속성 추가 (예: role="checkbox"는 aria-checked 필요)

### 설정 사유

- role만 지정하고 필수 속성이 없으면 스크린 리더가 요소의 상태를 올바르게 전달할 수 없음
- 예: role="checkbox"에 aria-checked가 없으면 체크 상태를 알 수 없음
- 접근성 API 스펙에 따라 각 role은 특정 필수 속성을 요구함

## <span style="color: orange;">[WARN]</span> [tabindex-no-positive](https://vue-a11y.github.io/eslint-plugin-vuejs-accessibility/rules/tabindex-no-positive.html)

> tabindex에 양수 값 사용 (키보드 탐색 순서 혼란)

### 해결

- tabindex="0" 또는 tabindex="-1" 사용
- 양수 tabindex 값 제거

### 설정 사유

- 양수 tabindex는 키보드 탐색 순서를 예측하기 어렵게 만들어 사용자 혼란을 야기
- 하지만 레거시 코드나 특정 라이브러리에서 사용하는 경우가 있어 일괄 수정이 어려움
- 점진적으로 제거하도록 경고하며, 새 코드에서는 사용하지 않도록 권장
