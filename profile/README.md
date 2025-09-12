<p align="center">
    <a href="https://doppar.com" target="_blank">
        <img src="https://raw.githubusercontent.com/doppar/doppar/7138fb0e72cd55256769be6947df3ac48c300700/public/logo.png" width="400">
    </a>
</p>

<p align="center">
<a href="https://github.com/doppar/framework/actions/workflows/tests.yml"><img src="https://github.com/doppar/framework/actions/workflows/tests.yml/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/doppar/framework"><img src="https://img.shields.io/packagist/dt/doppar/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/doppar/framework"><img src="https://img.shields.io/packagist/v/doppar/framework" alt="Latest Stable Version"></a>
<a href="https://github.com/doppar/framework/blob/main/LICENSE"><img src="https://img.shields.io/github/license/doppar/framework" alt="License"></a>
</p>

## Why Doppar?

Doppar is engineered for speed. With minimal reliance on third-party libraries and most features built directly into the core, you get lightning-fast performance right out of the box. No unnecessary bloat—just clean, efficient execution. Doppar ORM Built entirely from core with zero external dependencies, Doppar delivers a powerful and expressive ORM system. Manage complex relationships with ease—no third-party packages required. Whether you're a seasoned PHP developer or just diving in, Doppar makes it easy to build powerful applications quickly and cleanly.

We just put Doppar to the test under some serious load — and the results are in:

### Benchmark: Doppar vs Laravel Performance Test

**Objective:** Compare request handling and latency between Doppar and Laravel under high concurrency with a database-backed endpoint.

- **Load:** 50,000 requests
- **Concurrency:** 1,000 simultaneous requests
- **Endpoint:** `/tags` (database-backed endpoint to fetch `tags`)
- **Tool:** ApacheBench (ab)
- **Metrics Measured:** Requests per second, median/percentile latency, max latency, response size, failed requests

| Metric              | **Doppar**       | **Laravel**        | **Factor**        |
| ------------------- | ---------------- | ------------------ | ----------------- |
| **Total Requests**  | 50,000           | 50,000             | 1×                |
| **Failed Requests** | 0                | 0                  | 1×                |
| **Requests/sec**    | **318.5 req/s**  | **43.9 req/s**     | \~7.3×            |
| **Median Latency**  | \~2.7s (2703 ms) | \~22.2s (22180 ms) | \~8.2× faster     |
| **95th Percentile** | \~4.8s           | \~34.9s            | \~7.3× faster     |
| **Max Latency**     | \~7.9s           | \~40.2s            | \~5.1× faster     |
| **Response Size**   | 1083 bytes       | 4346 bytes         | \~0.25× (smaller) |

Doppar sustained `~7x higher` throughput than Laravel (318 vs 44 req/s). Doppar is `~8x faster` under 1000 concurrent requests. Doppar stayed under 3s median latency and delivered stable high throughput, making it far more suitable for high-concurrency, database-heavy workloads.

Under high-concurrency, database-backed scenarios, Doppar significantly outperforms Laravel in raw speed, latency, and efficiency. This makes Doppar a strong choice for applications requiring high throughput and low response times. Doppar isn’t just a `new PHP framework` — it outperforms PHP's popular framework by nearly an order of magnitude in concurrency + DB tests.

- **Simplicity with Power** Intuitive architecture that stays out of your way.
- **Feature-Based Development** Organize your application by features, not layers.
- **Just-in-Time (JIT)** Advanced JIT compilation for the Blade template engine.
- **Performance First** Lightweight and efficient, designed for speed without compromise.
- **Scalable & Modular** Perfect for projects of all sizes—from microservices to full-scale.
- **API Presenter Bundle** Fully internal, zero-config API Presenter. no overrides required.
- **Two-Factor Authentication (TOTP)** Industry-standard TOTP Authentication.
- **Rich Ecosystem** Eloquent ORM, Routing, Middleware, Pool Console, Caching and more.
- **Developer-Focused** Simplifies development with thoughtful conventions.

## Contributing

Thank you for considering contributing to the Doppar framework! The contribution guide can be found in the [Doppar documentation](https://doppar.com/versions/3.x/contributions.html).

## Code of Conduct

In order to ensure that the Doppar community is welcoming to all, please review and abide by the [Code of Conduct](https://doppar.com/versions/3.x/contributions.html#code-of-conduct).

## Security Vulnerabilities

Please review [our security policy](https://github.com/doppar/framework/security/policy) on how to report security vulnerabilities.

## License

The Doppar framework is open-sourced software licensed under the [MIT license](LICENSE.md).
