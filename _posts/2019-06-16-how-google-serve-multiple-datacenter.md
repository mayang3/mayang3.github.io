---
title: "How google serve multiple data center"
tag:
- google
- architecture
- multiple data center
categories:
- architecture
---

## Transactions Across Data Centers
회사에서 Global IDC 간의 동기화/트랜잭션 처리가 필요해서 이것저것 찾아보다가 발견한 영상이다.

Google I/O 2009 에서 소개된 영상인데, Google App Engine DataStore 팀의 Ryan Barret 이라는 분이 발표한 영상이다.

어떤 솔루션을 제공한다기 보다는 Multiple Data Center 간의 트랜잭션을 설정할때 고려해야될 요소와 개념들을 잘 설명해주고 있고,

특히 구성에 따라, Master/Slave, Master/Master, 2PC, Paxos 등의 모델의 장/단점 등을 일목요연하게 정리해두었는데 이 부분이 매우 좋았다.

최초 Multiple Data Center 간의 Transaction 에 대해 어떻게 접근해야 될지 방향이 잡히지 않을때 한 번 들어보고 topic 들을 정리하기 좋았던 영상이다.

[![Transactions Across Data Centers](http://img.youtube.com/vi/srOgpXECblk/0.jpg)](https://youtu.be/srOgpXECblk)

발표 내용 요약은 [이 사이트](http://highscalability.com/blog/2009/8/24/how-google-serves-data-from-multiple-datacenters.html)에 잘 정리되어 있다.


