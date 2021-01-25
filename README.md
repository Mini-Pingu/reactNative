# React Native

學習 React Native :)

這個是我 2021 年第一個計劃，媽的，一定要完成，並且記在腦子裏。

學習過程中的筆記也會記錄在這裏。

按照 Mosh 的課程大綱兩部分:

1. The Ultimate React Native Series: Fundamentals
2. The Ultimate React Native Series: Advanced Concepts

## No.1: Getting Started

### 2021-01-20 （早上）

#### 筆記

1. React Native 就是一套東西，可以用在兩個平臺上（iOS, Android）。
2. 可以直接用 Expo 來發布自己的作品（最重要），和在模擬器上測試 + 實機測試
3. 最好可以在模擬器上開發，實機上測試

#### 工具

1. Expo （Mosh 是用 Expo 的...）
2. React Native CLI

#### 要求

1. node > 12

2. 電腦安裝

   - expo

   ```shell
   $ npm install -g expo
   ```

   - VS Code extensions
     1. React Native Tools
     2. React-Native/React/Redux snippets for es6/es7
     3. Prettier => 需要將 vscode 的 Setting 裏的 Format On Save 打勾
     4. Material Icon Theme

3. 手機安裝 expo client

#### 流程

1. 安裝 node 和 expo

2. 初始化項目

   ```shell
   $ expo init firstProject
   ```

3. 啓動項目

   ```shell
   $ cd firstProject && yarn start
   ```

