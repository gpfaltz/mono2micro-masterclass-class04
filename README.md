# mono2micro-masterclass-c-lass04
Monolithic Applcation to Micro Services Applications - Class 04/05

Main Objective: Implement Health Check (Liveness and Readiness), and Fault Tolerance Functions on Micro Apps
@Fallback and @CircuitBreaker Annotations

Pre requistes:
JAVA 21 Installed
Docker  Installed

Quarkus Extensions Used on Project:
RestEasy Reactive - quarkus-resteasy
RestEasy Reactive JSON-B - quarkus-resteasy-jsonb
Hibernate ORM - quarkus-hibernate-orm3
Hibernate ORM with Panache - quarkus-hibernate-orm-panache
JDBC Driver - PostgreSQL - quarkus-jdbc-postgresql
Lombok - 1.18.36 - org.projectlombok
RestEasy Reactive Client - quarkus-resteasy-client
RestEasy Reactive Client JSON-B - quarkus-resteasy-client-jsonb
SmallRye Health - quarkus-smallrye-health
SmallRye Fault Tolerance - quarkus-smallrye-fault-tolerance

Check Docker Containers:
docker ps

#################Testing Micro Flight Application ###################

Starting Application:
./mvnw quarkus:dev
./mvnw clean quarkus:dev

Checking Quarkus User Interface:
http://localhost:8081/q/dev-ui/

Checking Quarkus Healh Check:
http://localhost:8081/q/health
http://localhost:8081/q/health/live
http://localhost:8081/q/health/ready


List Flights:
curl localhost:8081/flight

Find Flight
curl localhost:8081/flight/findById?id=1
curl localhost:8081/flight/findByTravelOrderId?travelOrderId=1

#################Testing Micro Hotel Application ###################

Starting Application:
./mvnw quarkus:dev
./mvnw clean quarkus:dev

Checking Quarkus User Interface:
http://localhost:8082/q/dev-ui/

Checking Quarkus Healh Check:
http://localhost:8082/q/health
http://localhost:8082/q/health/live
http://localhost:8082/q/health/ready


List Hotels:
curl localhost:8082/hotel

Find Flight
curl localhost:8082/hotel/findById?id=1
curl localhost:8082/hotel/findByTravelOrderId?travelOrderId=1

#################Testing Micro TravelOrder Application ###################

Starting Application:
./mvnw quarkus:dev
./mvnw clean quarkus:dev

Checking Quarkus User Interface:
http://localhost:8083/q/dev-ui/

Checking Quarkus Healh Check:
http://localhost:8083/q/health
http://localhost:8083/q/health/live
http://localhost:8083/q/health/ready


List Travel Orders:
curl localhost:8083/travelorder

Create Travel Order:
curl -d "{\"sourceAirport\": \"GRU\", \"destinyAirport\": \"GIG\", \"nights\": \"5\"}" -H "Content-Type: application/json" http://localhost:8083/travelorder
curl -d "{\"sourceAirport\": \"GRU\", \"destinyAirport\": \"SDU\", \"nights\": \"10\"}" -H "Content-Type: application/json" http://localhost:8083/travelorder
curl -d "{\"sourceAirport\": \"GRU\", \"destinyAirport\": \"CWB\", \"nights\": \"15\"}" -H "Content-Type: application/json" http://localhost:8083/travelorder
curl -d "{\"sourceAirport\": \"GRU\", \"destinyAirport\": \"FLN\", \"nights\": \"20\"}" -H "Content-Type: application/json" http://localhost:8083/travelorder
curl -d "{\"sourceAirport\": \"GRU\", \"destinyAirport\": \"POA\", \"nights\": \"25\"}" -H "Content-Type: application/json" http://localhost:8083/travelorder

Find Travel Order:
curl localhost:8083/travelorder/findById?id=1

Testing Circuit Breaker:
while true; do curl localhost:8083/travelorder; sleep .3; done

