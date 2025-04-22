# Expo Router - Tabs 네비게이터 요약

Expo Router의 Tabs 네비게이터는 앱 하단에 탭 바를 추가하여 여러 화면 간 쉽게 이동할 수 있도록 도와줍니다. 이 기능을 활용하면 직관적인 UI를 구성할 수 있으며, React Navigation의 Bottom Tabs Navigator를 기반으로 동작합니다.

## 1. 기본 파일 구조

파일 기반 라우팅을 사용하여 탭 네비게이터를 구성할 수 있습니다. 예를 들어, 아래와 같은 파일 구조를 가정해 봅니다.

```text
app/ ├── _layout.tsx ├── (tabs)/ │ ├── _layout.tsx │ ├── index.tsx  │ ├── settings.tsx
```

- `app/_layout.tsx`: 앱의 전체 레이아웃을 정의하는 파일
- `(tabs)/_layout.tsx`: 탭 네비게이터를 설정하는 파일
- `(tabs)/index.tsx`: 기본 탭 (홈 화면)
- `(tabs)/settings.tsx`: 설정 탭

## 2. 기본 탭 네비게이터 설정

`(tabs)/_layout.tsx` 파일에서 `Tabs` 컴포넌트를 사용하여 탭 네비게이터를 설정할 수 있습니다.

```tsx
import FontAwesome from "@expo/vector-icons/FontAwesome";
import { Tabs } from "expo-router";

export default function TabLayout() {
  return (
    <Tabs screenOptions={{ tabBarActiveTintColor: "blue" }}>
      <Tabs.Screen
        name="index"
        options={{
          title: "Home",
          tabBarIcon: ({ color }) => (
            <FontAwesome size={28} name="home" color={color} />
          ),
        }}
      />
      <Tabs.Screen
        name="settings"
        options={{
          title: "Settings",
          tabBarIcon: ({ color }) => (
            <FontAwesome size={28} name="cog" color={color} />
          ),
        }}
      />
    </Tabs>
  );
}
```

3. 개별 탭 화면 구성
   각 탭 화면은 index.tsx 및 settings.tsx 파일에서 정의됩니다.

```tsx
import { View, Text, StyleSheet } from "react-native";

export default function Tab() {
  return (
    <View style={styles.container}>
      <Text>Tab [Home|Settings]</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
});
```

4. 탭 숨기기
   특정 탭을 숨기고 싶다면 href: null 옵션을 사용할 수 있습니다.

```tsx
import { Tabs } from "expo-router";

export default function TabLayout() {
  return (
    <Tabs>
      <Tabs.Screen name="index" options={{ href: null }} />
    </Tabs>
  );
}
```

5. 추가적인 커스터마이징
   Expo Router의 Tabs 네비게이터는 React Navigation의 Bottom Tabs Navigator를 기반으로 동작하므로, React Navigation 문서에서 제공하는 다양한 옵션을 활용하여 탭 바를 커스터마이징할 수 있습니다.
