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
2. ***在 VS Code 上 debug*** 
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

1. React Native 中的 `<View>` 就是 React 中的 `<di>`
2. 要善用 Platform API 來區分不同平臺之間的開發差別，要留意哪些 API 是只能用在 Android，哪些是只能用在 iOS
3. `StylesSheet` 最好和 Js 文件放在一起，方便更改
4. `<View style={[styles.container, containerStyle]}>` 中的 `containerStyle` 會覆蓋 `styles.container ` 的內容
5. Flex 各參數的用法

#### 重點

1. 要熟悉 React Native 中的 API 用法
2. 要善用 `@react-native-community/hooks`

#### Stop @ Layout 10-Exercises