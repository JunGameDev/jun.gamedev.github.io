---
title: 'Static Class vs Singleton'
date: 2021-04-23 02:36:00
category: 'C#'
draft: false
---

# 🔷 <b>요약</b>
C#에는 Top Level Class에서도 정적 클래스 선언이 가능하다. 정적 클래스란 일반적인 클래스와 동일 하지만, 인스턴스화 할 수 없다는 차이점이 존재한다. <br> 정적클래스는 프로그램 내에서 단 하나만 존재할 수 있다는 특징이 있다. 이걸 들었을때 싱글톤이 떠오를 것이다. <br>
둘 다 프로그램내에서 단 한 객체만이 존재할 수 있는데, 그렇다면 정적 클래스는 싱글톤을 대체할 수 있을까? <br><br>
아래에 정적 클래스와 싱글톤의 비슷한 점과 차이점을 간단히 정리해보았다.

<br>

# 🔷 <b> 비슷한 점</b>
- 싱글톤, 정적 클래스 둘다 단 하나의 인스턴스 카피만 프로그램의 메모리 상에 존재할 수 있다.
- 두 가지 모두 쓰레드-세이프하게 구현이 가능하다.
- 정적 변수나 클래스들은 스택 메모리에 저장되지 않는다.<br>**High-Frequency Heap** 이라는 Heap 메모리의 특별한 구역에 저장된다. <br> 이 구역에 저장된 메모리는 합당한 프로세스나 앱 도메인이 언로드 되어야 한다.<br> 싱글톤 또한 정적 레퍼런스를 사용하기 때문에 GC에 수집되지 않는다.

<br>

# 🔷 <b> 차이점 </b>

| Static Class                                                                                                                        | Singleton                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 인스턴스를 생성할 수 없음.                                                                                                          | 인스턴스를 생성후 재사용이 가능                                                                                                                            |
| 컴파일러가 정적클래스를 컴파일할때 abstract 와 sealed class 인 것으로 취급함. 이것이 인스턴스를 생성하지 않아도 사용이 가능한 이유. | 싱글톤 클래스의 인스턴스 생성은 꼭 내부에서만 행해지기 때문에, 생성자가 private                                                                            |
| 처음 사용될때 초기화되어 클래스 로더 이슈가 발생할 수 있음.                                                                         | 초기화가 lazily하게 될 수 있고, CLR(Common Language Runtime)에 의해 프로그램이나 해당 크래스가 포함된 네임스페이스가 로드될 때 자동적으로 로드 될 수 있음. |
| 메서드 파라메터로 사용할 수 없음.                                                                                                   | 파라메터로 넘겨서 사용할 수 있음.                                                                                                                          |
| 어떤 것도 상속 받아 구현할 수 없음.                                                                                                 | 인터페이스나 다른 클래스를 상속받아 싱글톤 클래스를 만들 수 있음.                                                                                          |
| 인스턴스 클론, dispose 둘 다 불가능.                                                                                                | 인스턴스를 클론하여 사용할 수 있으며, dispose도 가능함.                                                                                                    |
| 인터페이스 주도 디자인이 아니기 때문에 불가능.                                                                                      | 인터페이스를 통해 의존성 주입 가능.                                                                                                                        |

<br>

# 🔷 <b> 선택 시 고려사항  </b>
- 클래스가 상태를 가져야하는가?
- 의존성 주입이 가능해야하는가?
- 객체를 복제할 일이 있는가?
<BR>

# 📚 <b> 레퍼런스 </b>
Singleton VS Static class in C# : https://dotnettutorials.net/lesson/singleton-vs-static-class/ <br>
Why You Should Prefer Singleton Pattern over a Static Class? : https://volosoft.com/blog/Prefer-Singleton-Pattern-over-Static-Class <br>
Singleton Pattern Versus Static Class : http://net-informations.com/faq/netfaq/singlestatic.htm <br>
Singleton vs. static classes in C# : https://www.infoworld.com/article/3601752/singleton-vs-static-classes-in-csharp.html