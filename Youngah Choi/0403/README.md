## 플러터 스터디 TIL 4월 

###  2023년 4월 3일 플러터 스터디 공부 
| 날짜       | 제목               | 설명                                | 링크                                                                             |
| ---------- | ------------------ | ----------------------------------- | -------------------------------------------------------------------------------- |
| 04/03 | Flutter  | Flutter, React native  | https://flutterplasma.dev |   

* Wonderous - Flutter로 만들어진 앱, 테스트 추천

* Flutter Plasma - 웹 상에서 Flutter의 가능성을 보여준다. 

### How Flutter Works
* **Native Frameworks** 동작 방식 - Swift로 ios 혹은 Java로 Android를 만드는 native 앱 개발을 할 때 버튼이나 text input 등 모든 요소들을 만들어달라고 운영체제에게 요구하고, 운영체제가 안드로이드 상의 버튼이나 ios 상의 버튼을 만들어준다. 
* **Flutter** - 다른 크로스플랫폼 프레임워크처럼 동작하지 않기에 실제 ios나 안드로이드 버튼을 만드는 기능은 존재하지 않고, 운영체제와 직접적으로 소통하지 않는다. 
* **Flutter Framework** - animation, painting, gestures 등 여러 요소들을 포함하고 있다. 
* **Flutter Engine** - 실제 UI 렌더링을 책임질 엔진으로, c/c++로 짜여졌고 화면 상에 그려주는 역할을 한다. 
* Flutter 어플리케이션은 플랫폼의 native widget을 사용하지 않는다. 
* 엔진이 input을 그려주고 버튼을 그려준다. 운영체제는 엔진을 동작시키고, 엔진이 프레임워크를 동작시키고 그려주는 역할을 수행한다. 
* 플랫폼은 엔진을 동작시키고 엔진이 Dart Flutter 코드를 동작시키면 화면에 UI를 그려준다.
#### iOS
* c/c++ 코드로 짜여진 엔진이 LLVM과 함께 컴파일된다. 유저가 어플리케이션을 다운로드 받은 후 실행시키면 엔진이 여는 것은 "runner" ios 프로젝트이다. "runner" ios 프로젝트는 엔진을 실행시키고 엔진이 UI를 렌더링해준다. 
#### Android
* c/c++ 코드로 짜여진 엔진이 안드로이드의 NDK와 함께 컴파일된다. 코드는 native와 ARM, x86 라이브러리로 컴파일된다. 이 라이브러리는 "runner" 프로젝트에 포함되고 모든 것은 .apk로 빌드된다. 유저가 어플리케이션을 실행시키면 Flutter 엔진을 동작시키는 "runner" 프로젝트를 실행하고 엔진이 Dart 코드를 실행시킨다. 
#### Flutter 사용할 때 발생하는 문제점 
* 운영체제에 의해 그려지는 게 아니라 c++로 만들어진 렌더링 엔진에 의해 그려진다. 작동 방식이 비디오 게임 엔진과 비슷하다.
* native widget을 사용하지 않는다. 따라서 native에서 가능한 위젯을 사용할 수 없어서 앱이 부자연스럽게 보인다.
* animation, Navigation 등 모든 것을 통제할 수 있는 이유 - 어플리케이션의 호스트에 의존할 필요 없이 화면 상의 모든 픽셀을 조절하기 때문이다. 

#### Flutter/other Frameworks
* **Flutter Framework** - 운영체제와 직접 소통하지 않고 엔진을 어플리케이션 내부에 집어넣고 Dart 코드를 컴파일한다. 그리고 유저가 어플리케이션을 실행시킬 때 엔진을 가동시키는 "runner" 프로젝트를 실행시킨다. 그 이후에 엔진이 모든 UI를 Framework와 함께 그려준다. 
* **other Frameworks** - 운영체제와 직접 소통하는 방식

#### Embedder
* **Embedder** : 특정 플랫폼에 특화된 것, Embedder는 엔진을 가동시키는 "runner" 프로젝트를 가리킨다. 호스트 플랫폼 상에서 엔진을 가동시키는 역할을 한다. 

* 유저가 어플리케이션 열 때 빈 캔버스 하나를 열고, 어플리케이션이 시작되면 엔진이 가동되고 모든 위젯을 그린다. 호스트는 캔버스를 렌더링하는 데에만 사용되고 엔진이 캔버스에 불러오는 역할을 수행하고 카메라의 모든 것을 조작한다. 이는 Flutter에서 다양한 것을 할 수 있는 이유이기도 하다. 운영체제에 대한 어떠한 제약 사항도 없다는 뜻이기도 하기 때문이다. 따라서 어플리케이션이 안드로이드와 윈도우 등에서도 똑같이 보일 수 있다.

* Flutter 어플리케이션 상의 모든 것은 호스트에 의해 그려진 것이 아닌 C/C++로 이루어진 엔진에 의해 그려진다. 또한, 위젯 등 보여지는 것들이 실제가 아니라 만들어낸 것이기에 앱이 부자연스럽다. 

### Flutter / React Native
* **React Native** - native widget을 제공한다. native 앱 운영체제 상에서 가능한 위젯을 사용하고 싶을 때 React Native로 만든다. 버튼이나 Loader를 만들면 iOS와 안드로이드에서 서로 다르게 보인다. 이는 Javascript를 통해 운영체제와 대화하고, 운영체제는 native app처럼 보이는 컴포넌트와 위젯을 만들어내는데 이것들은 전부 운영체제에 의해 만들어지기 때문이다. iOS 스타일의 버튼, input, 검색바를 사용하는 iOS스러운 앱을 만들고자 할 때는 호스트 운영체제의 스타일을 제공해주는 React Native를 사용한다. 
* **Flutter** - 컴포넌트를 렌더링하기 위해 운영체제와 직접 소통하지 않는다. 엔진을 통해 모든 컴포넌트를 렌더링한다. 섬세하게 디자인 요구사항이 들어가있고 요소나 애니메이션을 모두 커스터마이징해야 할 때 사용한다. 즉, 커스터마이징된 디자인을 만들거나 iOS 혹은 안드로이드 앱처럼 보이지 않게 만들 때 사용하는 것을 추천한다. 그리고 커스터마이징하려면 화면 상의 모든 픽셀을 통제할 수 있어야 한다.
#### 요약
* React Native : 호스트 운영체제가 제공하는 스타일에 의존하고 싶을 때, 호스트 플랫폼 디자인을 이용하여 만들고 싶을 때 사용
* Flutter : 나만의 커스터마이징된 UI를 만들 때 사용