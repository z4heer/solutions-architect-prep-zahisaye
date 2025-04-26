# 🛠️ API Rate Limiting Strategies in Spring Boot

API rate limiting is a crucial technique for ensuring that a web service doesn't get overwhelmed by too many requests. Rate limiting helps maintain system stability, prevents abuse, and ensures fair usage. In this document, we will explore various strategies for implementing rate limiting in Spring Boot applications.

---

## 🚦 Rate Limiting Strategies

1. **Fixed Window Rate Limiting**
    - In this strategy, the number of requests is limited within a fixed time window (e.g., per minute or per hour).
    - If the number of requests exceeds the limit within the window, the API returns a rate-limiting error (e.g., HTTP 429).

2. **Sliding Window Rate Limiting**
    - Similar to fixed window rate limiting, but the window "slides" over time.
    - It is more flexible than fixed window rate limiting because it doesn’t reset every fixed interval.

3. **Token Bucket Rate Limiting**
    - Tokens are added to a bucket at a fixed rate, and each request requires a token.
    - If there are no tokens left in the bucket, the request is denied.
    - The bucket refills over time at a defined rate, allowing burst traffic.

4. **Leaky Bucket Rate Limiting**
    - The leaky bucket is similar to the token bucket but with a fixed "leak" rate.
    - Requests are processed at a constant rate, and excess requests are queued or discarded.

---

## ⚙️ Key Components of Rate Limiting in Spring Boot

- **Redis for Distributed Rate Limiting**  
  Redis is commonly used for distributed rate limiting because it provides a fast, in-memory data store that allows multiple services to share the same rate-limiting information.

- **RateLimiter**  
  Spring has a RateLimiter API to handle rate-limiting, often used in combination with caching or distributed systems like Redis.

- **Throttling and Delay**  
  API calls are delayed or throttled if the rate limit has been exceeded, preventing the system from crashing and allowing for smoother operation under heavy load.

---

## 🧠 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Rate Limiting** | The process of controlling the amount of incoming requests to an API to prevent overloading. |
| **Token Bucket** | A rate-limiting algorithm where tokens are added at a fixed rate, and each request consumes one token. If there are no tokens, requests are denied. |
| **Leaky Bucket** | A rate-limiting algorithm where requests are handled at a fixed rate, and excess requests are either queued or discarded. |
| **Fixed Window** | A rate-limiting strategy where requests are allowed within a fixed time window (e.g., per minute). Once the window is full, new requests are rejected. |
| **Sliding Window** | A variation of the fixed window, where the window "slides" over time, allowing for a smoother rate-limiting experience. |
| **Redis** | An in-memory data structure store, often used for distributed caching and rate limiting due to its speed and scalability. |
| **API Throttling** | The process of slowing down the rate of requests when the system is overloaded to prevent service degradation. |

---

## 🔐 Implementing Rate Limiting in Spring Boot

### Example: Token Bucket Algorithm with Redis

1. **Add Dependencies in `pom.xml`**
    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-redis</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    ```

2. **Configure Redis Connection**
    ```java
    @Configuration
    public class RedisConfig {

        @Bean
        public JedisConnectionFactory connectionFactory() {
            JedisConnectionFactory factory = new JedisConnectionFactory();
            factory.setHostName("localhost");
            factory.setPort(6379);
            return factory;
        }

        @Bean
        public RedisTemplate<String, String> redisTemplate() {
            RedisTemplate<String, String> template = new RedisTemplate<>();
            template.setConnectionFactory(connectionFactory());
            return template;
        }
    }
    ```

3. **Rate Limiting Logic**
    ```java
    @Service
    public class RateLimiterService {

        private static final int MAX_TOKENS = 10;
        private static final int REFILL_RATE = 1; // tokens per second

        @Autowired
        private RedisTemplate<String, String> redisTemplate;

        public boolean isRequestAllowed(String userId) {
            String key = "rate_limit_" + userId;
            Long currentTokens = redisTemplate.opsForValue().get(key);
            
            if (currentTokens == null) {
                redisTemplate.opsForValue().set(key, String.valueOf(MAX_TOKENS), 1, TimeUnit.MINUTES);
                return true;
            }
            
            if (currentTokens < 1) {
                return false;
            }

            redisTemplate.opsForValue().increment(key, -1);
            return true;
        }
    }
    ```

4. **Rate Limiting Interceptor**
    ```java
    @Component
    public class RateLimitInterceptor implements HandlerInterceptor {

        @Autowired
        private RateLimiterService rateLimiterService;

        @Override
        public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
            String userId = request.getRemoteAddr();
            
            if (!rateLimiterService.isRequestAllowed(userId)) {
                response.setStatus(HttpStatus.TOO_MANY_REQUESTS.value());
                response.getWriter().write("Rate limit exceeded");
                return false;
            }
            return true;
        }
    }
    ```

5. **Register Interceptor**
    ```java
    @Configuration
    public class WebConfig implements WebMvcConfigurer {

        @Autowired
        private RateLimitInterceptor rateLimitInterceptor;

        @Override
        public void addInterceptors(InterceptorRegistry registry) {
            registry.addInterceptor(rateLimitInterceptor).addPathPatterns("/api/**");
        }
    }
    ```

---

## 🔎 Common Interview Questions

- What is the difference between Token Bucket and Leaky Bucket algorithms in rate limiting?
- Why is Redis commonly used for distributed rate limiting?
- How do you handle API rate limiting for a large-scale distributed system?
- Can you explain the Sliding Window strategy in rate limiting and when it is useful?
- How would you implement rate limiting in a microservices architecture with multiple instances?

---

## 🚀 Best Practices for Rate Limiting

- **Granularity**: Implement rate limiting at different granularities (e.g., user level, IP level, endpoint level) depending on use cases.
- **Response Headers**: Return rate-limit headers (`X-Rate-Limit`, `X-Rate-Limit-Remaining`, etc.) to inform clients of their rate limit status.
- **Distributed Caching**: Use Redis or other distributed caches to handle rate limiting in distributed systems.
- **Graceful Degradation**: Implement fallback strategies for clients when rate limits are exceeded, such as retry-after headers or limited access to critical endpoints.

---

## 🔗 Extras

- [API Rate Limiting - Wikipedia](https://en.wikipedia.org/wiki/Rate_limiting)
- [Rate Limiting in Distributed Systems](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781449373320/)
- [Spring Boot Rate Limiting with Redis](https://www.baeldung.com/spring-boot/rate-limiting-with-redis)
