```
        docker run --name keycloak_dev -p 8180:8180 \
        -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
        quay.io/keycloak/keycloak:latest \
        start-dev --http-port=8180 
```

- Cơ bản Keycloak là một Open Source Identity và Access Management cho Modern Applications và Services. Dùng để quản lý nhận dạng và truy cập vào các ứng dụng/ dịch vụ. 
- [link tham khảo](https://huongdanjava.com/vi/keycloak)  
- [ 1 vài thuật ngữ trong keycloak ](https://viblo.asia/p/keycloack-loadbalancer-springboot-angular-L4x5xV91ZBM)
- Tính năng của Keycloak 
    - Hỗ trợ nhiều giao thức - OpenID Connect, OAuth 2.0 và SAML 2.0.
    - SSO
    - Bảng điều khiển dành cho quản trị viên
    - Danh tính Người dùng và Quyền truy cập
    - Đồng bộ hóa nguồn nhận dạng bên ngoài
    - Môi giới nhận dạng
    - Nhà cung cấp danh tính xã hội
    - Tùy chỉnh trang

## start Keycloak
- vào port đã chạy keycloak , tạo realm mới 
    - Realms : Một lĩnh vực quản lý một tập hợp User, Credential , Role và Group. Một người dùng thuộc về và đăng nhập vào một lĩnh vực. Các lĩnh vực không thể giao tiếp với nhau.

- [trong realm vửa tạo sẽ tạo 1 clients mới](https://huongdanjava.com/vi/them-moi-client-trong-keycloak.html) 
    - Clients : Client là các thực thể có thể yêu cầu Keycloak xác thực người dùng. Thông thường, client là các ứng dụng(application) và dịch vụ (service).

- auth-client => 
- springboot-keycloak => http://localhost:9090 

- tạo role : admin , user 
- tạo user : 
    - thuhang -> Credentials : set password ( 123456 ) -> role mapping : admin
    - thuhang2 -> 123456 -> user 

- vao setting realm -> OpenID Endpoint Configuration -> copy JSON "token_endpoint":
- vao postman -> paste link -> chon authozation -> Grant Type : password -> Access Token URL : paster tiep -> Client ID : name client (springboot-keycloak) -> scope : openid -> Client Authentication : .... Basic ... -> username + password da tao -> oki -> 2s sau click use token -> copy token -> vao web jwt.io -> paste token vao o Encoded 

## tao du an spring boot 
- trong du an thu muc resource tao file application.yml ( // properties)
- [link](https://www.keycloak.org/docs/latest/securing_apps/#_spring_security_adapter) -> them dependence keycloak , openApi , Jpa , mySql ,.. con fig properties (database) , aplication (openApi) 
- thao tac vs du an : [link](https://youtu.be/La082JsJoH4)

- SercurityConfig.java 
    - extends KeycloakWebSecurityConfigurerAdapter 
    - @KeycloakConfiguration
    - @EnableGlobalMethodSecurity(jsr250Enabled = true) [tham khao](https://techmaster.vn/posts/37238/gioi-thieu-spring-method-security)

- EmployeeController.java
    -     @RolesAllowed("admin")
    -     @RolesAllowed("user")
    - role ma minh da tao 

