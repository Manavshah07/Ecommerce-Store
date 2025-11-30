# Ecommerce Store

## Project flow (how this application works)

1. **Landing / Browse**

   * Visitor opens the index page and sees featured products, categories, and search.
   * Products can be filtered by category and searched by name/keyword.

2. **User registration & authentication**

   * New users register with email and password. A verification / password-reset mechanism can be configured via mail sender.
   * Registered users log in. Spring Security handles authentication and role-based access (USER, ADMIN).

3. **User actions (after login)**

   * Browse product listings and view product details (single product page).
   * Add products to the shopping cart and update quantities.
   * Place an order (checkout flow uses stored user details and cart contents).
   * View order history and profile information.

4. **Admin actions**

   * Admin dashboard provides management UIs for Categories, Products, and Users.
   * Admin can add / edit / delete categories and products, including uploading product images and setting discounts.
   * Admin can manage users (enable/disable accounts) and view statistics / lists.

5. **Persistence & services**

   * Spring Data JPA repositories persist entities (User, Product, Category, Order, etc.) to MySQL.
   * A service layer contains business logic and sits between controllers and repositories.

6. **Security & Roles**

   * Spring Security secures routes; certain endpoints / pages are restricted to ADMIN role.
   * Passwords should be stored hashed (project uses Spring Security’s encoding mechanism).

7. **Deployment**

   * The project can be packaged as a WAR to deploy on a servlet container (e.g. Tomcat) or run as a standalone Spring Boot application.

---

## Features included in this project

* Clean Spring Boot MVC architecture (Controller → Service → Repository).
* Thymeleaf server-side templating for all front-end pages.
* User registration, login, logout, and role-based authorization.
* Admin dashboard for managing categories, products, and users.
* Product listing and single-product detail pages.
* Shopping cart functionality (add/update/remove items).
* Order creation (basic checkout flow) and order listing for users.
* Product image upload handling (store images in filesystem or DB – configured in code).
* Search and pagination for product / category listings (jQuery DataTables used in admin lists).
* MySQL persistence using Spring Data JPA and custom JPA finder methods.
* Email capability via JavaMailSender (used for password reset flows if configured).
* Lombok to reduce boilerplate code (getters/setters, constructors).
* Maven build lifecycle and packaging (WAR/JAR).

---

## Technology stack

* Java (project targeted to Java 17; adjust if needed)
* Spring Boot
* Spring MVC, Spring Security
* Spring Data JPA (Hibernate)
* Thymeleaf
* MySQL
* Maven
* jQuery & DataTables on the frontend
* Lombok
* (Optional) Apache Tomcat for WAR deployment

---


## Quick setup & run (local development)

> These steps assume you already cloned the repository into a local folder.

1. **Clone the repo**

```bash
git clone https://github.com/Manavshah07/Ecommerce-Store
cd Ecommerce_Store
```

2. **Create a MySQL database**

Open MySQL and create a database (example name `ecommerce_store`):

```sql
CREATE DATABASE ecommerce_store;
```

3. **Configure application properties**

Open `src/main/resources/application.properties` (or `application.yml`) and set your DB credentials and other environment-specific settings, for example:

```
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_store
spring.datasource.username=YOUR_DB_USER
spring.datasource.password=YOUR_DB_PASSWORD
spring.jpa.hibernate.ddl-auto=update
# mail and other properties (optional)
# spring.mail.host=
# spring.mail.username=
# spring.mail.password=
```

4. **Build and run**

Run with Maven (embedded container):

```bash
mvn clean package
# then either
mvn spring-boot:run
# or run the generated jar/war
java -jar target/<artifact-name>.jar
```

If you prefer WAR deployment, copy the generated WAR from `target/` into your Tomcat `webapps/` directory and start Tomcat.

5. **Access the app**

Open your browser at `http://localhost:8080` (or whichever port is configured).

---



