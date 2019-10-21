---
layout: post
title:  Pandas timestamp error - OutOfBoundsDatetime
date: 2019-07-10 15:10:00
description: Pandas timestamp OutOfBoundsDatetime error
categories: [pandas, python]
---

### Error: OutOfBoundsDatetime
```python
pandas.tslib.OutOfBoundsDatetime: Out of bounds nanosecond timestamp: 2819-01-10 00:00:00
```

Pandas version that I've used: 

```python
import pandas as pd
pd.__version__
'0.23.4'
```
## Overview
While I was performing some timeseries analysis, I tried pandas's pd.DataFrame.to_datatime() method to convert a column of timestamps from "str" to "datetime" and I've come across this error message "Error: OutOfBoundsDatetime". My dataset had some typos in timestamps and some timestamps had the following years - ***2818, 2808, 2919, 2909*** instead of ***2018, 2008, 2019, 2009***

However the maximum timestamp YEAR supported by pandas is 2262 for a 64-bit integer (see below).

## Reason
Pandas timestamp has a limitation. Here is the official documentation notes:
```
Since pandas represents timestamps in nanosecond resolution, 
the time span that can be represented using a 64-bit integer is limited to approximately 584 years:

In [92]: pd.Timestamp.min
Out[92]: Timestamp('1677-09-21 00:12:43.145225')

In [93]: pd.Timestamp.max
Out[93]: Timestamp('2262-04-11 23:47:16.854775807')
```

### Resolution
Resolved my issues by fixing the typo values with correct years.

[Pandas documentation link](https://pandas-docs.github.io/pandas-docs-travis/user_guide/timeseries.html#timestamp-limitations)

