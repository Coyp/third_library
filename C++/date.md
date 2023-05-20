# daylight saving 

标准时间（EST）为UTC-5，夏令时间（EDT）为UTC-4  

美国夏令时规则:  
1. 在3月第二个周日凌晨2AM（当地时间）开始，将时钟调到3点，拨快1小时，俗称“Spring Forward 1 Hour"  -> 2-3 不存在
2. 在11月第一个周日凌晨2AM（当地时间）夏令时结束，要将时钟调到1点，拨慢1小时，俗称“Fall Back 1 Hour”  -> 1-2 重复

# local time 

local time to sys time maybe throw 2 errors 
1. local_info::ambiguous

```c

auto zt = make_zoned("America/New_York", local_days{Sunday[1]/November/2016} + 1h + 30min);

Which outputs:
2016-11-06 01:30:00 is ambiguous.  It could be
2016-11-06 01:30:00 EDT == 2016-11-06 05:30:00 UTC or
2016-11-06 01:30:00 EST == 2016-11-06 06:30:00 UTC
```

2. local_info::nonexistent

```c
auto zt = make_zoned("America/New_York", local_days{Sunday[2]/March/2016} + 2h + 30min);

Which outputs:
2016-03-13 02:30:00 is in a gap between
2016-03-13 02:00:00 EST and
2016-03-13 03:00:00 EDT which are both equivalent to
2016-03-13 07:00:00 UTC
```
