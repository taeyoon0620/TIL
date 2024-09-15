class Example {
    // 정적 변수: 모든 객체가 공유
    static int staticVar = 0;

    // 인스턴스 변수: 각 객체마다 독립적으로 가짐
    int instanceVar = 0;

    // 정적 메서드: 객체를 생성하지 않고 클래스 자체에서 호출 가능
    static void staticMethod() {
        System.out.println("Static method called.");
        staticVar++; // 정적 변수만 접근 가능
        // instanceVar++; // 에러 발생: 정적 메서드는 인스턴스 변수에 접근 불가
    }

    // 인스턴스 메서드: 객체를 통해 호출해야 함
    void instanceMethod() {
        System.out.println("Instance method called.");
        staticVar++; // 정적 변수에 접근 가능
        instanceVar++; // 인스턴스 변수에 접근 가능
    }
}

public class Main {
    public static void main(String[] args) {
        // 정적 메서드는 객체 생성 없이 바로 호출 가능
        Example.staticMethod();
        System.out.println("Static Var: " + Example.staticVar);

        // 인스턴스 메서드는 객체 생성 후 호출
        Example obj1 = new Example();
        Example obj2 = new Example();

        obj1.instanceMethod();
        obj2.instanceMethod();
        
        System.out.println("Obj1 Instance Var: " + obj1.instanceVar);
        System.out.println("Obj2 Instance Var: " + obj2.instanceVar);
        System.out.println("Static Var after instance methods: " + Example.staticVar);
    }
}

# 실행 결과:

Static method called.
Static Var: 1
Instance method called.
Instance method called.
Obj1 Instance Var: 1
Obj2 Instance Var: 1
Static Var after instance methods: 3

설명:
static 변수는 클래스 레벨에서 공유됩니다. 모든 인스턴스가 동일한 변수를 공유합니다.
static 메서드는 객체를 생성하지 않고 호출할 수 있습니다. 그러나 인스턴스 변수에는 접근할 수 없습니다.
인스턴스 메서드는 각 객체에서 호출되고, 인스턴스 변수와 정적 변수에 모두 접근할 수 있습니다.







