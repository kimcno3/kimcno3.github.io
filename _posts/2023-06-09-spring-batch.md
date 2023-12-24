---
layout: post
title: Spring Batch
subheading:
categories: Spring
tags:  Spring
---

## 요구사항(문제점)
배치 코드가 Spring Batch로 구현되어 있었고 Spring Batch에 대한 전반적인 이해가 필요했습니다.

## Spring Batch
Spring Batch는 대량의 데이터를 처리하는 일괄 처리(Batch Processing) 작업을 구현하는데 사용되는 Spring 기반 프레임워크 
입니다. 일괄 처리 작업은 주로 데이터베이스 상의 대량 데이터를 읽어와 가공, 처리, 저장하는 과정을 말합니다. 이러한 작업은 
주기적이거나 일괄 처리 작업이 필요한 경우에 사용됩니다.

## Spring Batch 주요 개념
![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*fuBypL-YEcW_uZziJ2RRmg.png)

### Job Repository
작업의 상태와 실행 이력을 관리하는 역할을 수행합니다. 작업의 시작, 중지, 재시작 등을 관리하고, 작업 실행 로그를 저장합니다.
이미지로는 데이터를 저장하고 관리하는 데이터베이스 아이콘이나 로그 파일 등을 사용할 수 있습니다.

### Job
Spring Batch의 최상위 개념으로, 하나의 작업 단위를 나타내며 하나 이상의 Step으로 구성됩니다.

### Step
Job을 여러 단계로 나눈 것을 의미하며 각 Step은 일련의 처리를 수행하거나 입력 데이터를 읽어와 가공하고 결과 데이터를 저장하는 
등의 역할을 수행합니다.

### Item
일괄 처리 작업의 처리 대상이 되는 단위 데이터입니다. 예를 들어, 데이터베이스 테이블의 레코드, 파일의 라인 등이 Item이 될 수 
있습니다.

### Chunk
아이템을 한 번에 처리하는 단위를 말합니다. **Reader**가 아이템을 일정량씩 읽어오고, **Processor**가 그 아이템을 가공한 후,
**Writer**가 일정량씩 저장하는 과정을 반복합니다.

### Reader
데이터베이스 조회, 파일 읽기 등의 Item을 읽어오는 역할을 수행합니다. Spring Batch는 다양한 유형의 Reader를 제공합니다.

### Processor
읽어온 Item을 가공하는 역할을 수행합니다. 필요에 따라 Item을 변환, 유효성 검사, 비즈니스 로직 처리 등을 수행할 수 있습니다.

### Writer
가공된 Item을 저장소에 저장하는 역할을 수행합니다. 예를 들어 데이터베이스에 쓰기, 파일 쓰기 등을 Writer에서 처리합니다. 
Writer 또한 Spring Batch에서 다양한 유형을 제공합니다.

### Tasklet
일괄 처리 작업의 기본적인 처리 단위입니다. Tasklet은 단일한 작업 단위로, 특정한 작업을 수행하는 데 사용됩니다. 주로 비즈니스 
로직이나 반복적인 작업을 포함하고 있습니다.

> #### **참고: Tasklet 기반 배치 vs Chunk 기반 배치**
> ![](https://velog.velcdn.com/images%2Fgillog%2Fpost%2Fbf3040b5-5d35-457a-92fc-c7fbec7e0e96%2Fimage.png)
> 
> Tasklet 기반 배치는 하나의 덩어리로 작업을 처리하기 때문에 구현이 상대적으로 단순하고 작은 범위의 데이터를 처리할 때 적합합니다.
하지만 대용량 작업을 처리할 경우, 코드 구현이 더 복잡해질 수 있어(가독성이 좋지 못하다.) 적합하지 않습니다.
> 
> 이에 반해 Chunk 기반 배치는 chunk size 만큼 작업범위를 나눠서 처리가 가능하고 Reader & Processor & Writer로 나뉜 
역할에 따라 구현이 가능해 대용량 작업을 처리하는 로직에서 구현이 더 편리하고 안전합니다. 하지만 각 역할의 관계에 대한 이해가 
필요하단 점에서 Tasklet 기반 배치에 비해 진입장벽이 있는 편입니다.

## Spring Batch의 사용 목적
Spring Batch는 위와 같은 개념들을 활용하여 일괄 처리 작업을 간단하게 구현할 수 있는 방법을 제공합니다. 작업의 흐름을 선언적으로
설정하고, 필요한 리더, 프로세서, 라이터를 구성(또는 하나의 Tasket으로 구성)하여 작업을 수행합니다. Spring Batch의 장점은 
확장성과 안정성이 높으며, 실패한 작업을 롤백하고 재시작할 수 있는 기능을 제공한다는 것입니다.

## 참고자료

- [이미지 1](https://hello-woody.medium.com/2-spring-batch-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90-%EC%B6%94%EA%B0%80-908e848a6ebb)
- [이미지 2](https://velog.io/@gillog/Batch-Application-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0)
- [Job Repository](https://velog.io/@s2moon98/JobRepository%EC%99%80-%EB%A9%94%ED%83%80-%EB%8D%B0%EC%9D%B4%ED%84%B0)
