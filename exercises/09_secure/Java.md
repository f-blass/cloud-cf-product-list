
## Step 4.1: Prerequisite
Make sure that you've imported the Product List sample application (Spring) as part of this [Exercise](/exercises/02_clone/README.md).
Within Eclipse IDE you should see the `product-list-java` project in the Project Explorer View.

* Build the project in Eclipse (`Context Menu -> Run As -> Maven install`) -> Result: **BUILD FAILURE**

> The build fails as the `ControllerTests` JUnit test expects that all `GET` endpoints of the Product-List are secured.  

## Step 4.2: Security configuration

The web.xml of the application must use auth-method with value XSUAA. This enables authentication of requests using incoming OAuth authentication tokens.

```xml
<web-app>
<display-name>Products App</display-name>
  <login-config> 
    <auth-method>XSUAA</auth-method>
  </login-config> 
</web-app> 
```

In the Java coding, use the @ServletSecurity annotations:
```java
package com.sap.cp.cf.demoapps;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.ServletSecurity;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.annotation.HttpConstraint;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.google.gson.Gson;

@WebServlet({ "/products/*", "/productsByParam" })
// configure servlet to check against scope "$XSAPPNAME.read"
@ServletSecurity(@HttpConstraint(rolesAllowed = { "read" }))
public class Controller extends HttpServlet {

	private static final long serialVersionUID = 1L;
	private Gson gson = new Gson();
	private ProductService productService = new ProductService();
	private static final Logger logger = LoggerFactory.getLogger(Controller.class);

	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

		String productsJson;
		if (request.getParameter("name") != null) {
			String name = request.getParameter("name");
			logger.info("***First - Retrieving details for '{}'.", name);
			logger.info("***Second - Retrieving details for '{}'.", name);
			productsJson = this.gson.toJson(productService.getProductByName(name));

		} else {
			productsJson = this.gson.toJson(productService.getProducts());
		}

		response.setContentType("application/json");
		PrintWriter out = response.getWriter();
		out.print(productsJson);
		out.flush();

	}
}
```

Now all endpoints are blocked.


## Step 4.3: Build the Project
* Build the project in Eclipse (`Context Menu -> Run As -> Maven install`) -> Result: **BUILD SUCCESS**
  * Or, alternatively build the project on the console with the following commands:
    ```
    D:
    cd D:\Files\Session\SEC364\cloud-cf-product-list-sample-teched2019\samples\java
    mvn clean install
    ```
* Finally, make sure that the folder `D:\Files\Session\SEC364\cloud-cf-product-list-sample-teched2019\samples\java\target` contains a `product-list.war` file. 

