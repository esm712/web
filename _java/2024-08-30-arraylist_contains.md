---
title: "[Java] ArrayList의 contains 메소드에 관하여"
author: Lee Seung Min
date: 2024-08-30
category: java
layout: post
---
## 서론

먼저 이 글을 작성하게 된 이유에 대하여 말해보려고한다.

알고리즘에 대한 감각을 다시 끌어올리기위해 [숫자카드]([https://www.acmicpc.net/problem/10815](https://www.acmicpc.net/problem/10815))라는 문제를 풀었고있었다. 이 문제를 간략하게 설명하자면 특정 숫자가 특정 배열에 들어있는지 확인하면 되는 아주 간단한 문제이다.

이 문제를 푸는 방법은 사실 바이너리 서치를 사용하여 풀면 매우 간단하게 풀린다. 하지만 나는 “ArrayList의 contains 메소드는 내부적으로 어떻게 구성되어 있기에 이를 사용할 수 없을까?”라는 의문점을 가지고 이 글을 작성해보고자한다.

## ArrayList의 contains 메소드

```java
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, ...
{
    ...
    
    /**
     * Returns the index of the first occurrence of the specified element
     * in this list, or -1 if this list does not contain the element.
     * More formally, returns the lowest index {@code i} such that
     * {@code Objects.equals(o, get(i))},
     * or -1 if there is no such index.
     */
    public int indexOf(Object o) {
        return indexOfRange(o, 0, size);
    }

    int indexOfRange(Object o, int start, int end) {
        Object[] es = elementData;
        if (o == null) {
            for (int i = start; i < end; i++) {
                if (es[i] == null) {
                    return i;
                }
            }
        } else {
            for (int i = start; i < end; i++) {
                if (o.equals(es[i])) {
                    return i;
                }
            }
        }
        return -1;
    }
    ...
	  public boolean contains(Object o) {
        return indexOf(o) >= 0;
    }
    ...
    
}
```

ArrayList는 AbstarctList 클래스를 상속하고 List 인터페이스를 구현한다.

차근차근 소스코드를 봐보자.

1. contains 메소드에서 Object o를 parameter로 받고 인덱스확인(indexOf 메소드)하고 만약 인덱스가 0이상이라면 true를 반환하고 0미만이라면 false를 반환한다.
2. indexOf 메소드는 Object o를 parameter로 받고 indexOfRange 메소드에 0~ArrayList의 크기에서 o의 인덱스를 요청한다.
3. indexOfRange 메소드는 Object o, int start, int end를 parameter로 받고 elementdata(현재 ArrayList의 값들)을 가져오고 찾으려는 값을 **순차탐색**하여 그 인덱스를 반환하고 만약에 존재하지 않는다면 -1을 반환한다.

## 결론

“ArrayList의 contains 메소드는 내부적으로 어떻게 구성되어 있기에 이분탐색를 사용할 수 없을까?”라는 것의 답변은 “ArrayList에는 **정렬**되어있다는 조건이 없기 때문에 이분탐색을 사용할 수 없다.”이다.

추가적으로 ArrayList의 contains 메소드는 **순차탐색**한다.

다음 글에서는 AbstractCollection의 contains 메소드에 대하여 파해쳐보도록하겠다.

## 번외

ArrayList의 UML이 궁금하여 Intellij UML Plugin을 사용하여 그려보았다.

![ArrayList.png]({{site.baseurl}}/assets/java/ArrayList.png)