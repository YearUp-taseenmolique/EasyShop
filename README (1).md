
# Easy Shop

This project is the backend for an e-commerce application called EasyShop. The front-end was provided, and the backend functionalities were developed and debugged. The application enables managing categories, products, and user roles while following RESTful API conventions. It also integrates role-based access control to ensure secure operations.











## Features

## Phase 1: Categories Controller

Goal:
- Implement the CategoriesController class to manage product categories.
- Ensure role-based access control to restrict category creation, updates, and deletion to administrators

Work Done:
1. CategoriesController:
- Added appropriate RESTful annotations (@GetMapping, @PostMapping, @PutMapping, @DeleteMapping) for category management endpoints.
- Implemented methods to handle CRUD (Create, Read, Update, and Delete) operations and categories.
- Restricted insert, update, and delete operations to users with the role of Admin using @PreAuthorze annotations.

2. MySqlCategoryDao:
- Implemented database interaction logic for CRUD operations.
- Methods Implemented
    - getAllCategories: Fetch all categories from the database.
    - getById: Fetch a category by its ID.
    - create: Add a new category 
    - update: Modify an existing category.
    - delete: Remove a category by its ID.
- Ensured error handling and SQL query execution.

## Phase 2: Bug fixes

Bug 1: Product Search Incorrect Results
- Fixed the filter logic in the MySqlProductDao class to ensure accurate results.
- Correctly mapped query parameters (Category, Price Range, Color) to SQL statements.

Bug 2: Product Duplication During updates
- Identified the issue where updates to products were inserting new rows instead of modifying existing ones.
- Updated the ProductController's updateProduct method:
    - Replaced the create call with the correct update method in the DAO.
    - Ensured the update method in MySqlProductDao modifies the record instead of inserting a new one.
    


## Testing and Validation

## - Users created for Testing:
- Admin: Administrator with permissions to manage categories and products.
- user: Standard user with read-only access.
- george: Another standard user for testing purposes.

## - Used Postman to:
- test API endpoints for categories and products.
- Validate role-based accesscontrol for restricted operations.
- Simulate various query parameters for product search and confirm results.

## - Verified successful fixes for reported bugs.
## Technologies Used
- Language: Java
- Framework: Spring Boot
- Database: MySQL
- Testing tool: Postman
- Build Tool: Maven
## API Endpoints
## Categories Controller

1. Get all Categories
- Get /api/Categories
- Public endpoint to retreive all Categories

2. Get Category by ID
- Get /api/categories/{id}
- Public endpoint to retrieve a category by its ID

3. Create Category
- POST /api/categories
- Restricted to admin role.
- Request Body: { "name": "", "description": "" }

4. Update Category
- PUT /api/categories/{id}
- Restricted to admin role.
- Request Body: { "name": "", "description": "" }

5. Delete Category
- DELETE /api/categories/{id}
- Restricted to admin role.

## ProductController

1. Search Products
- GET /api/products/search
- Query Parameters: category, minPrice, maxPrice, color, etc.

2. Update Product
- PUT /api/products/{id}
- Restricted to admin role.
## Project Structure

Easy-Shop/
├── .idea/                              # IDE configuration folder (for IntelliJ IDEA)
├── database/                           # Database-related files
│   └── src/
│       └── main/
│           └── java/
│               └── com/
│                   └── org/
│                       └── yearup/
│                           ├── configurations/         # Configuration classes
│                           │   └── DatabaseConfig.java  # Database configuration
│                           ├── controllers/            # API controllers
│                           │   ├── AuthenticationController.java
│                           │   ├── CategoriesController.java
│                           │   ├── ProductsController.java
│                           │   └── ShoppingCartController.java
│                           ├── data/                    # Data-related classes
│                           │   ├── mysql/               # MySQL-specific DAO classes
│                           │   │   ├── MySqlCategoryDao.java
│                           │   │   ├── MySqlDaoBase.java
│                           │   │   ├── MySqlProductDao.java
│                           │   │   ├── MySqlProfileDao.java
│                           │   │   └── MySqlUserDao.java
│                           │   ├── CategoryDao.java      # Category DAO interface
│                           │   ├── ProductDao.java       # Product DAO interface
│                           │   ├── ProfileDao.java       # Profile DAO interface
│                           │   ├── ShoppingCartDao.java  # Shopping Cart DAO interface
│                           │   └── UserDao.java          # User DAO interface
│                           ├── models/                  # Data models
│                           │   ├── authentication/      # Authentication-related models
│                           │   │   ├── Authority.java
│                           │   │   ├── LoginDto.java
│                           │   │   ├── LoginResponseDto.java
│                           │   │   └── RegisterUserDto.java
│                           │   ├── Category.java         # Category model
│                           │   ├── Product.java          # Product model
│                           │   ├── Profile.java          # Profile model
│                           │   ├── ShoppingCart.java     # Shopping Cart model
│                           │   ├── ShoppingCartItem.java # Shopping Cart Item model
│                           │   └── User.java             # User model
│                           ├── security/                # Security-related classes
│                           │   ├── jwt/                 # JWT authentication classes
│                           │   │   ├── JWTConfigurer.java
│                           │   │   ├── JWTFilter.java
│                           │   │   └── TokenProvider.java
│                           │   ├── JwtAccessDeniedHandler.java
│                           │   ├── JwtAuthenticationEntryPoint.java
│                           │   ├── SecurityUtils.java
│                           │   ├── UserModelDetailsService.java
│                           │   ├── UserNotActivatedException.java
│                           │   └── WebSecurityConfig.java
│                           └── EasyshopApplication.java  # Main application entry point
├── resources/                         # Configuration files and static resources
├── test/                               # Test classes
├── target/                             # Compiled classes and build output
├── .gitignore                          # Git ignore configuration
├── pom.xml                             # Maven project configuration file
└── README.md                           # Project description and documentation

