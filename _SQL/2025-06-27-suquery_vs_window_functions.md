---
title: "[SQL] Sub Query vs Window Functions"
author: Lee Seung Min
date: 2025-06-27
category: SQL
layout: post
---
## 서론

먼저 이 글을 작성하게 된 이유에 대하여 말해보려고한다.

회사에서 일을하던 도중에 원가내역등록 테이블의 가장 최신의 원가내역을 얻어내고자 하였다.   
예를 들어보자면 A라는 테이블에서 col1(pk), col2(pk), col3(pk)가 있다.
A: 원가내역 테이블
col1: 원가 번호
col2: 아이템 번호
col3: revision

```SQL
SELECT *
    FROM 
	(
        SELECT *,
               ROW_NUMBER() OVER (PARTITION BY CS_ITEM,CS_NUM ORDER BY REV_NO DESC) AS RN
        FROM SOD310T
    ) A
    WHERE RN = 1;
```

```SQL
SELECT *
	FROM SOD310T A
	WHERE REV_NO = (
		SELECT MAX(REV_NO)
		FROM SOD310T
		WHERE CS_ITEM = A.CS_ITEM AND CS_NUM = A.CS_NUM
	)
```


## 본론

## 결론
