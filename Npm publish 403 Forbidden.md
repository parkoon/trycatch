# Npm publish 403 Forbidden

[NPM](https://www.npmjs.com/) 에 접속해서 회원가입 후에 패키지를 하나 만들고 `npm publish` 을 입력하니 아래와 같이 에러가 발생한다.

```
npm ERR! code E403
npm ERR! 403 403 Forbidden - PUT http://registry.npmjs.org/passport-naver-v2 - Forbidden
npm ERR! 403 In most cases, you or one of your dependencies are requesting
npm ERR! 403 a package version that is forbidden by your security policy.
```

> NPM 에 직접 들어가 `repository` 를 만들고 다시 `publish` 을 해야하나? 🧐

라는 의문이 들어 NPM 에 들어가보니, **private repository** 만드는 버튼밖에 없다.

검색을 해보니, 로그인을 해야 한다고 한다.

```
$ npm login
```

위 명령를 입력하니 **username** **password** **email** 을 입력하는 화면이 출력된다.

정상적으로 입력했다면 `npm whoami` 를 입력해보자.

**username** 이 나온다면, 정상적으로 로그인된 것으로 볼 수 있다.

이제 다시 `npm publish` 을 입력해보자.

보통은 여기서 해결이 될 것이다.

나는 여기서 해결이 되지 않고 계속해서 동일한 에러 메세지가 출력됬다. 이유는 회원가입을 방금했고, NPM 에서 내 메일에 인증 메일을 전송했는데 인증 확인을 누르지 않아 발생했던 것이다.

~~결론, NPM 개발자님들아 에러 메세지좀 제대로 적어주세요. 계정 인증이 필요하다고 보내주면 얼마나 좋아요. 아까운 내 1시간 😢~~
