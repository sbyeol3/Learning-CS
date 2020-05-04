# ***Mutex & Semaphore***

## **Mutex**
#### **Mutex** 는 리소스에 대한 액세스를 동기화 하는 상호배제 객체입니다. mutex는 한번에 하나의 스레드만 mutex를 획득하고 중요 섹션에 들어갈 수 있도록 하는 잠금 메커니즘 입니다. 임계영역에 들어갈때 락 (LOCK)을 걸어 다른 쓰레드가 접근하지 못하도록 하고 , 나오면 해당 락을 (UNLOCK)해줍니다.


## **Semaphore**
####  **Semaphore** 는 멀티 프로그래밍 환경에서 공유 자원에 대한 접근을 제한 하는 방법으로 사용됩니다. 세마포어 카운트는 1이상이며 카운트를 조절하여 진입가능한 프로세스/ 쓰레드 수를 조절할 수 있습니다. 세마포어 의 값이 0이면 자원에 접근할 수 없도록 블럭을 하고 0보다 크면 접근함과 동시에 세마포어 값을 1감소 시킵니다. 반대로 종료하고 나갈 때에는 세마포어 값을 1 증가시켜 다른 프로세스가 접근할 수 있도록 합니다. 




## **Differnece between Mutex and Semaphore**

+ **Semaphore**는 현재 수행중이지 않은 프로세스가 세마포어를 해제할 수 있다.
+ **Mutex**는 lock을 획득한 쓰레드만이 unlock을 할 수 있다.
+ **Mutex**는 오직 1개의 쓰레드/ 프로세스만이 접근 가능하다. 
+ **Mutex**는 **Semaphore**가 될 수 없지만 **Semaphore**는 **Mutex**가 될 수 있다. 
  
  <br>

  
  * * *
  ##### 출처 

  [Semaphore](https://en.wikipedia.org/wiki/Semaphore_(programming))<br>

  [Mutex](https://worthpreading.tistory.com/90)









