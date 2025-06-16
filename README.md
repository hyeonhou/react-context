# React Context API & useReducer 학습 프로젝트

## 🖼️ 프로젝트 스크린샷

![메인 화면](./public/react_context_1.png)
_쇼핑몰 메인 화면 - 상품 목록과 장바구니 기능_

![장바구니 화면](./public/react_context_2.png)
_장바구니 모달 - 실시간 상태 관리 및 수량 조절_

## 📚 프로젝트 개요

이 프로젝트는 React의 **Context API**와 **useReducer Hook**을 사용한 전역 상태 관리를 학습하기 위한 쇼핑몰 애플리케이션입니다. 전통적인 prop drilling 문제를 해결하고, 복잡한 상태 로직을 효율적으로 관리하는 방법을 익힐 수 있습니다.

## 🎯 학습 목표

### 1. React Context API 이해

- **Context 생성**: `createContext()`를 사용한 컨텍스트 생성
- **Provider 패턴**: 컴포넌트 트리에 전역 상태 제공
- **Context 소비**: `use()` Hook을 사용한 컨텍스트 값 접근

### 2. useReducer Hook 활용

- **복잡한 상태 로직 관리**: useState보다 복잡한 상태 업데이트 처리
- **액션 기반 상태 업데이트**: 명확한 액션 타입으로 상태 변경 관리
- **순수 함수**: 예측 가능한 상태 업데이트를 위한 리듀서 함수 작성

### 3. 전역 상태 관리 패턴

- **Prop Drilling 해결**: 깊이 중첩된 컴포넌트 간 데이터 전달 최적화
- **상태 중앙화**: 애플리케이션 전체에서 공유되는 상태 관리
- **컴포넌트 분리**: 상태 로직과 UI 로직의 명확한 분리

## 🛠️ 기술 스택

- **React 19.0.0**: 최신 React 기능 활용
- **Vite**: 빠른 개발 환경 구축
- **Context API**: 전역 상태 관리
- **useReducer**: 복잡한 상태 로직 처리

## 📁 프로젝트 구조

```
src/
├── components/
│   ├── Cart.jsx           # 장바구니 아이템 표시 및 수량 조절
│   ├── CartModal.jsx      # 장바구니 모달 컴포넌트
│   ├── Header.jsx         # 헤더 및 장바구니 버튼
│   ├── Product.jsx        # 개별 상품 컴포넌트
│   └── Shop.jsx           # 상품 목록 래퍼
├── store/
│   └── shopping-cart-context.jsx  # 장바구니 컨텍스트 및 리듀서
├── assets/                # 상품 이미지
├── dummy-products.js      # 더미 상품 데이터
└── App.jsx               # 메인 앱 컴포넌트
```

## 🧠 핵심 학습 내용

### 1. Context API 구현

```jsx
// 컨텍스트 생성
export const CartContext = createContext({
  items: [],
  addItemToCart: () => {},
  updateItemQuantity: () => {},
});

// Provider 컴포넌트
export default function CartContextProvider({ children }) {
  // ... 상태 로직
  return <CartContext value={ctxValue}>{children}</CartContext>;
}
```

### 2. useReducer로 복잡한 상태 관리

```jsx
function shoppingCartReducer(state, action) {
  if (action.type === "ADD_ITEM") {
    // 아이템 추가 로직
  }

  if (action.type === "UPDATE_ITEM") {
    // 아이템 수량 업데이트 로직
  }

  return state;
}
```

### 3. 컴포넌트에서 Context 사용

```jsx
// React 19의 새로운 use() Hook 활용
const { items, addItemToCart } = use(CartContext);
```

## 🔍 주요 기능

### 장바구니 관리

- **상품 추가**: 상품을 장바구니에 추가
- **수량 조절**: 장바구니 내 상품 수량 증가/감소
- **자동 제거**: 수량이 0이 되면 자동으로 장바구니에서 제거
- **실시간 업데이트**: 모든 컴포넌트에서 실시간 장바구니 상태 반영

### 상태 관리 패턴

- **중앙화된 상태**: 장바구니 상태를 한 곳에서 관리
- **액션 기반 업데이트**: 명확한 액션 타입으로 상태 변경
- **불변성 유지**: 상태 업데이트 시 불변성 원칙 준수

## 🚀 실행 방법

1. **의존성 설치**

   ```bash
   npm install
   ```

2. **개발 서버 실행**

   ```bash
   npm run dev
   ```

3. **빌드**
   ```bash
   npm run build
   ```

## 💡 학습 포인트

### Context API의 장점

- **Prop Drilling 제거**: 중간 컴포넌트를 거치지 않고 데이터 전달
- **코드 가독성**: 명확한 데이터 흐름
- **유지보수성**: 상태 로직의 중앙화

### useReducer의 활용

- **복잡한 상태**: 여러 하위 값이 있는 상태 객체 관리
- **예측 가능성**: 순수 함수로 인한 예측 가능한 상태 업데이트
- **디버깅**: 액션 기반으로 상태 변화 추적 용이

### React 19 새 기능

- **use() Hook**: Context를 더 간편하게 사용할 수 있는 새로운 Hook

## 🎓 배운 것들

1. **전역 상태 관리의 필요성**: 컴포넌트 간 상태 공유의 중요성
2. **Context API 활용법**: 효율적인 전역 상태 관리 방법
3. **useReducer 패턴**: 복잡한 상태 로직을 관리하는 방법
4. **상태 불변성**: React에서 상태 업데이트 시 지켜야 할 원칙
5. **컴포넌트 설계**: 상태와 UI 로직의 효과적인 분리

## 📈 다음 단계

이 프로젝트를 통해 학습한 내용을 바탕으로 다음과 같은 심화 학습을 진행할 수 있습니다:

- **Redux Toolkit**: 더 큰 규모의 상태 관리
- **Zustand**: 경량화된 상태 관리 라이브러리
- **React Query**: 서버 상태 관리
- **상태 최적화**: useMemo, useCallback을 활용한 성능 최적화
