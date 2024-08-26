## 객체 지향 프로그래밍 (OOP)
## Java는 객체 지향 언어로, 모든 것이 객체로 다뤄집니다. 클래스와 객체를 사용하여 데이터와 메소드를 캡슐화하고 상속, 다형성을 지원합니다.
<hr>
// 클래스 정의 및 객체 생성
class Animal {
    String name;

    // 생성자
    Animal(String name) {
        this.name = name;
    }

    // 메소드
    void makeSound() {
        System.out.println(name + " makes a sound.");
    }
}

// 상속
class Dog extends Animal {
    Dog(String name) {
        super(name);
    }

    // 메소드 오버라이딩
    @Override
    void makeSound() {
        System.out.println(name + " barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal("Generic Animal");
        animal.makeSound(); // 출력: Generic Animal makes a sound.

        Dog dog = new Dog("Buddy");
        dog.makeSound(); // 출력: Buddy barks.
    }
}

## 2. 플랫폼 독립성
## Java는 JVM (Java Virtual Machine)에서 실행되기 때문에 플랫폼에 독립적입니다. 코드가 JVM에서 실행되므로, 동일한 Java 코드가 어떤 플랫폼에서도 실행될 수 있습니다.
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
## 3. 자동 메모리 관리 (가비지 컬렉션)
## Java는 자동 메모리 관리를 통해 객체의 생명주기를 관리하고 가비지 컬렉터가 사용하지 않는 객체를 자동으로 삭제합니다.

public class GarbageCollectionExample {
    public static void main(String[] args) {
        // 객체 생성
        GarbageCollectionExample obj1 = new GarbageCollectionExample();
        GarbageCollectionExample obj2 = new GarbageCollectionExample();

        // obj1에 대한 참조를 잃어버림, 가비지 컬렉션의 대상이 될 수 있음
        obj1 = null;

        // 강제 가비지 컬렉션 호출 (보통 JVM이 자동으로 처리함)
        System.gc();
        
        // 잠시 대기하여 가비지 컬렉션이 완료될 시간 제공
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    @Override
    protected void finalize() throws Throwable {
        System.out.println("Garbage collected: " + this);
        super.finalize();
    }
}

## 4. 강한 타입 검사
## Java는 강한 타입 검사를 통해 컴파일 타임에 타입 오류를 방지합니다.

public class TypeSafetyExample {
    public static void main(String[] args) {
        // 정수형 변수
        int number = 10;

        // 문자열과 정수를 더하려고 하면 컴파일 오류 발생
        // String result = number + " is a number"; // 오류 발생

        // 올바른 예
        String result = number + " is a number";
        System.out.println(result); // 출력: 10 is a number
    }
}

