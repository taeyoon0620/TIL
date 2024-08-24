## stack 후입선출(LIFO, Last In First Out) 구조로, 나중에 들어간 데이터가 먼저 나옵니다.

import java.util.EmptyStackException;

class Stack {
    private int[] stack;
    private int top;
    private int maxSize;

    // 스택 생성자
    public Stack(int size) {
        maxSize = size;
        stack = new int[maxSize];
        top = -1;
    }

    // 스택이 비어 있는지 확인
    public boolean isEmpty() {
        return top == -1;
    }

    // 스택이 가득 찼는지 확인
    public boolean isFull() {
        return top == maxSize - 1;
    }

    // 스택에 데이터 추가
    public void push(int value) {
        if (isFull()) {
            System.out.println("Stack is full");
        } else {
            stack[++top] = value;
        }
    }

    // 스택에서 데이터 제거
    public int pop() {
        if (isEmpty()) {
            throw new EmptyStackException();
        } else {
            return stack[top--];
        }
    }

    // 스택의 가장 위의 데이터 확인
    public int peek() {
        if (isEmpty()) {
            throw new EmptyStackException();
        } else {
            return stack[top];
        }
    }
}

public class StackExample {
    public static void main(String[] args) {
        Stack stack = new Stack(5);
        stack.push(10);
        stack.push(20);
        stack.push(30);

        System.out.println("Top element: " + stack.peek());
        System.out.println("Popped element: " + stack.pop());
        System.out.println("Top element after pop: " + stack.peek());
    }
}

## 큐는 선입선출(FIFO, First In First Out) 구조로, 먼저 들어간 데이터가 먼저 나옵니다.
class Queue {
    private int[] queue;
    private int front;
    private int rear;
    private int maxSize;
    private int currentSize;

    // 큐 생성자
    public Queue(int size) {
        maxSize = size;
        queue = new int[maxSize];
        front = 0;
        rear = -1;
        currentSize = 0;
    }

    // 큐가 비어 있는지 확인
    public boolean isEmpty() {
        return currentSize == 0;
    }

    // 큐가 가득 찼는지 확인
    public boolean isFull() {
        return currentSize == maxSize;
    }

    // 큐에 데이터 추가
    public void enqueue(int value) {
        if (isFull()) {
            System.out.println("Queue is full");
        } else {
            rear = (rear + 1) % maxSize;
            queue[rear] = value;
            currentSize++;
        }
    }

    // 큐에서 데이터 제거
    public int dequeue() {
        if (isEmpty()) {
            throw new RuntimeException("Queue is empty");
        } else {
            int value = queue[front];
            front = (front + 1) % maxSize;
            currentSize--;
            return value;
        }
    }

    // 큐의 가장 앞의 데이터 확인
    public int peek() {
        if (isEmpty()) {
            throw new RuntimeException("Queue is empty");
        } else {
            return queue[front];
        }
    }
}

public class QueueExample {
    public static void main(String[] args) {
        Queue queue = new Queue(5);
        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);

        System.out.println("Front element: " + queue.peek());
        System.out.println("Dequeued element: " + queue.dequeue());
        System.out.println("Front element after dequeue: " + queue.peek());
    }
}
