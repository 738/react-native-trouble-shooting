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

### 안드로이드 빌드할 때 다음 에러가 뜸

```
Fatal Exception: java.lang.IllegalStateException: Native module RNDeviceModule tried to override RNDeviceModule for module name RNDeviceInfo. If this was your intention, set canOverrideExistingModule=true
       at com.facebook.react.NativeModuleRegistryBuilder.addNativeModule(NativeModuleRegistryBuilder.java:121)
       at com.facebook.react.NativeModuleRegistryBuilder.processPackage(NativeModuleRegistryBuilder.java:109)
       at com.facebook.react.ReactInstanceManager.processPackage(ReactInstanceManager.java:1050)
       at com.facebook.react.ReactInstanceManager.processPackages(ReactInstanceManager.java:1021)
       at com.facebook.react.ReactInstanceManager.createReactContext(ReactInstanceManager.java:959)
       at com.facebook.react.ReactInstanceManager.access$600(ReactInstanceManager.java:109)
       at com.facebook.react.ReactInstanceManager$4.run(ReactInstanceManager.java:802)
       at java.lang.Thread.run(Thread.java:818)
```

#### Solution

MainApplication.java의 protected List<ReactPackage> getPackages() 부분에서 RNDeviceModule이 두 번 들어있을 것이다.

참고: https://github.com/rebeccahughes/react-native-device-info/issues/243


