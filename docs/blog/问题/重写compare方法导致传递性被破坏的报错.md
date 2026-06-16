问题代码
```java
            Collections.sort(travelUserList, new Comparator<TravelUserList>() {
                @Override
                public int compare(travelUserList o1, travelUserList o2) {
                    String travelUser1 = o1.getTravelUser();
                    String travelUser2 = o2.getTravelUser();
                    ZonedDateTime travelStartDate1 = o1.getTravelStartDate();
                    ZonedDateTime travelStartDate2 = o2.getTravelStartDate();
                    if (travelUser1 != null && travelUser2 != null && travelStartDate1 != null
                            && travelStartDate2 != null) {
                        int compare = travelUser1.compareTo(travelUser2);
                        if (compare != 0) {
                            return compare;
                        }
                        return travelStartDate1.compareTo(travelStartDate2);
                    }
                    return 0;
                }
            });
```
报错场景      
张三     2026-05-22T00:00+08:00[Asia/Shanghai]  
张三     2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
李四   2026-05-22T00:00+08:00[Asia/Shanghai]
李四   2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
王五   2026-05-22T00:00+08:00[Asia/Shanghai]
王五   2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
朱八   2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
薛六     2026-05-22T00:00+08:00[Asia/Shanghai]
薛六     2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
张三     2026-05-22T00:00+08:00[Asia/Shanghai]
张三     2026-05-25T00:00+08:00[Asia/Shanghai]
张三     2026-05-25T00:00+08:00[Asia/Shanghai]
张三     2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
杨七    2026-05-22T00:00+08:00[Asia/Shanghai]
杨七    2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
李九     2026-05-22T00:00+08:00[Asia/Shanghai]
李九     2026-05-22T00:00+08:00[Asia/Shanghai]
李九     2026-05-25T00:00+08:00[Asia/Shanghai]
李九     2026-05-25T00:00+08:00[Asia/Shanghai]
唐十     2026-05-22T00:00+08:00[Asia/Shanghai]
唐十     2026-05-25T00:00+08:00[Asia/Shanghai]
唐十     2026-05-22T00:00+08:00[Asia/Shanghai]
唐十     2026-05-25T00:00+08:00[Asia/Shanghai]
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
null    2026-05-25T00:00+08:00[Asia/Shanghai] 
朱八     2026-05-22T00:00+08:00[Asia/Shanghai]
杨七    2026-05-25T00:00+08:00[Asia/Shanghai]
刘十一     2026-05-22T00:00+08:00[Asia/Shanghai]
刘十一     2026-05-24T00:00+08:00[Asia/Shanghai]
土军     2026-06-02T00:00+08:00[Asia/Shanghai]

问题原因
违反了传递性原则

解决方案

