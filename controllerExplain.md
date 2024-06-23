### 패키지 및 라이브러리 임포트

```java
package com.webjjang.main.controller;
```
- **패키지 선언**: 코드를 논리적으로 묶기 위해 사용됩니다. 여기서는 `com.webjjang.main.controller` 패키지에 속하는 클래스를 정의합니다.

```java
import java.io.IOException;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import com.webjjang.board.controller.BoardController;
```
- **라이브러리 임포트**: 서블릿과 관련된 다양한 기능을 사용하기 위해 필요한 라이브러리를 가져옵니다.
  - `ServletConfig`, `ServletException`, `HttpServletRequest`, `HttpServletResponse` 등은 서블릿 기능을 제공합니다.
  - `BoardController`는 게시판 관련 요청을 처리하는 클래스입니다.

### 클래스 선언 및 변수 정의

```java
/**
 * Servlet implementation class DispatcherServlet
 */
public class DispatcherServlet extends HttpServlet {
   private static final long serialVersionUID = 1L;
   
   private BoardController boardController = new BoardController();
```
- **클래스 선언**: `DispatcherServlet` 클래스를 정의하고, `HttpServlet`을 상속받아 서블릿으로 동작하게 합니다.
- **변수 선언**: `BoardController` 인스턴스를 생성하여 게시판 관련 요청을 처리할 준비를 합니다.
- `serialVersionUID`: 직렬화에 사용되는 고유 ID로, 객체가 저장되거나 전송될 때 사용됩니다.

### 초기화 메서드

```java
   /**
    * @see Servlet#init(ServletConfig)
    */
   public void init(ServletConfig config) throws ServletException {
      System.out.println("DispatcherServlet.init() --- 초기화 진행 -------");
      try {
         Class.forName("com.webjjang.main.controller.Init");
      } catch (ClassNotFoundException e) {
         e.printStackTrace();
      }
   }
```
- **init 메서드**: 서블릿이 처음 생성될 때 한 번 실행되는 메서드입니다.
- **클래스 로드**: `Init` 클래스를 메모리에 로드하여 초기 설정을 수행합니다. 만약 클래스를 찾을 수 없으면 오류를 출력합니다.
- `System.out.println`: 초기화 과정을 콘솔에 출력합니다.

### 서비스 메서드

```java
   /**
    * @see HttpServlet#service(HttpServletRequest request, HttpServletResponse response)
    */
   protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
      System.out.println("DispatcherServlet.service()-----------------------");
      
      String uri = request.getRequestURI();
      System.out.println("uri = " + uri);
```
- **service 메서드**: 모든 HTTP 요청(GET, POST 등)을 처리하는 메서드입니다.
- **요청 URI 추출**: 사용자가 요청한 URL(URI)을 가져와 출력합니다. 예를 들어, 사용자가 `http://example.com/board/list`를 요청하면 `/board/list`가 URI가 됩니다.

```java
      int pos = uri.indexOf("/", 1);
      System.out.println("pos = " + pos);
      
      if(pos == -1) {
         request.getRequestDispatcher("/WEB-INF/views/error/404.jsp")
         .forward(request, response);
         return;
      }
```
- **슬래시 위치 찾기**: URI에서 첫 번째 슬래시 이후의 위치를 찾습니다. 예를 들어, `/board/list`에서 두 번째 슬래시의 위치는 6입니다.
- **404 오류 처리**: 만약 슬래시를 찾을 수 없으면(즉, 잘못된 URI 형식이라면), 404 오류 페이지로 요청을 포워딩합니다.

```java
      String module = uri.substring(0, pos);
      System.out.println("module = " + module);
```
- **모듈 추출**: URI의 첫 번째 슬래시부터 두 번째 슬래시까지의 문자열을 모듈로 정의합니다. 예를 들어, `/board/list`에서 모듈은 `/board`가 됩니다.

```java
      String jsp = null;
      
      switch (module) {
      case "/board":
         System.out.println("일반 게시판");
         jsp = boardController.execute(request);
         break;

      default:
         request.getRequestDispatcher("/WEB-INF/views/error/404.jsp")
         .forward(request, response);
         return;
      }
```
- **모듈에 따른 분기 처리**: 모듈이 `/board`인 경우, `boardController`의 `execute` 메서드를 호출하여 처리하고, 결과로 JSP 경로를 반환받습니다. 그 외의 모듈은 404 오류 페이지로 포워딩합니다.

```java
      if(jsp.indexOf("redirect:") == 0) {
         response.sendRedirect(jsp.substring("redirect:".length()));
      } else {
         request.getRequestDispatcher("/WEB-INF/views/" + jsp + ".jsp")
         .forward(request, response);
      }
   }
}
```
- **리디렉션 처리**: 반환된 JSP 경로가 `redirect:`로 시작하면, 해당 경로로 리디렉션(다른 URL로 이동)합니다.
- **포워딩 처리**: 그렇지 않으면, JSP 경로를 `/WEB-INF/views/` 디렉토리 아래의 JSP 파일로 포워딩(해당 페이지를 사용자에게 보여줌)합니다.

### 요약

이 코드는 사용자가 특정 URL을 요청했을 때, 해당 URL에 따라 적절한 컨트롤러를 호출하고 결과를 JSP 페이지로 포워딩하거나 리디렉션하는 기능을 담당합니다. 이를 통해 다양한 요청을 처리하고 적절한 응답을 제공하는 웹 애플리케이션을 만들 수 있습니다.
