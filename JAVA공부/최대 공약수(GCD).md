유클리드 호제법을 사용하여 두 숫자의 최대 공약수를 구하는 간단한 자바 프로그램을 구현해보겠습니다.

import java.util.Scanner;

public class GCD {

    // 유클리드 호제법을 사용하여 GCD를 구하는 메서드
    public static int calculateGCD(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("첫 번째 숫자를 입력하세요: ");
        int num1 = scanner.nextInt();
        
        System.out.print("두 번째 숫자를 입력하세요: ");
        int num2 = scanner.nextInt();
        
        int gcd = calculateGCD(num1, num2);
        
        System.out.println(num1 + "와 " + num2 + "의 최대 공약수는: " + gcd);
        
        scanner.close();
    }
}

# 설명
calculateGCD 메서드: 두 숫자의 최대 공약수를 계산하는 메서드입니다. 유클리드 호제법을 사용하여 반복적으로 나머지를 계산합니다.
main 메서드: 사용자로부터 두 개의 숫자를 입력받아 calculateGCD 메서드를 호출하여 최대 공약수를 계산하고 결과를 출력합니다.

# 사용 방법
위 코드를 Java IDE에 복사하여 붙여넣습니다.
프로그램을 실행하면 두 개의 숫자를 입력하라는 메시지가 나타납니다.
숫자를 입력하면 그들의 최대 공약수가 출력됩니다.
