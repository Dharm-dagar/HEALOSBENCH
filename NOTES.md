# HEALOSBENCH Eval Harness Notes

## Strategy Comparison

1. **zero_shot**: Direct prompt with schema. Fast but may fail complex normalizations.
2. **few_shot**: Added examples to handle formatting. More stable.
3. **cot**: Step-by-step reasoning. Best for nested structures and catching edge cases but higher cost.

## Observations
- Schema validation retry loops significantly reduce parsing errors compared to one-shot.
- F1 Set matching is critical for medications to avoid penalizing order differences.
- Prompt caching (ephemeral) works effectively for the system prompt.

## Implementation Details
- Used Anthropic Tool Use for robust JSON enforcement.
- Implemented `p-limit` for concurrency and rate limits.
- Resumability handled via SQLite/Postgres run hashing.

## Future Improvements
- Cross-model evaluations (e.g. Sonnet 4.6).
- UI diff for prompt regressions.
