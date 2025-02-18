---
pcx_content_type: changelog
title: Changelog
weight: 11
rss: file
---

# Changelog

## 2023-07-27

### Time Travel

[Time Travel](/d1/learning/time-travel/) is now available. Time Travel allows you to restore a D1 database back to any minute within the last 30 days (Workers Paid plan) or 7 days (Workers Free plan), at no additional cost for storage or restore operations.

Refer to the [Time Travel](/d1/learning/time-travel/) documentation to learn how to travel backwards in time.

Databases using D1's [new storage subsystem](https://blog.cloudflare.com/d1-turning-it-up-to-11/) can use Time Travel. Time Travel replaces the [snapshot-based backups](/d1/learning/backups/) used for legacy alpha databases.

## 2023-06-16

### Generated columns documentation

We've published new documentation describing how to use D1's support for [generated columns](/d1/learning/generated-columns/) to define columns that are dynamically generated on write (or read). Generated columns allow you to extract data from [JSON objects](/d1/learning/querying-json/) or use the output of other SQL functions.

## 2023-06-28

### Metrics and analytics

You can now view [per-database metrics](/d1/platform/metrics-analytics/) via both the [Cloudflare dashboard](https://dash.cloudflare.com/) and the [GraphQL Analytics API](/analytics/graphql-api/).

D1 currently exposes read & writes per second, query response size, and query latency percentiles.

## 2023-06-12

### Deprecating Error.cause

As of [`wrangler v3.1.1`](https://github.com/cloudflare/workers-sdk/releases/tag/wrangler%403.1.1) the [D1 client API](/d1/platform/client-api/) now returns [detailed error messages](/d1/platform/client-api/#errors) within the top-level `Error.message` property, and no longer requires developers to inspect the `Error.cause.message` property.

To facilitate a transition from the previous `Error.cause` behaviour, detailed error messages will continue to be populated within `Error.cause` as well as the top-level `Error` object until approximately July 14th, 2023. Future versions of both `wrangler` and the D1 client API will no longer populate `Error.cause` after this date.

## 2023-05-19

### New experimental backend

D1 has a new experimental storage back end that dramatically improves query throughput, latency and reliability. The experimental back end will become the default back end in the near future. To create a database using the experimental backend, use `wrangler` and set the `--experimental-backend` flag when creating a database: 

```sh
$ wrangler d1 create your-database --experimental-backend
```

Read more about the experimental back end in the [announcement blog](https://blog.cloudflare.com/d1-turning-it-up-to-11/).

### Location hints

You can now provide a [location hint](/d1/learning/data-location/) when creating a D1 database, which will influence where the leader (writer) is located. By default, D1 will automatically create your database in a location close to where you issued the request to create a database. In most cases this allows D1 to choose the optimal location for your database on your behalf.

## 2023-05-17

### Query JSON

[New documentation](/d1/learning/querying-json/) has been published that covers D1's extensive JSON function support. JSON functions allow you to parse, query and modify JSON directly from your SQL queries, reducing the number of round trips to your database, or data queried.
