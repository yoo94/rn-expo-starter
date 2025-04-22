# Expo Router 파일 기반 네비게이션 표기법 요약

Expo Router는 파일 및 폴더 이름에 특정 표기법(노테이션)을 사용하여 앱의 네비게이션 트리와 URL 매핑을 정의합니다. 아래는 각 표기법의 주요 개념입니다.

## 1. 일반 파일 및 디렉토리 (Simple Names / No Notation)

- **정적 경로**: 파일이나 디렉토리 이름을 그대로 사용하면, 파일 시스템 구조가 곧 URL 경로가 됩니다.
  - 예) `app/home.tsx`는 `/home` 경로,  
    `app/feed/favorites.tsx`는 `/feed/favorites` 경로에 매핑됩니다.

## 2. 대괄호 표기법 (Square Brackets)

- **동적 경로**: 파일명 또는 폴더명을 대괄호([])로 감싸면, 해당 부분이 동적 파라미터로 처리됩니다.
  - 예) `app/[userName].tsx`는 `/evanbacon`, `/expo` 등 파라미터에 따라 다양한 URL로 매핑됩니다.
  - 페이지 내에서는 `useLocalSearchParams` 훅을 이용해 해당 파라미터의 값을 불러올 수 있습니다.

## 3. 괄호 표기법 (Parentheses)

- **라우트 그룹 (Route Groups)**: 디렉토리 이름을 괄호로 감싸면, URL에 나타나지 않으면서 여러 화면을 그룹화할 수 있습니다.
  - 예) `app/(tabs)/settings.tsx`는 실제 URL이 `/settings`로 매핑되며, `tabs` 폴더는 네비게이션 구조를 조직하기 위한 용도로 사용됩니다.
  - 이를 통해 복잡한 네비게이션 레이아웃(예: 탭, 스택 등)을 보다 깔끔하게 구성할 수 있습니다.

## 4. Index 파일 (index.tsx)

- **기본 라우트 지정**: 각 디렉토리 내의 `index.tsx` 파일은 해당 폴더의 기본(루트) 페이지를 의미합니다.
  - 예) `app/profile/index.tsx`는 `/profile` 경로에 해당합니다.
  - 라우트 그룹 내부에서도 가장 가까운 `index.tsx` 파일이 기본 라우트로 사용됩니다.

## 5. 레이아웃 파일 (\_layout.tsx)

- **레이아웃 정의**: `_layout.tsx` 파일은 개별 페이지가 아니라, 해당 디렉토리 내의 라우트들을 감싸는 레이아웃 컴포넌트를 정의합니다.
  - 예) `app/_layout.tsx`는 앱 전체의 초기화 코드(폰트 로딩, 스플래시 스크린 등)를 관리합니다.
  - 동일 디렉토리 내의 다른 `_layout.tsx` 파일은 해당 그룹 내에서 스택, 탭 등의 네비게이션 관계를 설정하는 역할을 합니다.

## 6. 플러스 기호 (+) 표기법

- **특별한 용도의 파일**: 파일명이 `+` 로 시작하면 Expo Router에서 특정 기능을 위해 예약된 파일로 인식합니다.
  - 예) `+not-found.tsx`는 매칭되는 라우트가 없을 경우 표시될 404 페이지 역할을 합니다.
  - `+native-intent.tsx`는 네이티브 딥링크 처리와 같은 특별한 동작을 구현할 때 사용됩니다.

---

이와 같이 Expo Router의 표기법은 파일 시스템 구조와 URL 경로를 자연스럽게 연계하여, 개발자가 복잡한 네비게이션을 명확하고 직관적으로 구성할 수 있도록 돕습니다.

---

## Stack Navigation

개념:

Stack Navigation은 화면을 카드처럼 쌓아 올리는 방식으로, 새로운 화면이 이전 화면 위에 쌓입니다.
사용자는 새로운 화면으로 이동하거나 이전 화면으로 돌아갈 수 있습니다.
일반적으로 @react-navigation/stack 패키지를 사용하여 구현합니다.
특징:

기본적인 화면 전환 애니메이션을 제공합니다.
하드웨어 백 버튼이나 헤더의 백 버튼을 통해 뒤로 이동할 수 있습니다.
화면 간 매개변수를 전달할 수 있습니다.
사용 예시:

```tsx
import { createStackNavigator } from "@react-navigation/stack";

const Stack = createStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Home">
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Details" component={DetailsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

## Tab Navigation

개념:

Tab Navigation은 화면 하단에 탭을 제공하여 사용자가 앱의 다른 섹션 간에 빠르게 전환할 수 있도록 합니다.
주로 @react-navigation/bottom-tabs 패키지를 사용하여 구현합니다.
특징:

앱의 여러 주요 섹션에 대한 지속적인 네비게이션을 제공합니다.
탭 아이콘과 레이블을 사용자 정의할 수 있습니다.
상위 수준의 뷰에 빠르고 쉽게 접근할 수 있습니다.
사용 예시:

```tsx
import { createBottomTabNavigator } from "@react-navigation/bottom-tabs";

const Tab = createBottomTabNavigator();

function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator>
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="Profile" component={ProfileScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

## 차이점

구조: Stack은 화면을 쌓아 올리는 구조로, 사용자가 이전 화면으로 돌아갈 수 있는 반면, Tab은 여러 화면을 나란히 배치하여 사용자가 탭을 통해 쉽게 전환할 수 있습니다.
사용 사례: Stack은 일반적으로 단계별로 진행되는 프로세스나 깊이 있는 탐색에 적합하며, Tab은 여러 주요 섹션을 빠르게 탐색할 수 있는 앱에 적합합니다.
애니메이션 및 전환: Stack은 화면 전환 시 애니메이션을 제공하며, Tab은 탭 간 전환 시 애니메이션을 제공합니다.
