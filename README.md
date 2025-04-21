# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
    npx expo start
   ```

---

## react native core components and api

## 1. 코어 컴포넌트 (Cross-Platform)

애플리케이션의 기본 UI를 구성하는 핵심 구성요소들로, 안드로이드와 아이오에스 모두에서 동일하게 동작합니다.

### A. 기본 컴포넌트 (Basic Components)

- **View**  
  UI의 기본 컨테이너이자 레이아웃의 빌딩 블록
- **Text**  
  텍스트를 표시하며, 스타일링이나 터치 이벤트까지 처리
- **Image**  
  다양한 포맷의 이미지를 표현
- **TextInput**  
  사용자로부터 텍스트 입력을 받기 위한 컴포넌트
- **ScrollView**  
  여러 하위 컴포넌트를 감싸면서 스크롤이 가능한 컨테이너
- **StyleSheet**  
  CSS와 유사한 방식으로 스타일을 정의할 수 있는 도구

### B. 사용자 인터페이스 (User Interface)

- **Button**  
  터치 이벤트를 감지하는 기본 버튼 컴포넌트
- **Switch**  
  Boolean 타입의 값을 토글할 수 있는 스위치

### C. 리스트 뷰 (List Views)

- **FlatList**  
  최적화된 스크롤 가능한 리스트로, 큰 데이터 집합에 적합
- **SectionList**  
  구간별(section) 리스트 렌더링에 특화된 컴포넌트

## 2. 플랫폼별 컴포넌트 및 API

필요에 따라 해당 플랫폼 전용 기능을 제공하는 컴포넌트를 사용할 수 있습니다.

### A. 안드로이드 전용 (Android-Specific Components and APIs)

- **BackHandler**  
  안드로이드의 하드웨어 백 버튼 이벤트 처리를 위한 API
- **DrawerLayoutAndroid**  
  안드로이드 네이티브의 내비게이션 드로어(Drawer)를 구현
- **PermissionsAndroid**  
  안드로이드 런타임 권한 요청 및 관리
- **ToastAndroid**  
  안드로이드 특유의 Toast(짧은 메시지 팝업) 알림 생성

### B. 아이오에스 전용 (iOS-Specific Components and APIs)

- **ActionSheetIOS**  
  아이오에스 스타일의 액션 시트(옵션 목록 또는 공유 시트)를 표시  
  _(추가로 아이오에스의 UIKit 기반의 다양한 네이티브 컴포넌트를 필요에 따라 네이티브 모듈로 래핑해 사용할 수 있습니다.)_

## 3. 기타 유용한 컴포넌트 및 API (Others)

크로스 플랫폼 및 플랫폼별 컴포넌트 외에도, 앱 개발에 도움이 되는 다양한 유틸리티 컴포넌트와 API가 제공됩니다.

- **ActivityIndicator**  
  로딩 상태를 나타내는 원형 스피너
- **Alert**  
  모달 형태의 알림 대화상자 표시
- **Animated**  
  자연스러운 애니메이션 효과 구현을 위한 라이브러리
- **Dimensions**  
  기기의 화면 크기 및 방향 정보를 제공
- **KeyboardAvoidingView**  
  키보드가 나타날 때 자동으로 레이아웃을 조정하여 입력창 가리기를 방지
- **Linking**  
  앱 내외의 URL 연동 및 딥 링크 지원
- **Modal**  
  기존 뷰 위에 내용을 오버레이 형태로 표시하는 모달 창
- **PixelRatio**  
  디바이스의 픽셀 밀도 정보를 제공하여, 해상도 관련 처리를 지원
- **RefreshControl**  
  ScrollView 내부에서 당겨서 새로고침 기능을 구현
- **StatusBar**  
  디바이스의 상태 표시줄(시계, 배터리 아이콘 등) 스타일과 동작 제어
