# 설명: 1부터 n까지의 숫자를 출력하는 프로그램을 작성하되, 숫자가 3의 배수일 경우 "Fizz", 5의 배수일 경우 "Buzz", 두 경우 모두 해당될 경우 "FizzBuzz"를 출력하도록 합니다.

public class FizzBuzz {
    public static void main(String[] args) {
        int n = 100; // 출력할 숫자 범위
        for (int i = 1; i <= n; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                System.out.println("FizzBuzz");
            } else if (i % 3 == 0) {
                System.out.println("Fizz");
            } else if (i % 5 == 0) {
                System.out.println("Buzz");
            } else {
                System.out.println(i);
            }
        }
    }
}

# 2. 문자열 뒤집기
# 설명: 주어진 문자열을 뒤집는 메서드를 작성하세요.

public class ReverseString {
    public static void main(String[] args) {
        String input = "Hello, World!";
        String reversed = reverse(input);
        System.out.println(reversed);
    }

    public static String reverse(String str) {
        StringBuilder reversed = new StringBuilder(str);
        return reversed.reverse().toString();
    }
}

# 3. 소수 판별
# 설명: 주어진 숫자가 소수인지 판별하는 메서드를 작성하세요.

public class PrimeNumber {
    public static void main(String[] args) {
        int number = 29; // 소수 판별할 숫자
        boolean isPrime = isPrime(number);
        System.out.println(number + "은 소수입니다: " + isPrime);
    }

    public static boolean isPrime(int num) {
        if (num <= 1) return false;
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }
}

# 4. 피보나치 수열
# 설명: n번째 피보나치 수를 계산하는 메서드를 작성하세요.

public class Fibonacci {
    public static void main(String[] args) {
        int n = 10; // n번째 피보나치 수
        int fib = fibonacci(n);
        System.out.println(n + "번째 피보나치 수: " + fib);
    }

    public static int fibonacci(int n) {
        if (n <= 1) return n;
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
}

# 5. 배열의 최대값 찾기
# 설명: 주어진 정수 배열에서 최대값을 찾는 메서드를 작성하세요.

public class MaxInArray {
    public static void main(String[] args) {
        int[] numbers = {3, 5, 1, 8, 2};
        int max = findMax(numbers);
        System.out.println("배열의 최대값: " + max);
    }

    public static int findMax(int[] arr) {
        int max = arr[0];
        for (int number : arr) {
            if (number > max) {
                max = number;
            }
        }
        return max;
    }
}



