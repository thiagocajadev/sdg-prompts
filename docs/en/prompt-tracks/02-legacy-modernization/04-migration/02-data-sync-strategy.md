# 02 - Data Sync and Load Strategy

## Synchronization Model (Sync)

- Will data need to be synchronized in real-time between the Legacy and New systems? Or will there be an asynchronous maintenance window (e.g., Midnight Batch)?
- Will the synchronization flow be Unidirectional (Legacy -> New) or Bidirectional (updates in one reflect in the other)?

## ETL Track (Extract, Transform, Load)

- Which tool or script will ensure the conversion of old data (e.g., a formatted string `"1"`) to the new typing in the database (pure _Boolean_)?
- Will there be a mirror table or _Read-replica_ to offload the main legacy database during migration?

## Rollback and Legacy Disposal

- What are the criteria and estimated timeframe for safely "switching off" the old database after the new one becomes operational?
- How will an emergency rollback re-synchronize data that had already been persisted only in the modern database?

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 02 - Data Synchronization

## Sync Model

We'll keep writing to the new API and hope the legacy system doesn't need to read it.

## ETL Track

Copy MySQL data using a Python script at the end of the day.
```

> **Rationale**: How does the operation remain online while the Python script runs freely? If the script fails halfway through, we break both databases simultaneously.

### ✅ Good Example

```markdown
# 02 - Data Synchronization

## Sync Model

- **Continuous Bidirectional**: We will use Debezium (CDC - Change Data Capture) to listen for changes from MongoDB (Legacy) to PostgreSQL (New) via Kafka. The user microservice will trigger the reverse via the Legacy API in the callback.

## ETL Track

- **Clean Load Batch**: Heavy historical migrations will be done at 03:00 AM (Sunday) using optimized routines via AWS Glue, mapping obsolete columns to `.jsonb`.

## Disposal

- **Shadow DB Period**: The old database will run in _Read-Only_ mode for 14 days post-migration. If PostgreSQL breaks irreversibly, we use a reverse Glue script and flip the router switch back to MongoDB.
```

> **Rationale**: Fault-tolerant approach. Based on the industrial CDC model (real-time events), drastically reducing inconsistencies for users of the mixed system.
