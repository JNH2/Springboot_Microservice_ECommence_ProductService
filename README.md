🚀 Product Microservice: Enterprise Persistence Layer
🚀 產品微服務：企業級持久化層

🇨🇭 Project Context | 項目背景
This microservice is the foundational Product Management Module for a scalable e-commerce ecosystem. It is engineered to meet standards of software excellence, prioritizing architectural decoupling, type safety, and standardized API responses.
本項目是可擴展電商生態系統中的核心產品管理模組。開發過程嚴格遵循軟體工程標準，優先考慮架構解耦、類型安全（Type Safety）以及標準化的 API 響應規範。

🛠️ Tech Stack | 技術棧
 * Framework: Spring Boot 2.7.3 (Enterprise stability).
 * Persistence: Spring Data JPA / Hibernate.
 * Database: MySQL 8.0 (Containerized via Docker).
 * Patterns: DTO Pattern, Builder Pattern, and Global Exception Handling.
 * 框架: Spring Boot 2.7.3（確保企業級穩定性）。
 * 持久化: Spring Data JPA / Hibernate。
 * 資料庫: MySQL 8.0（透過 Docker 容器化部署）。
 * 設計模式: DTO 模式、Builder 模式以及全域異常處理。
 * 
⚠️ Challenges & Solutions | 挑戰與解決方案
1. Architectural Decoupling (DTO Pattern) | 架構解耦 (DTO 模式)
 * Challenge: Preventing internal DB schemas from leaking to the API layer.
 * Solution: Implemented ProductRequest and ProductResponse DTOs to abstract the Product entity.
 * 挑戰: 防止資料庫實體（Entity）結構直接暴露於 API 層，導致架構耦合。
 * 解決方案: 實作 ProductRequest 與 ProductResponse 作為數據傳輸物件（DTO），將 Product 實體抽象化。
2. Dependency Management | 依賴管理
 * Challenge: Runtime incompatibility between Java 11 and Spring Boot 3.x.
 * Solution: Performed a strategic downgrade to Spring Boot 2.7.3 and migrated namespaces to javax.
 * 挑戰: Java 11 環境與 Spring Boot 3.x 之間的運行時不相容問題。
 * 解決方案: 策略性降級至 Spring Boot 2.7.3，並將命名空間遷移回 javax 以確保穩定。
3. Security Filter Chain Configuration | 安全過濾鏈配置
 * Challenge: Default security configurations blocking API testing (401 Unauthorized).
 * Solution: Excluded SecurityAutoConfiguration during development to streamline integration testing.
 * 挑戰: Spring Security 預設配置攔截了 API 測試請求，導致 401 錯誤。
 * 解決方案: 在開發階段排除 SecurityAutoConfiguration，以加速集成測試流程。
   
💻 Technical Operations | 技術操作
Infrastructure (Docker) | 基礎設施
# Provision MySQL Instance | 啟動 MySQL 實例
docker run --name mysql-product-service -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=springbootdb -p 3306:3306 -d mysql:8.0

# Shell Access | 進入資料庫終端
docker exec -it mysql-product-service mysql -u root -p

Build & Run | 構建與運行
# Execute application skipping tests | 跳過測試運行程式
mvn clean spring-boot:run -DskipTests

📅 Future Roadmap | 未來規劃
The next phase involves implementing Service Discovery via Netflix Eureka to enable dynamic registration of ProductService and OrderService within the cluster.
下一階段將透過 Netflix Eureka 實作服務發現機制，實現集群中 ProductService 與 OrderService 的動態註冊。
> Note: Postman test results and database screenshots (verifying 200 OK and data persistence) are available in the project documentation folder.
> 註: Postman 測試結果與數據庫截圖（驗證 200 OK 與數據持久化）已上傳至項目文檔文件夾中。

