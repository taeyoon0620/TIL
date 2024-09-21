# 문제 설명
여러 스레드가 공유 자원을 동시에 접근할 때, 데이터 무결성을 유지하는 방법을 알아야 합니다. synchronized 키워드를 사용하여 한 번에 하나의 스레드만 공유 자원을 수정하도록 보장할 수 있습니다.

# 예제: 동기화된 메서드를 이용한 은행 계좌에서의 출금 예제

class BankAccount {
    private int balance = 1000;

    // synchronized 메서드를 통해 동기화 처리
    public synchronized void withdraw(int amount) {
        if (balance >= amount) {
            System.out.println(Thread.currentThread().getName() + " is going to withdraw " + amount);
            try {
                Thread.sleep(100);  // 출금 중간에 지연이 발생한다고 가정
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            balance -= amount;
            System.out.println(Thread.currentThread().getName() + " completed the withdrawal. Remaining balance: " + balance);
        } else {
            System.out.println(Thread.currentThread().getName() + " tried to withdraw " + amount + " but insufficient balance.");
        }
    }

    public int getBalance() {
        return balance;
    }
}

class WithdrawTask implements Runnable {
    private BankAccount account;
    private int amount;

    public WithdrawTask(BankAccount account, int amount) {
        this.account = account;
        this.amount = amount;
    }

    @Override
    public void run() {
        account.withdraw(amount);
    }
}

public class ThreadSynchronizationExample {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();

        // 두 개의 스레드가 동일한 은행 계좌에서 출금하려고 시도
        Thread t1 = new Thread(new WithdrawTask(account, 600), "Thread-1");
        Thread t2 = new Thread(new WithdrawTask(account, 600), "Thread-2");

        t1.start();
        t2.start();
    }
}

# 코드 설명
BankAccount 클래스: balance라는 공유 자원을 가지고 있습니다.
synchronized 메서드 withdraw: 이 메서드는 여러 스레드가 동시에 접근할 때 동기화를 보장합니다. 즉, 한 스레드가 withdraw 메서드를 실행하고 있을 때 다른 스레드는 대기하게 됩니다.
WithdrawTask 클래스: Runnable 인터페이스를 구현하여 스레드에서 실행할 수 있는 작업을 정의합니다.
ThreadSynchronizationExample 클래스: 두 개의 스레드를 생성하여 동시에 출금을 시도합니다.
# 결과
두 개의 스레드가 동시에 600원을 출금하려고 시도하지만, 동기화 덕분에 한 스레드가 먼저 출금을 완료하면 다른 스레드는 남은 잔액을 확인하고 출금을 실패하게 됩니다.

이 예제는 자바에서 스레드 동기화가 어떻게 작동하는지 설명하는 좋은 방법입니다.
