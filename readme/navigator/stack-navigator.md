# Expo Router - Stack 네비게이터 요약

Expo Router의 Stack 네비게이터는 앱 내에서 화면 간 전환(네비게이션)을 관리하는 기본 구조입니다.
Android에서는 새로운 화면이 기존 화면 위로 쌓이는 애니메이션,
iOS에서는 오른쪽에서 슬라이드되는 애니메이션 효과를 제공합니다.

## 기본 파일 구조와 사용 방법

파일 기반 라우팅을 사용하여 간단한 스택 네비게이터를 구성할 수 있습니다. 예를 들어, 아래와 같은 파일 구조가 있다고 가정해 봅니다.

```text
app/ ├── _layout.tsx ├── index.tsx  └── details.tsx
```

- `app/index.tsx`는 스택의 시작(루트) 페이지로 동작합니다.
- `app/details.tsx`는 네비게이션을 통해 `index` 화면 위로 쌓이는 추가 페이지로 동작합니다.

`_layout.tsx` 파일에서 `Stack` 컴포넌트를 사용해 전체 네비게이션 스택을 설정할 수 있습니다.

```tsx
import { Stack } from "expo-router/stack";

export default function Layout() {
  return <Stack />;
}
```

스크린 옵션과 헤더 설정

1. 정적 옵션 설정
   <Stack.Screen> 컴포넌트를 활용하여 각 라우트의 옵션(헤더 스타일, 제목, 색상 등)을 미리 정의할 수 있습니다. 예를 들어:

```tsx
import { Stack } from "expo-router";

export default function Layout() {
  return (
    <Stack
      screenOptions={{
        headerStyle: {
          backgroundColor: "#f4511e",
        },
        headerTintColor: "#fff",
        headerTitleStyle: {
          fontWeight: "bold",
        },
      }}
    >
      {/* 각 라우트에 대한 옵션은 여기서 추가로 정의할 수 있음 */}
      <Stack.Screen name="home" options={{}} />
    </Stack>
  );
}
```

2. 동적 옵션 설정
   각 화면 컴포넌트 내부에서 navigation.setOptions()를 사용해 헤더 옵션을 동적으로 변경할 수도 있습니다.

```tsx
import { Stack, useNavigation } from "expo-router";
import { Text, View } from "react-native";
import { useEffect } from "react";

export default function Home() {
  const navigation = useNavigation();

  useEffect(() => {
    navigation.setOptions({
      headerShown: false,
    });
  }, [navigation]);

  return (
    <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
      <Text>Home Screen</Text>
    </View>
  );
}
```

헤더 바 구성 방법
Stack 네비게이터의 screenOptions를 이용하면 모든 스크린에 대해 공통된 헤더 스타일을 적용할 수 있습니다.

```tsx
import { Stack } from "expo-router";

export default function Layout() {
  return (
    <Stack
      screenOptions={{
        headerStyle: {
          backgroundColor: "#f4511e",
        },
        headerTintColor: "#fff",
        headerTitleStyle: {
          fontWeight: "bold",
        },
      }}
    />
  );
}
```

또한, 개별 스크린에서 <Stack.Screen> 컴포넌트를 사용해 특정 화면의 헤더 제목이나 아이콘 등 세부 옵션을 직접 설정할 수 있습니다.

```tsx
import { Link, Stack } from "expo-router";
import { Image, Text, View, StyleSheet } from "react-native";

function LogoTitle() {
  return (
    <Image
      style={styles.image}
      source={{ uri: "https://reactnative.dev/img/tiny_logo.png" }}
    />
  );
}

export default function Home() {
  return (
    <View style={styles.container}>
      <Stack.Screen options={{ title: "My home" }} />
      <Text>Home Screen</Text>
      {/* 추가 UI 구성 요소 */}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: "center",
    justifyContent: "center",
  },
  image: {
    width: 30,
    height: 30,
  },
});
```
