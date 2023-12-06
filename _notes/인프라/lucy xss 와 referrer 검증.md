[REFERER 검증 코드 예제 ]
package blog.in.action.handler;

import org.springframework.web.servlet.HandlerInterceptor;

import javax.servlet.http.HttpServletRequest; import javax.servlet.http.HttpServletResponse;

public class ReferrerCheckInterceptor implements HandlerInterceptor {

```
@Override
public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
    String referer = request.getHeader("Referer");
    String host = request.getHeader("host");
    if (referer == null || !referer.contains(host)) {
        response.sendRedirect("/");
        return false;
    }
    return true;
}

```

}

[https://junhyunny.github.io/information/security/spring-boot/spring-security/cross-site-reqeust-forgery/](https://junhyunny.github.io/information/security/spring-boot/spring-security/cross-site-reqeust-forgery/)

Q) 왜 Spring security 옵션인 CSRF 보호기능 사용안함? rest api를 이용한 서버라면, session 기반 인증과는 다르게 stateless하기 때문에 서버에 인증정보를 보관하지 않는다 따라서 referrer 검증 과 암호화된 토큰 (jwt토큰)사용으로 CSRF를 막을 수 있다.

lucy xss

form data 형식만 처리가능한 라이브러리 지만 json 형식을 messageConverter로 변환하여 filter에 요청하는 방식으로 처리. 결국엔 Request Raw Body로 넘어가는 JSON에 대한 XSS가 제외됨.