# 질문: "멀티스레딩 환경에서 공유 자원에 대한 동시 접근 문제를 어떻게 해결할 수 있나요?"

이 질문에 대한 답변으로는 자바의 synchronized 키워드를 사용하여 공유 자원에 대한 동시 접근 문제를 해결하는 방법을 설명할 수 있습니다. 그럼 간단한 예제를 통해 이를 구현해 보겠습니다.

예제: 동기화를 사용하여 멀티스레딩 환경에서 데이터 일관성 유지

class Counter {
    private int count = 0;

    // synchronized 메서드: 여러 스레드가 동시에 이 메서드에 접근하지 못하도록 동기화
    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

class CounterThread extends Thread {
    private Counter counter;

    public CounterThread(Counter counter) {
        this.counter = counter;
    }

    @Override
    public void run() {
        for (int i = 0; i < 1000; i++) {
            counter.increment();  // 공유 자원에 접근
        }
    }
}

public class SynchronizationExample {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        // 두 개의 스레드를 생성하여 동시에 count 값을 증가시킴
        Thread t1 = new CounterThread(counter);
        Thread t2 = new CounterThread(counter);

        t1.start();
        t2.start();

        // 두 스레드가 종료될 때까지 대기
        t1.join();
        t2.join();

        // 동기화된 메서드 덕분에 정확한 결과 출력
        System.out.println("Final count: " + counter.getCount());
    }
}

설명:
Counter 클래스는 count라는 공유 자원을 가집니다.
increment() 메서드는 synchronized로 선언되어 있어, 여러 스레드가 동시에 이 메서드를 실행하려고 하면 하나의 스레드가 끝날 때까지 다른 스레드는 대기합니다.
두 개의 스레드 t1, t2는 동시에 counter.increment() 메서드를 호출하여 count 값을 1000번씩 증가시키려고 합니다.
synchronized 키워드를 사용하지 않으면, 스레드들이 동시에 count 값을 수정하여 예상치 못한 값이 나올 수 있지만, 동기화를 통해 데이터 레이스(Data Race) 문제를 방지할 수 있습니다.
결과:
두 스레드가 count를 1000번씩 증가시키면 최종 값은 2000이어야 합니다. 동기화를 사용했기 때문에 스레드 간 경쟁 조건을 방지하고 정확한 결과인 Final count: 2000이 출력됩니다.

요약:
이 예제는 자바의 synchronized 키워드를 사용해 멀티스레딩 환경에서 동시 접근을 제어하는 방법을 보여줍니다. 이를 통해 공유 자원에 대한 스레드 간의 충돌 문제를 해결할 수 있습니다.
