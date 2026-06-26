# Casino-DB-Pipeline

An automated SQLite backend data pipeline for player loyalty segmentation, live high-roller alerts, and scheduled database optimization on a cruise line gaming floor.

## Business Scenario

Managing data operations on a modern cruise ship casino requires efficient, automated background processing to conserve satellite bandwidth and keep live dashboards running quickly.

## System Architecture

![System Architecture](/docs/Casino-DB-Pipeline.png)

## Solutions Implemented

### 1. On-Demand Player Profiling

* **Objective**: Allows VIP casino hosts to instantly pull a breakdown of customer tiers.

### 2. High-Roller Intercept Guard

* **Objective**: Instantly logs high-dollar transactions into a security table.

### 3. Automated Storage Performance Purge

* **Objective**: Frees up indexing overhead by purging zero-revenue slots.

## Business Intelligence & Core Analytics

![Player Tier Distribution](/docs/tier_distribution_chart.png)

### High-Roller Security Dispatch Protocol

Matches automated security triggers back to the core passenger ledger:

```sql
SELECT 
    v.alert_id,
    p.player_name,
    v.large_wager,
    v.alert_status,
    v.alert_timestamp
FROM vip_alerts v
INNER JOIN player_activity p 
    ON v.player_id = p.player_id;