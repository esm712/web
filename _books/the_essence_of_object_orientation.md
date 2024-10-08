---
title: 객체지향의 사실과 오해
author: Seung Min
date: 2024-08-01
category: book
layout: post
---

**[객체지향의 사실과 오해(저자: 조영호)][1]{:target="\_blank"}**라는 책을 읽고 정리 및 [나][2]{:target="\_blank"}의 생각을 챕터별로 작성하고자한다.

## Chatper 1. 협력하는 객체들의 공동체

- 객체지향의 목표는 새로운 세계를 창조하는 것이다.
- 객체지향의 가장 중요한 개념은 역할, 책임, 협력이다.
- 역할은 책임의 의미를 내포하고 있다.
- 객체는 상태와 행동을 가진다.
- 객체는 객체끼리 협력적이어야하고 자율적인 존재여야한다.
- 객체가 객체에게 요청을 하는 것을 메시지라고한다.
- 객체가 객체의 요청을 처리하는 방법을 메소드라고한다.
- 객체지향의 핵심은 적절한 책임을 수행하는 역할간의 유연하고 견고한 협력관계를 구축하는 것이다.

## Chapter 2. 이상한 나라의 객체

> ##### 객체지향 설계 팁
>
> 애플리케이션에 필요한 협력을 생각하고 협력에 참여하는데 필요한 행동을 생각한 후 행동을 수행할 객체를 선택한다.
{: .block-tip }

- **객체**란 식별가능한 개체 또는 사물이다. 객체는 구별가능한 **식별자**, 특징적인 **행동**, 변경 가능한 **상태**를 가진다. 소프트웨어 안에서 객체는 저장된 상태와 실행 가능한 코드를 통해 구현된다.
- **상태**는 특정 시점에 객체가 가지고 있는 정보의 집합으로 객체의 구조적 특징을 표현한다. 객체의 상태는 **정적 프로퍼티**와 **동적 프로퍼티**로 구성된다. 객체의 프로퍼티는 단순한 **값**과 다른 객체를 참조하는 **링크**로 구분할 수 있다.
- **행동**은 외부의 요청이나 수신된 메시지에 응답하기 위해 동작하고 반응하는 활동이다. 행동의 결과로 객체는 자신의 상태를 변경하거나 다른 객체에게 메시지를 전달할 수 있다. 객체는 행동을 통해 다른 객체와의 협력에 참여하므로 행동은 외부에 가시적이어야한다.
- **식별자**는 어떤 객체를 다른 객체와 구분하는 데 사용하는 객체의 프로퍼티이다. 값은 식별자를 가지지 않기 때문에 상태를 이용한 동등성 검사를 통해 두 인스턴스를 비교해야한다. 객체는 상태가 변경될 수 있기 때문에 식별자를 이용한 동일성 검사를 통해 두 인스턴스를 비교할 수 있다.
- **명령(Command)**란 객체의 상태를 변경하는 작업을 말하고 **쿼리(Query)**란 객체의 상태를 조회하는 작업을 말한다.
- 행동이 상태를 결정한다.
- **의인화(anthropomorphism)**란 현실의 객체보다 더 많은 일을 할 수 있는 소프트웨어 객체의 특징이다.


## Chapter 3. 타입과 추상화

- **추상화**란 어떤 양상, 세부 사항, 구조를 좀 더 명확하게 이해하기 위해 특정 절차나 물체를 의도적으로 생략하거나 감춤으로써 복잡도를 극복하는 방법이다.

> ##### 추상화 방법
> 1. 구체적인 사물들 간의 공통점은 취하고 차이점은 버리는 일반화를 통해 단순하게 만든다.
> 2. 중요한 부분을 강조하기 위해 불필요한 세부 사항을 제거함으로써 단순하게 만든다.
{: .block-tip}

- **객체**란 특정한 개념을 적용할 수 있는 구체적인 사물이다.
- **개념의 인스턴스**란 **개념**이 적용된 객체이다.
- **타입**이란 개념과 동일하며, 우리가 인식하고 있는 다양한 사물이나 객체에 적용할 수 있는 아이디어나 관념을 의미한다.
- **타입**은 데이터가 어떻게 사용되냐에 관한 것이다.
- 타입에 속한 데이터는 메모리에 어떻게 표현하는지 외부로부터 철저하게 감춰진다.
- **데이터 타입**은 메모리 안에 저장된 데이터의 종류를 분류하는 데 사용하는 메모리 집합에 관한 메타데이터이다.
- 어떤 객체가 어떤 타입에 속할지 결정하는 것은 객체가 수행하는 **행동**이다.
- 객체의 내부적인 표현은 외부로부터 철저하게 감춰진다.(캡슐화)
- **다형성**이란 동일한 요청에 대해 서로 다른 방식으로 응답할 수 있는 능력을 뜻한다.
- 일반적인 타입(슈퍼타입)은 특수한 타입(서브타입)에 비해 더 적은 수의 행동을 가지지만 더 큰 외연 집합을 가진다.
- 결국 타입은 추상화이다.
- 동적 모델(dynamic model): 실제로 객체가 살아있는 동안 상태가 어떻게 변하고 행동하는지를 포착하는 것
- 정적 모델(static model): 객체가 가질 수 있는 모든 상태와 모든 행동을 시간에 독립적으로 표현하는 것
- **타입**은 **객체를 분류하는 기준**이며, **타입을 나누는 기준**은 **객체가 수행하는 행동**이다.
- **클래스**는 단지 타입을 구현할 수 있는 여러가지 방법 중 하나

[1]: https://m.yes24.com/Goods/Detail/18249021
[2]: https://github.com/esm712
