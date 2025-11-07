# 25-02-PB-2-2: Vue 2 → Vue 3 마이그레이션

**GitHub Repo:** `https://github.com/s44158619-code/25-02-PB-2-2.git`

## 📌 프로젝트 개요

이 프로젝트는 Vue 2의 **Options API** 또는 Vue 3의 `setup()` 함수 방식으로 작성된 기존 예제 컴포넌트들을, 최신 Vue 3 스타일인 **`<script setup>`** 구문으로 리팩터링하는 과제입니다.

모든 컴포넌트의 기능과 화면은 유지하면서 내부 코드 스타일만 Vue 3 방식으로 전환하는 것을 목표로 했습니다.

---

## 🔥 변경 요약 (Summary of Changes)

프로젝트 내의 모든 `.vue` 컴포넌트 파일(`main.js` 제외)을 **`<script setup>`** 기반의 Composition API로 통일했습니다.

### 1. `<script setup>` 구문 도입 및 보일러플레이트 제거

* 모든 컴포넌트에 `<script lang="ts" setup>`을 적용했습니다.
* 불필요한 `export default { ... }` 및 `setup() { ... }` 래퍼(wrapper) 코드를 모두 제거하여 코드를 간결하게 만들었습니다.
* `setup()` 함수 내의 `return { ... }` 구문을 제거했습니다. (`<script setup>`에서는 최상위 변수/함수가 템플릿에 자동 노출됩니다.)

### 2. Options API → Composition API 핵심 변환

* **Reactivity (반응성)**
    * `data()` 옵션 → `ref()` 또는 `reactive()` 함수로 대체했습니다.
    * (예: `E04Directives.vue`, `E03Binding.vue`, `E02Reactive.vue`)

* **Methods (함수)**
    * `methods: { ... }` 옵션 → `<script setup>` 내의 최상위 `const func = () => { ... }` 함수 선언으로 변경했습니다.
    * (예: `E07OptionsApi.vue`, `E03Binding.vue`)

* **Computed (계산된 속성)**
    * `computed: { ... }` 옵션 → `const val = computed(() => { ... })` 함수로 변경했습니다.
    * (예: `E07OptionsApi.vue`, `E02Reactive.vue`)

* **Lifecycle (라이프사이클 훅)**
    * `mounted()`, `beforeMount()` 등 옵션 훅 → `onMounted()`, `onBeforeMount()` 등 Composition API 훅으로 대체했습니다.
    * (`beforeCreate`, `created`는 `<script setup>` 실행 시점으로 자연스럽게 통합되었습니다.)
    * (예: `E07OptionsApi.vue`, `E12RefComponent.vue`)

* **Props & Emits (데이터 전달)**
    * `props: [...]` 옵션 → `defineProps()` 매크로로 대체했습니다.
    * `$emit`을 명시적으로 선언하기 위해 `defineEmits()` 매크로를 사용했습니다.
    * (예: `E05ParentComponent.vue`의 자식 컴포넌트)

* **Provide & Inject (데이터 주입)**
    * `provide: { ... }` 옵션 → `provide()` 함수로 변경했습니다.
    * `inject: [...]` 옵션 → `inject()` 함수로 변경했습니다.
    * (예: `E06ParentComponent.vue` 및 하위 자식 컴포넌트)

* **`this` 키워드 제거**
    * Options API에서 컴포넌트 인스턴스를 가리키던 `this` 키워드 사용을 모두 제거했습니다.
    * 대신 `ref`로 선언된 변수의 `.value` 속성으로 상태에 접근하도록 수정했습니다.

### 3. TypeScript 및 일관성 적용

* 모든 스크립트 태그에 `lang="ts"`를 적용하여 프로젝트 전체를 타입스크립트 기반으로 통일했습니다.
* `E12RefComponent.vue` 등 DOM 요소를 참조하는 `ref`에 `ref<HTMLInputElement | null>(null)`와 같이 명시적인 타입을 지정하여 코드 안정성을 높였습니다.

---

## 🖥️ 동작 확인용 스크린샷

*(과제 요구사항) 변환 후에도 기존과 동일하게 동작하는 화면 스크린샷을 여기에 첨부하세요.*

![동작 확인 예시 1](<./path/to/screenshot1.png>)
![동작 확인 예시 2](<./path/to/screenshot2.png>)