# PES-VCS Lab Report

## Student Details

- Name: Harsh Pandya
- SRN: PES1UG24CS182
- Repository: https://github.com/Seaweed-Boi/os-u4-orange-problem
- Date: 2026-04-20

## Work Completed So Far

### Phase 1: Object Storage Foundation

Completed implementation in [object.c](object.c):

- Implemented object_write:
  - Builds object payload as type + size + null separator + data.
  - Computes SHA-256 on full payload (header + data).
  - Supports deduplication by returning success when object already exists.
  - Creates sharded object directory if required.
  - Uses temp file + fsync + rename for atomic durable writes.
  - fsyncs shard directory after rename.
- Implemented object_read:
  - Reads full object file from path derived from hash.
  - Verifies integrity by recomputing hash and matching expected ObjectID.
  - Parses header safely (type and length).
  - Validates declared length with actual payload length.
  - Returns parsed type and extracted payload.

### Phase 1 Validation

Commands run:

```bash
make clean && make all && ./test_objects
```

Observed result summary:

- PASS: blob storage
- PASS: deduplication
- PASS: integrity check
- All Phase 1 tests passed

### Screenshot 1A (Required)

Output of test_objects with passing checks:

![Screenshot 1A](screenshots/1a.png)

### Screenshot 1B (Required)

Object store sharded structure from .pes/objects:

![Screenshot 1B](screenshots/1b.png)

## Progress Checklist

| Phase | Item | Status |
| --- | --- | --- |
| 1 | object.c (object_write, object_read) | Completed |
| 1 | Screenshot 1A | Added |
| 1 | Screenshot 1B | Added |
| 2 | tree.c | Pending |
| 3 | index.c | Pending |
| 4 | commit.c | Pending |

| Final | Integration test evidence | Pending |



## Notes

- This report currently includes completed work up to Phase 1 (object storage) and screenshots 1A/1B.

- Remaining implementation phases will be appended as work progresses.

