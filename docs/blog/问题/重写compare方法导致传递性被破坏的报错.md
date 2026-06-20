---
title: 重写compare方法导致传递性被破坏的报错
createTime: 2026/06/20 10:46:06
permalink: /blog/ndnyeolr/
---
问题代码
```java
            Collections.sort(userList, new Comparator<UserList>() {
                @Override
                public int compare(userList o1, userList o2) {
                    String user1 = o1.getUser();
                    String user2 = o2.getlUser();
                    ZonedDateTime createDate1 = o1.getCreateDate();
                    ZonedDateTime createDate2 = o2.getCreateDate();
                    if (user1 != null && user2 != null && createDate1 != null
                            && createDate2 != null) {
                        int compare = user1.compareTo(user2);
                        if (compare != 0) {
                            return compare;
                        }
                        return createDate1.compareTo(createDate2);
                    }
                    return 0;
                }
            });
```
报错场景
问题原因
违反了传递性原则

解决方案

