---
layout: post
title: "[ionic] Ionic Deeplinks 플러그인 "
tags: [ionic]
categories: [ionic]
banner:
  image: "/assets/images/banners/2024/06/19-ionic.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---


## 딥 링크(Deep Links)란?

딥 링크 플러그인은 `Android` 앱 링크와 `iOS` 유니버셜 링크 모두에 대한 딥 링크 지원을 제공합니다.
특정 주소를 입력하면 `앱이 실행`,`앱 내 특정 화면으로 이동`시키는 링크를 말합니다.
 

## 딥링크는 3가지 방식
- URI 스킴 방식 : 앱에 URI 스킴(scheme) 값을 등록해 딥링크 사용
- 앱링크(App Link) : Andorid 제공 - 도메인 주소를 이용한 딥링크 사용
- 유니버셩 링크 (Universal Link) : iOS 제공 - 도메인 주소를 이용한 딥링크 사용 


### URI Scheme 방식 

가장 일반적으로 사용되는 딥링크 방식은 URI Scheme 방식입니다.
URI 스킴을 이용한 딥링크는 앱에 Scheme값을 등록하는 형태로 앱을 구분합니다. 스킴은 앱마다 등록할 수 있는 값으로 "특정 스킴값을 호출하면 특정 앱이 오픈된다." 라는 약속을 실행합니다. 여러분이 트위터 앱을 오픈하고자 한다면 twitter:// 라는 스킴값을 이용하면 됩니다. 이 스킴값은 앱 개발시 효율적인 앱 오픈을 위해 자체적으로 개발사에서 자신들만의 값으로 등록을 하게 됩니다.

앱 내에서의 특정 페이지는 'path' 값으로 구분합니다. 예를 들어, 트위터 앱의 회원가입 페이지를 오픈하고자 한다면 twitter://signup 이라는 값을 사용합니다.

정리하면, URI 스킴 방식은 Scheme://Path라는 두개의 요소로 구성됩니다.

- Scheme://Path
- Scheme = 앱을 특정함 (트위터)
- Path = 앱 내 페이지를 특정함 (트위터 내 회원가입 페이지)
- 안드로이드의 경우 아래와 같이 Androidmanifest.xml 이라는 파일에 스킴 값을 등록합니다.




### javaScript에서 딥링크 방법

platform.ready 또는 deviceready event 에서 ionic deepLink 호출 
```javascript
import { Platform, NavController } from 'ionic-angular';
import { Deeplinks } from '@ionic-native/deeplinks/ngx';

export class MyApp {
  constructor(
    protected platform: Platform
    , protected navController: NavController
    , protected deeplinks: Deeplinks
    ) {
    this.platform.ready().then(() => {
      this.deeplinks.route({
        '/about-us': HomePage,
        '/products/:productId': HelpPage
      }).subscribe((match) => {  // subscribe : 앱이 정의된 경로와 일치하는 딥 링크를 처리하는 곳, 딥 링크가 경로 중 하나 일치하면 첫 번째 함수 내부의 코드가 실행됩니다.
        // match.$route - the route we matched, which is the matched entry from the arguments to route()
        // match.$args - the args passed in the link
        // match.$link - the full link data
        console.log('Successfully matched route', match);
      },
      (nomatch) => {   // 해당 링크 일치하지 않음으로 콘솔에러 메시지 
        // nomatch.$link - the full link data
        console.error('Got a deeplink that didn\'t match', nomatch);
      });
    });
  }
}
```