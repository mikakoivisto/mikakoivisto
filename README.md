# Mika Koivisto

Creator of [Vertique](https://vertique.dev). Hands-on solution architect, 25 years in software, the last nine in payments and banking. I design the system, write the code, and run it in production. Kauniainen, Finland.

[Website](https://mikakoivisto.fi) · [Resume](https://mikakoivisto.fi/resume) · [LinkedIn](https://www.linkedin.com/in/mikakoivisto) · [X](https://x.com/mikakoivisto)

## Vertique

A Java 21+ framework on Vert.x for APIs, durable workflows, and background jobs. The interface is the whole contract:

```java
@ServiceContract(namespace = "shop", value = "pricing")
public interface PricingService {

    @Resilient(policy = "pricing")
    @Timeout(2_000)
    @Retry(maxRetries = 2, delayMs = 50)
    @CircuitBreaker(maxFailures = 5)
    Future<Quote> quote(QuoteRequest request);
}
```

Vertique generates the wiring at compile time, dispatches over the event bus with the request context, and enforces the timeout, retries, and breaker. Workflow state and outbox messages live in PostgreSQL, in the same transaction as your data. Your implementation is just the pricing.

- [vertiquehq/vertique](https://github.com/vertiquehq/vertique): the open-core framework, v0.2.0, EUPL-1.2
- [vertiquehq/vertique-skills](https://github.com/vertiquehq/vertique-skills): agent skills that answer Vertique questions from the module versions your project uses

Before Vertique, I co-created a shared Vert.x toolkit (JAX-RS, OpenAPI router, resilience patterns) that a bank's teams adopted across their projects.

## Background

Nine years consulting for a large Nordic financial group as lead developer and hands-on architect, designing regulated payment and API systems that process millions of payments a month, and operating them in production with continuous delivery.

Before that, 2009 to 2016 on Liferay's platform team, where I designed and built the SAML 2.0 identity and service provider that still ships in the product, and consulted for Bosch, Vodafone, Barclays, and IBM. Earlier, lead architect and pre-sales at Logica (now CGI).

These days I work AI-native: agents write a lot of the code, and I own the specs, the architecture, and the review.
