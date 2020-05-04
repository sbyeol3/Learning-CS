# **PROCESS  & THREAD**



+ <u> **프로세스**</u>
###  프로세스(process)는 컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램을 말한다. 종종 스케쥴링의 대상이 되는 작업 (task)이라는 용어와 거의 같은 의미로 쓰인다. 여러 개의 프로세서를 사용하는 것을 멀티 프로세싱이라고 하며 같은 시간에 여러개의 프로그램을 띄우는 시분할 방식을 멀티 태스킹이라고 한다. 

  
  

+ <u> **쓰레드** </u>

### 쓰레드(thread)는 어떠한 프로그램 내에서 , 특히 프로세스 내에서 실행되는 흐름의 단위를 말한다. 일반적으로 한 프로그램은 하나의 쓰레드를 가지고 있지만, 프로그램 환경에 따라 둘 이상의 쓰레드를 동시에 실행할 수 있다. 이러한 실행 방식을 멀티 쓰레드(multithread)라고한다.
 

<br>

*  *  * 
<br>

+ <u>**프로세스와  쓰레드의 차이** </u>


<br>


&nbsp;

<img src = "https://gmlwjd9405.github.io/images/os-process-and-thread/process.png" width = "400" height ="300" >
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 &nbsp;
 
 
<img src = "https://gmlwjd9405.github.io/images/os-process-and-thread/thread.png" width = "400" height = "300">

<br>
<br>

**프로세스**는 운영체제로 부터 자원을 할당 받는 작업의 단위이고 각각의 독립된 메모리 영역 (Code, Data, Stack, Heap)을 할당 받는다.한 프로세스는 다른 프로세스의 변수나 자료구조에 접근 할 수 없다. 한 프로세스가 다른 프로세스의 자원에 접근하려면 프로세스간 통신 (IPC , inter - communication)을 사용해야한다. 
<br>

**쓰레드**는 프로세스 내에서 각각 Stack만을 따로 할당 받고, Code, Data, Heap 영역은 공유한다. 프로세스 내의 주소 공간이나 자원들을 같은 프로세스 내에 쓰레드 끼리 공유하면서 실행한다. 따라서, 한 쓰레드가 프로세스 자원을 변경하면 다른 쓰레드도 그 변경결과를 즉시 볼 수 있다. 

<br>

 * * * 

### **참고자료**

[프로세스](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4)
 
[쓰레드](
https://ko.wikipedia.org/wiki/%EC%8A%A4%EB%A0%88%EB%93%9C_(%EC%BB%B4%ED%93%A8%ED%8C%85))

[difference between process and thread](https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html)









