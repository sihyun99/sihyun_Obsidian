
[REFERER 검증 코드 예제 ]
package blog.in.action.handler;

import org.springframework.web.servlet.HandlerInterceptor;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class ReferrerCheckInterceptor implements HandlerInterceptor {

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
}


https://junhyunny.github.io/information/security/spring-boot/spring-security/cross-site-reqeust-forgery/

Q) 왜 Spring security 옵션인 CSRF 보호기능 사용안함? 
 rest api를 이용한 서버라면, session 기반 인증과는 다르게 stateless하기 때문에 서버에 인증정보를 보관하지 않는다
따라서 referrer 검증 과 암호화된 토큰 (jwt토큰)사용으로 CSRF를 막을 수 있다. 