4. [安裝 android 模擬器](https://docs.expo.io/workflow/android-studio-emulator/) （因爲安裝過程出現問題，加上是用手機爲電腦提供網絡，所以目前只能在實機上進行開發。）

5. 開發 + 打 log + debug

6. 發布在 expo 上

#### 重點

1. 在 VS Code 上打 Log
2. **_在 VS Code 上 debug_**
   1. 在 VS Code 的 debug 中按 create a launch.json
   2. 選擇 Attach to packager
   3. 在 VS Code 的 Settings 的 Users 中，修改 react-native.packager.port 改爲 19000 (啓動 Expo 時，Chrome 上顯示 debug 的端口)
   4. 關閉 Chrome 上的 debug page
   5. 開啓 VS Code 的 Debug

#### 問題 & 之後

1. 可以找出並對比 Expo 和 React Native CLI 的不同
2. 解決 ubuntu 不能正確安裝 android 模擬器問題

## No.2: Fundamental Concepts & Layout

### 2021-01-20（晚上）

#### 筆記

1. React Native 中的 `<View>` 就是 React 中的 `<div>`
2. 要善用 Platform API 來區分不同平臺之間的開發差別，要留意哪些 API 是只能用在 Android，哪些是只能用在 iOS
3. `StylesSheet` 最好和 Js 文件放在一起，方便更改
4. `<View style={[styles.container, containerStyle]}>` 中的 `containerStyle` 會覆蓋 `styles.container ` 的內容
5. Flex 各參數的用法

#### 重點

1. 要熟悉 React Native 中的 API 用法
2. 要善用 `@react-native-community/hooks`

## No.3: Layout

### 2021-01-21（早上）

#### 筆記

1. `justifyContent` 是 x 軸上控制位置的參數，`alignItems` 是 y 軸上控制位置的參數
2. `flex` 是必要參數，`position` 和 `top` 等參數是控制單個 component 位置的最好參數
3. `app.json` 中 `expo` 中的 ` "orientation": "protrait"` 可以控制應用的橫豎屏的切換
   - protrait: 豎屏
   - landscape: 橫屏
   - default: 自動偵測

#### 重點

1. 將一些重要並且經常要修改的參數放在另一個 config 的 folder 裏，主文件只是負責引入就好了

2. 注意項目架構

3. 目前架構

   ```shell
   .
   ├── app
   ├── App.js
   ├── app.json
   ├── babel.config.js
   ├── jsconfig.json
   ├── node_modules
   ├── package.json
   └── yarn.lock
   ```

   ```shell
   .
   ├── assets
   │   ├── adaptive-icon.png
   │   ├── background.jpg
   │   ├── chair.jpg
   │   ├── favicon.png
   │   ├── icon.png
   │   ├── logo-red.png
   │   └── splash.png
   ├── config
   │   └── colors.js
   └── screens
       ├── ViewImageScreen.js
       └── WelcomeScreen.js
   ```

#### 問題 & 之後

1. 每次完成單個 feature 之後，最好要 Refactor d code

## No.4 Styling

### 2021-01-21 （晚上）& 2021-01-22（早上）& 2021-01-22（晚上）

#### 筆記

1. 可以在 [這裏](https://icons.expo.fyi/) 選擇更多的 icon
2. 留意 stylesSheet 中`overflow` 的用法
3. UI 庫推介使用 [React Native Elements](https://reactnativeelements.com/) 或者 [@expo/vector-icons](https://icons.expo.fyi/)

#### 重點

1. 移動平臺之間的 styles 顯示的不同是重點

   ```
   ├── assets
   │   ├── adaptive-icon.png
   │   ├── background.jpg
   │   ├── chair.jpg
   │   ├── favicon.png
   │   ├── icon.png
   │   ├── logo-red.png
   │   └── splash.png
   ├── components
   │   ├── AppText.android.js // 根據平臺不同，只要在後綴之前添加 平臺 名稱就好
   │   └── AppText.ios.js //
   ├── config
   │   └── colors.js
   └── screens
       ├── ViewImageScreen.js
       └── WelcomeScreen.js
   ```

2. 在 App.js 中 import 也會進行簡單的選擇

   ```react
   import React from "react";
   import { Text, View, StyleSheet } from "react-native";
   import { AntDesign } from "@expo/vector-icons";

   import AppText from "./app/components/AppText";

   export default function App() {
     return (
       <View style={styles.container}>
         {/* <View style={styles.container2}> ...
         // Other codes...
   ```

3. 要善用 styles 的覆蓋性

   ```react
   # AppText.android.js
   function AppText({ children, style }) {
     return <Text style={[styles.text, style]}>{children}</Text>; // [styles.text, style]
   }
   ```

   ```react
   # App.js
   <AppText style={styles.subTitle}>{subTitle}</AppText> // 這樣子就可以傳入獨有的 styles
   ```

4. app 裏的文件架構

   ```shell
   .
   ├── assets
   │   ├── adaptive-icon.png
   │   ├── background.jpg
   │   ├── chair.jpg
   │   ├── favicon.png
   │   ├── icon.png
   │   ├── logo-red.png
   │   └── splash.png
   ├── components
   │   ├── AppButton
   │   │   ├── AppButton.android.js // 類似 html
   │   │   ├── index.js // export 口
   │   │   └── styles.js // css
   │   ├── AppCard
   │   │   ├── AppCard.android.js
   │   │   ├── index.js
   │   │   └── styles.js
   │   └── AppText
   │       ├── AppText.android.js
   │       ├── AppText.ios.js
   │       ├── index.js
   │       └── styles.js
   ├── config
   │   └── colors.js
   └── screens // Views
       ├── ViewImageScreen.js
       └── WelcomeScreen.js
   ```

   - 將一些常變化的 參數 添加到 `config ` 的文件夾裏
   - 每個 component 都要區分出 android 和 iOS 的版本
   - `styles.js` 和 xxx.android.js 要分開
   - 每個 component 都要有 `index.js ` 來作爲 export 口
   - `screens` 就類似 React 的 `views`

## No.5 Lists

### 2021-01-23（早上）& 2020-01-23（晚上）

#### 筆記

1. 可以從 [expo-constant](https://docs.expo.io/versions/latest/sdk/constants/) 中獲取機器原始數據，如平臺類型等
2. 凡系要重復兩次使用的 component 都要單獨寫出來，並且要寫到全世界通用的模式
3. Expo 的 API 要學習：[API Reference](https://docs.expo.io/versions/latest/)

#### 重點

#### 代碼

#### 跟進問題

1. 把 VS Code 中的 **ES7 React/Redux/GraphQL/React-Native snippets extension** 看熟悉

### 2021-01-25（早上）

#### 筆記

1. 可以參考 mosh，現在 prop components 上規定好了 children component 要獨特展示什麼東西，對應設定什麼參數，如：

   ```react
   // 先構想好要展示什麼內容
   // 接着設定 props 的參數
   <Icon name="email" size={50} backgroundColor="red" iconColor="white" />
   
   // 最後在 children 中設定
   function Icon({name, //...}) {
     return ()
   }
   ```

#### 重點

1. `rsf` => 創建 React Functional Content for starting a file

1. 一定要注意 每個 components 都要保持獨立性，保持可復性要高

#### 代碼

#### 跟進問題

## No.6 Input Components (34m)

### 2021-01-25 （早上）

#### 筆記

#### 重點

1. 傳參時可以使用 `...otherProps` 來將剩下全部的參數一模一樣地傳下去

   ```react
   // App.js
   <AppTextInput placeholder="hihi" />
   
   // AppTextInput.android.js
   function AppTextInput({ icon, ...otherProps }) { // ...otherProps
     return (
       <View style={styles.container}>
         {icon && <MaterialCommunityIcons name={icon} />}
         <TextInput style={styles.textInput} {...otherProps} />
       </View>
     );
   }
   ```


### 2021-01-26（晚上）

#### 筆記

1. 可以在 `./config/styles` 中將其他不同風格的 `styles.js` 組合在一起，方便其他 component 取用，和提高可讀性

   ```react
   import { Platform } from "react-native";
   
   import colors from "./colors";
   
   export default { // default
     text: {
       color: colors.dark,
       fontSize: 18,
       fontFamily: "Roboto",
     },
   };
   ```

2. 可以選擇用 expo 的 [DateTimePicker](https://docs.expo.io/versions/latest/sdk/date-time-picker/) 來代替 react-native 的 DateTimePicker

#### 重點