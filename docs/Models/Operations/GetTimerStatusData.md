# GetTimerStatusData


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        | Example                                                            |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `isRunning`                                                        | *bool*                                                             | :heavy_check_mark:                                                 | Whether there is currently a running timer                         | true                                                               |
| `currentEntry`                                                     | [Operations\CurrentEntry](../../Models/Operations/CurrentEntry.md) | :heavy_check_mark:                                                 | Current running timer details, null if not running                 |                                                                    |
| `elapsedTime`                                                      | *float*                                                            | :heavy_check_mark:                                                 | Elapsed time in seconds for the current running timer              | 1800                                                               |