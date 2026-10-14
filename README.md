# Android kotlin-mvvm-covid19
This repository contains simple COVID19 data monitoring with android stack MVVM, Live Data, Koin, RxJava, RxBinding, Offline first with simple caching, etc

![alt text](https://cdn.dribbble.com/users/1114210/screenshots/10762051/media/3250c1dd7fd00434cbf5df6498afb996.png)

## Local setup for this fork

This is a historical educational project. A Google Maps key and the original Android toolchain are required for its map feature. The store/download links below belong to the original project; they are not builds of this fork.

1. Use JDK 11 with the checked-in Gradle 5.6.4 wrapper and Android Gradle Plugin 3.6.3. This legacy wrapper cannot run on the JDK bundled with many current Android Studio releases; select the Gradle JDK explicitly.
2. Install Android SDK Platform 29 and the build tools requested by Gradle. Open the repository in Android Studio and set the SDK location in local `local.properties` if needed.
3. Enable Maps SDK for Android in your own Google Cloud project and create a key following the [official Maps setup guide](https://developers.google.com/maps/documentation/android-sdk/start). Configure any project/billing requirements there. Restrict the key to the package and signing certificate you actually use: `id.rizmaulana.covid19.dev` for `devDebug`, or `id.rizmaulana.covid19` for the production flavor.
4. Add the setting from [gradle.properties.example](gradle.properties.example) to your **user** Gradle properties (`~/.gradle/gradle.properties`, or `%USERPROFILE%\.gradle\gradle.properties` on Windows), preserving other settings. Replace `YOUR_GOOGLE_MAPS_API_KEY` with your own key. The `MAPS_API_KEY` environment variable is an alternative; a Gradle property takes precedence.
5. Select `devDebug`, rebuild, and run on an emulator/device with Google Play services and internet access.

```sh
sh ./gradlew :app:assembleDevDebug
```

On Windows use `gradlew.bat :app:assembleDevDebug`. The debug APK is generated under `app/build/outputs/apk/dev/debug/`. Use `:app:signingReport` to find the signing-certificate SHA-1 needed for your Maps restriction.

### Remaining setup checklist

- `MAPS_API_KEY` is a placeholder in the example. It is inserted into `AndroidManifest.xml` at build time; its default is empty. Without a valid key, Google Maps tiles will not load. Rebuild after changing it.
- Statistics use the original external backend `https://covid19.mathdro.id/` through `BuildConfig.BASE_URL` in both flavors in `app/build.gradle`. Its availability and response format are not guaranteed. If it no longer serves the expected data, provide a compatible replacement and update `BASE_URL` together with the endpoints/models in `data/source/remote/Api.kt`. A Maps key does not enable this separate backend.
- Dependency resolution still relies on historical `jcenter()` and JitPack repositories. If an artifact is unavailable, migrate that dependency/repository before expecting a full build. Keep the Kotlin/AGP/Gradle versions compatible when upgrading.
- A Firebase `google-services.json` is not required by the current app module: it does not apply the Google Services plugin. Do not reintroduce the old historical credentials or prebuilt APK.
- Full APK compilation, device UI behavior, Maps access, and live statistics have not been verified for this setup. The manifest/configuration checks alone do not establish a working backend.

### Available on Playstore 🎉
<a href="https://play.google.com/store/apps/details?id=id.rizmaulana.covid19"><img src="https://locations.massageenvy.com/images/google-play-badge.png" width="200"/></a>
#### Update
Since Google restrict app distribution about covid-19 on Google Play Store, we will upload latest feature apk [here](https://drive.google.com/folderview?id=1MaO9mIKWCFWSK2lFtEfKge1z8XDesi8n)

### Library References
1. RxJava2 
2. Koin 
3. Retrofit
4. RxBinding
5. [Hawk](https://github.com/orhanobut/hawk)
6. [MPAndroidChart](https://github.com/PhilJay/MPAndroidChart)
7. [Dexter](https://github.com/Karumi/Dexter)
8. [SlidingUp Panel](https://github.com/umano/AndroidSlidingUpPanel)
9. Spek2 Framework
10. Android ViewBinding
11. [Kiel](https://github.com/ibrahimyilmaz/kiel)

### License
```
   Copyright (C) 2020

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

### Contributing
Just make pull request. You are in!
