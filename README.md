# react-native-trouble-shooting

> react-native를 개발하면서 마주쳤던 trouble shooting을 모아놓은 레포지토리입니다.

## Android

### 안드로이드 apk 빌드할 때 나는 에러 (Android apk build error)

```bash
$ ./gradlew assembleRelease
...
Execution failed for task ':app:processReleaseResources'.
```

#### Solution

gradle.properties에 아래 코드를 넣는다.

```
android.enableAapt2=false
```

> 주의사항: 하지만 android.enableAapt2 옵션은 2018년 말 이후로 deprecated된다고 하니 나중에는 다른 방법을 찾아야할 것 같다.

참고: https://github.com/facebook/react-native/issues/19239
