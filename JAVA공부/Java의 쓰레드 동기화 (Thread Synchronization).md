# 면접 질문 예시:
  synchronized 키워드의 역할은 무엇인가요?
  멀티스레딩 환경에서 동기화 문제를 어떻게 해결할 수 있나요?
  volatile과 synchronized의 차이점은 무엇인가요?

# 개념 설명:
  동기화는 여러 쓰레드가 동시에 하나의 자원에 접근하는 것을 조절하는 방법입니다.
  synchronized 키워드를 사용하여 임계영역(critical section)을 보호할 수 있습니다.
  동기화가 이루어지지 않으면 데이터 경쟁(race condition) 문제가 발생하여 예상치 못한 결과가 나올 수 있습니다.

# 코드 예시: 쓰레드 동기화 예제
class Counter {
    private int count = 0;

    // synchronized 메서드를 통해 동기화 처리
    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

class MyThread extends Thread {
    private Counter counter;

    public MyThread(Counter counter) {
        this.counter = counter;
    }

    @Override
    public void run() {
        for (int i = 0; i < 1000; i++) {
            counter.increment(); // 동기화된 increment() 호출
        }
    }
}

public class SynchronizedExample {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        // 2개의 쓰레드를 생성하여 시작
        MyThread t1 = new MyThread(counter);
        MyThread t2 = new MyThread(counter);

        t1.start();
        t2.start();

        // 메인 쓰레드가 두 쓰레드가 종료될 때까지 대기
        t1.join();
        t2.join();

        // 최종 카운트 값 출력
        System.out.println("Final Count: " + counter.getCount());
    }
}

그렇다면 이번에는 "Java의 쓰레드 동기화 (Thread Synchronization)" 주제를 선택하여 간단한 코드를 구현해 보겠습니다. 이 주제는 자바의 멀티스레딩 환경에서 동기화를 어떻게 처리하는지에 대한 이해를 테스트하는 면접에서 자주 나올 수 있습니다.

면접 질문 예시:
synchronized 키워드의 역할은 무엇인가요?
멀티스레딩 환경에서 동기화 문제를 어떻게 해결할 수 있나요?
volatile과 synchronized의 차이점은 무엇인가요?
개념 설명:
동기화는 여러 쓰레드가 동시에 하나의 자원에 접근하는 것을 조절하는 방법입니다.
synchronized 키워드를 사용하여 임계영역(critical section)을 보호할 수 있습니다.
동기화가 이루어지지 않으면 데이터 경쟁(race condition) 문제가 발생하여 예상치 못한 결과가 나올 수 있습니다.
코드 예시: 쓰레드 동기화 예제
java
코드 복사
class Counter {
    private int count = 0;

    // synchronized 메서드를 통해 동기화 처리
    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

class MyThread extends Thread {
    private Counter counter;

    public MyThread(Counter counter) {
        this.counter = counter;
    }

    @Override
    public void run() {
        for (int i = 0; i < 1000; i++) {
            counter.increment(); // 동기화된 increment() 호출
        }
    }
}

public class SynchronizedExample {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        // 2개의 쓰레드를 생성하여 시작
        MyThread t1 = new MyThread(counter);
        MyThread t2 = new MyThread(counter);

        t1.start();
        t2.start();

        // 메인 쓰레드가 두 쓰레드가 종료될 때까지 대기
        t1.join();
        t2.join();

        // 최종 카운트 값 출력
        System.out.println("Final Count: " + counter.getCount());
    }
}

# 코드 설명:
# Counter 클래스:
 
increment() 메서드는 synchronized 키워드를 사용하여 동기화되었습니다. 이렇게 하면 여러 쓰레드가 동시에 increment()를 호출해도 하나의 쓰레드만 이 메서드를 실행할 수 있습니다.
동기화되지 않으면 여러 쓰레드가 동시에 count 값을 수정하려고 하여 데이터 손실이 발생할 수 있습니다.
MyThread 클래스:

Counter 객체를 공유하여 각 쓰레드가 1000번씩 increment()를 호출하도록 설정되었습니다.
# main() 메서드:

두 개의 쓰레드를 실행하고, join() 메서드를 사용하여 두 쓰레드가 끝날 때까지 기다린 후 최종 결과를 출력합니다.


# 주요 질문에 대한 답변:
# synchronized의 역할: synchronized 키워드는 임계영역(critical section)을 보호하여 여러 쓰레드가 동시에 접근하지 못하도록 합니다.
# 동기화 문제 해결: 동기화 문제는 synchronized 블록이나 메서드를 사용하여 해결할 수 있습니다. 이 방법을 통해 여러 쓰레드가 동시에 하나의 자원에 접근하는 것을 방지합니다.
# volatile과 synchronized의 차이점: volatile은 변수를 쓰레드 간에 즉시 공유하도록 하며, 단일 읽기 및 쓰기 작업에만 동작합니다. 반면 synchronized는 여러 쓰레드가 특정 블록에 접근하는 것을 제어하고, 임계영역 내의 모든 코드가 동기화됩니다.
