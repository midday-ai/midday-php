# ListTrackerEntriesMeta

Metadata about the tracker entries response including totals and date range


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      | Example                                                          |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `totalDuration`                                                  | *float*                                                          | :heavy_check_mark:                                               | Total duration of all tracker entries in the response in seconds | 86400                                                            |
| `totalAmount`                                                    | *float*                                                          | :heavy_check_mark:                                               | Total monetary amount for all tracker entries in the response    | 1800                                                             |
| `from`                                                           | *string*                                                         | :heavy_check_mark:                                               | Start date of the queried range in YYYY-MM-DD format             | 2024-04-01                                                       |
| `to`                                                             | *string*                                                         | :heavy_check_mark:                                               | End date of the queried range in YYYY-MM-DD format               | 2024-04-30                                                       |