# Servlet 
 ## Class diagram (add image) 
 
 
 Servlet 
 ```Java
 public interface Servlet {

    public void init(ServletConfig config) throws ServletException;

    public ServletConfig getServletConfig();

    public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException;

    public String getServletInfo();

    public void destroy();
}

 ```
 GenericServlet
  ```Java
public abstract class GenericServlet implements Servlet, ServletConfig, Serializable {
}
 ```
  HttpServlet
  ```Java
  public abstract class HttpServlet extends GenericServlet {
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) 
  protected void doPost(HttpServletRequest req, HttpServletResponse resp) 
  protected void doPut(HttpServletRequest req, HttpServletResponse resp) 
  protected void doDelete(HttpServletRequest req, HttpServletResponse resp) 
  }
  ```
  
  MyServlet.java
  ```java
  @WebServlet(name = "names", urlPatterns = {"/names"})
public class names extends HttpServlet {
    
    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    if(notLoggedIn()) {
        response.sendRedirect("/login");   //redirect to another serlet
        return;
    }
    
    // read header 
    String host = request.getHeader("host");
    
    //read parameter ?name=ali
    String name = req.getParameter("name");
    
    response.setContentType("text/xml");
    response.getWriter().println("hello world");
    
    }
}
  ```
  
  ## servlet Mapping 
  
  Web.xml
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
<web-app version="3.1" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd">
   
    <servlet>
        <servlet-name>home</servlet-name>
        <servlet-class>com.mansito.HelloServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>home</servlet-name>
        <url-pattern>*.do</url-pattern>         //any file ends with .do will go to home servlet
    </servlet-mapping>
    
    <servlet>
        <servlet-name>login</servlet-name>
        <servlet-class>com.mansito.LoginServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>login</servlet-name>
        <url-pattern>/login</url-pattern>
    </servlet-mapping>
  
   
</web-app>

  ```
  
  The values in the web deployment desriptor overrides the attributes values
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  