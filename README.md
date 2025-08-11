# Eureka_server


In a microservices ecosystem, Eureka Server acts as a service registry where all microservices register themselves upon startup. Each service runs on a different port (e.g., localhost:8081, localhost:8082, etc.) and includes the @EnableEurekaClient annotation along with Eureka client configurations in application.yml. Once registered, these services become visible on the Eureka dashboard, typically accessible at http://localhost:8761. To enable inter-service communication, we use Feign clients, which allow one service to call another using the registered service name instead of a hardcoded URL. For example, a service can call @FeignClient(name = "user-service") without knowing its actual port. To streamline external access and routing, we introduce an API Gateway (like Spring Cloud Gateway), which runs on a common port (e.g., localhost:8080) and acts as a single entry point to all services. The gateway uses route definitions to forward requests to the appropriate microservice based on the path, enabling centralized routing, load balancing, and even security. This architecture ensures loose coupling, scalability, and resilience across services.


so, we have restaurant-service and order-service both registered to eureka server, we can see that in the dashboard. 
As well as we have api-gateway, which routes to services via common port. 
