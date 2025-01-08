---
description: Support for Redis database instances
---

# Managed Redis

nholuongut supports Redis database instances. Redis stands for Remote Dictionary Server and is a fast, open-source, in-memory, key-value data store. Redis can function as a database, cache, message broker, and queue.

Redis delivers sub-millisecond response times, enabling millions of requests per second for real-time applications.

## Adding a Redis database instance

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Redis**.
2. Click **Add**. The **Add Redis Instance** page displays.

<div align="left">

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.15-12_22_23 (1).png" alt=""><figcaption><p><strong>Add Redis Instance</strong> page</p></figcaption></figure>

</div>

3. Enter the database **Name**.
4. In the **Display Name** field, enter a useful database name for reference.
5. From the **Tier** list box, select **Basic** for a Tier0 standalone instance; select **Standard** for a Tier1 High Availability primary/replica instance.
6. In the **Memory Size** field, enter memory size in gigabytes (GB).
7. In the **Redis Config** field, specify the Redis configuration.
8. In the **Labels** field, specify `key`/`value` pairs.
9. Select **Enable Auth and Security** to enable OSS Redis AUTH for the Redis instance.
10. Select Enable **Encryption-in-Transit** to select the TLS mode of the Redis instance.
11. Click **Create**. The Redis database **Details** tab displays on the **Redis** tab with **Connectivity**, **General**, and **Security** cards.

<div align="left">

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.15-12_26_37.png" alt=""><figcaption><p><strong>Details</strong> tab for a Redis database instance</p></figcaption></figure>

</div>
