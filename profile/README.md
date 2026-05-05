<p align="center">
  <img src="https://raw.githubusercontent.com/doppar/.github/main/logo.svg" width="540">
</p>

<p align="center">
<a href="https://github.com/doppar/framework/actions/workflows/tests.yml"><img src="https://github.com/doppar/framework/actions/workflows/tests.yml/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/doppar/framework"><img src="https://img.shields.io/packagist/dt/doppar/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/doppar/framework"><img src="https://img.shields.io/packagist/v/doppar/framework" alt="Latest Stable Version"></a>
<a href="https://github.com/doppar/framework/blob/main/LICENSE"><img src="https://img.shields.io/github/license/doppar/framework" alt="License"></a>
<a href="https://packagist.org/packages/doppar/framework"><img src="https://img.shields.io/packagist/php-v/doppar/framework" alt="PHP Version"></a>
<a href="https://github.com/doppar/framework/stargazers"><img src="https://img.shields.io/github/stars/doppar/framework?style=flat" alt="GitHub Stars"></a>
<a href="https://github.com/doppar/framework/network/members"><img src="https://img.shields.io/github/forks/doppar/framework?style=flat" alt="GitHub Forks"></a>
<a href="https://github.com/doppar/framework/issues"><img src="https://img.shields.io/github/issues/doppar/framework" alt="GitHub Issues"></a>
<a href="https://github.com/doppar/framework/graphs/contributors"><img src="https://img.shields.io/github/contributors/doppar/framework" alt="Contributors"></a>
<a href="https://github.com/doppar/framework/commits/main"><img src="https://img.shields.io/github/last-commit/doppar/framework" alt="Last Commit"></a>
<a href="https://github.com/doppar/framework"><img src="https://img.shields.io/github/repo-size/doppar/framework" alt="Repo Size"></a>
</p>

## [Why Doppar?](https://doppar.com/versions/3.x/getting-started)

As developers, we continually strive for harmony in our craft — a balance between elegance and performance. Often, we find one at the cost of the other: elegant syntax that slows us down, or high performance wrapped in complexity.

Doppar brings both worlds together. It offers aristocratic elegance in syntax and uncompromising performance under the hood — a framework designed for developers who value both beauty and speed.

If you are building systems that demand real scalability, high concurrency, and reliable performance, Doppar is ready to power them.

## Benchmark Snapshot

Doppar is designed to feel expressive without giving away raw
throughput. To give that claim some concrete shape, here is a simple
real-world benchmark from a local Doppar application running on
**Nginx + PHP-FPM + PHP 8.5** with `wrk` on **Ubuntu 22**.

The benchmark target was intentionally small and easy to reason about:
the `/` endpoint returning a single record from SQLite.

```php
#[Route(uri: '/', name: 'home')]
public function welcome()
{
    return User::find(1);
}
```

### Benchmark Environment

This benchmark was run with the following setup:

- web server: `nginx`
- PHP runtime: `PHP 8.5`
- process manager: `php-fpm`
- database: `SQLite`
- load generator: `wrk` on `Ubuntu 22`
- benchmark route: `/`
- benchmark behavior: fetch `User::find(1)` and return the model

### Benchmark Commands

The following `wrk` commands were used:

```bash
wrk -t2 -c50 -d20s http://localhost
wrk -t4 -c200 -d30s http://localhost
wrk -t8 -c500 -d60s http://localhost
```

### Benchmark Results

Here is the measured output summary:

| Threads | Connections | Duration | Avg Latency | Requests/sec | Transfer/sec | Notes |
|---------|-------------|----------|-------------|--------------|--------------|-------|
| `2`     | `50`        | `20s`    | `24.16ms`   | `2066.98`    | `1.23MB/s`   | Stable baseline |
| `4`     | `200`       | `30s`    | `94.76ms`   | `2103.41`    | `1.25MB/s`   | Best throughput in this run |
| `8`     | `500`       | `60s`    | `252.25ms`  | `1959.45`    | `1.17MB/s`   | Saturation starts to show |

### Benchmark Highlights

These three cards make the run easier to scan at a glance before
reading the detailed interpretation.

<img width="665" height="236" alt="image" src="https://github.com/user-attachments/assets/b813a90a-a407-4e5b-94d3-518d25c1ad0e" />

### Latency Visualization

As expected, latency rose as concurrency increased.

<img width="672" height="265" alt="image" src="https://github.com/user-attachments/assets/60b4f859-5db7-486e-ba42-451bcb133ddc" />

### What This Result Shows

This benchmark is not meant to be a synthetic "hello world" victory
lap. The endpoint still enters the framework, resolves routing, touches
SQLite through the ORM, and returns a real model response.

Even with that full request path, Doppar sustained roughly **2,000
requests per second** on this setup. The most balanced run in this set
was:

- `4` threads
- `200` connections
- `30` seconds
- `2103.41` requests/sec
- `94.76ms` average latency

At the highest concurrency profile, throughput remained strong but the
system began to show pressure through higher latency and `604` socket
read errors. That is a useful signal: the benchmark did not collapse,
but it did reveal where this particular machine and stack started to
push beyond a comfortable steady state.

### How To Read These Numbers

Benchmarks always depend on workload, hardware, web server tuning,
database choice, opcode cache settings, and what the endpoint is
actually doing. A JSON API, a rendered view, a cache hit, and a complex
join-heavy query will all produce different numbers.

So treat this as a baseline snapshot of Doppar under a real but narrow
workload:

- a real HTTP request
- a real ORM lookup
- a real SQLite-backed response
- a standard `nginx + php-fpm` deployment shape

That baseline is encouraging because it shows Doppar can stay expressive
and still deliver strong request throughput on a straightforward PHP
stack.

## Ecosystem
- [AI](https://doppar.com/versions/3.x/doppar-ai)
- [Queue](https://doppar.com/versions/3.x/doppar-queue)
- [Airbend](https://doppar.com/versions/3.x/doppar-airbend)
- [Insight](https://doppar.com/versions/3.x/doppar-insight)
- [Flarion](https://doppar.com/versions/3.x/doppar-flarion)
- [Notifier](https://doppar.com/versions/3.x/doppar-notifier)
- [Orion](https://doppar.com/versions/3.x/doppar-orion)
- [Guard](https://doppar.com/versions/3.x/doppar-guard)
- [Axios](https://doppar.com/versions/3.x/doppar-axios)
- [OAuthic](https://doppar.com/versions/3.x/doppar-oauthic)
- [Bloom](https://doppar.com/versions/3.x/doppar-bloom)
- [Twig Bridge](https://doppar.com/versions/3.x/doppar-twig-bridge)

## Learn
Welcome to the official learning hub for the Doppar PHP Framework. Here you will find easy-to-follow tutorials, practical examples, and beginner-friendly guides designed to help you master Doppar.
[Watch Tutorial](https://www.youtube.com/@doppar-3x)
