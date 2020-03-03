---
title: Release History of Pegasus
layout: releases
show_sidebar: false
toc: false
content-toc: true
content-toc-title: Releases
---

# Release Notes of v1.12.1 (Latest)

This is a patch release. We strongly recommend you to upgrade to this version instead of using v1.12.0.

## What's new in this version

- fix: fix log bug in fmt logging (XiaoMi/rdsn#346)
- feat: optimize tcmalloc release memory (XiaoMi/rdsn#343)
- feat: update config for tcmalloc release memory optimization (#433)
- feat: add a interface to get perf-counters info of all partitions of all apps (#417)
- feat(collector): add statistics for estimate key number of partition (#435)

## Upgrade from the previous version

```ini
[replication]
- mem_release_interval_ms
+ mem_release_check_interval_ms = 3600000
+ mem_release_max_reserved_mem_percentage = 10
```

# Release Notes of v1.12.0

Release page on Github: <https://github.com/XiaoMi/pegasus/releases/tag/v1.12.0>

The following are the highlights in this release:

## HTTP Support

We exposed many metadata of a Pegasus cluster and some system states of a Pegasus server through HTTP interfaces. Thanks to @Skysheepwang.

Related PR: [XiaoMi/rdsn#280](https://github.com/XiaoMi/rdsn/pull/280), [#360](https://github.com/XiaoMi/pegasus/pull/360), [XiaoMi/rdsn#321](https://github.com/XiaoMi/rdsn/pull/321), [XiaoMi/rdsn#296](https://github.com/XiaoMi/rdsn/pull/296)

Related Docs: <https://pegasus-kv.github.io/api/http>

## Multi-tenant Support

In XiaoMi as our user base grows, improvements on our multi-tenant support become increasingly needed for stability. For example, we lack monitoring support for table-level latency (only server-level latency). When a table is observed unreasonably slow, we need to refine our slow query mechanism in order to dynamically configure the "slow" threshold per table without system reboot. Another requirement is to support size-based write throttling to reduce the influence of a high-throughput-low-QPS table to other tables in the same cluster.

Related PR: [XiaoMi/rdsn#314](https://github.com/XiaoMi/rdsn/pull/314), [XiaoMi/rdsn#298](https://github.com/XiaoMi/rdsn/pull/298), [#400](https://github.com/XiaoMi/pegasus/pull/400), [XiaoMi/rdsn#336](https://github.com/XiaoMi/rdsn/pull/336), [XiaoMi/rdsn#340](https://github.com/XiaoMi/rdsn/pull/340)

Docs on table-level latency: TBD

Docs on table-level slow query: TBD

Docs on size-based throttling: TBD

## Prometheus Support

Pegasus is continuously lowering our access costs for community users. In this release, we provide our experimental support on Promentheus, thanks to @ChenQShmily.

Related PR: [XiaoMi/rdsn#287](https://github.com/XiaoMi/rdsn/pull/287), [XiaoMi/rdsn#284](https://github.com/XiaoMi/rdsn/pull/284), [#397](https://github.com/XiaoMi/pegasus/pull/397), [#368](https://github.com/XiaoMi/pegasus/pull/368)

Related Docs: TBD

## CPU Profiling Support

Thanks to @linlinhaohao888.

Related PR: [XiaoMi/rdsn#290](https://github.com/XiaoMi/rdsn/pull/290)

Related Docs: TBD

## Bug Fixes

- fix: meta unnecessary assert [XiaoMi/rdsn#332](https://github.com/XiaoMi/rdsn/pull/332)
- fix(coldbackup): delay clean request when chkpting [XiaoMi/rdsn#327](https://github.com/XiaoMi/rdsn/pull/327)

## Upgrade from the previous version

No configuration update is needed in this release.

For table-level latency, some new perf-counters are added. Every read/write operation to a table has  two perf-counters (p99&p999) for latency.

```txt
replica*eon.replica*table.level.RPC_RRDB_RRDB_PUT.latency(ns)@${for.each.table}
replica*eon.replica*table.level.RPC_RRDB_RRDB_PUT.latency(ns)@${for.each.table}.p999
replica*eon.replica*table.level.RPC_RRDB_RRDB_GET.latency(ns)@${for.each.table}
replica*eon.replica*table.level.RPC_RRDB_RRDB_GET.latency(ns)@${for.each.table}.p999
```

# Release Notes of v1.11.6

Release page on Github: <https://github.com/XiaoMi/pegasus/releases/tag/v1.11.6>

<button class="button release-button" data-target="#modal_v1_11_6">Released at 26/8/2019</button>

# Release Notes of v1.11.5

Release page on Github: <https://github.com/XiaoMi/pegasus/releases/tag/v1.11.5>

<button class="button release-button" data-target="#modal_v1_11_5">Released at 24/6/2019</button>

# Release Notes of v1.11.4

Release page on Github: <https://github.com/XiaoMi/pegasus/releases/tag/v1.11.4>

<button class="button release-button" data-target="#modal_v1_11_4">Released at 10/6/2019</button>

# Other Releases

For earlier releases, please refer to <https://github.com/XiaoMi/pegasus/releases>.
