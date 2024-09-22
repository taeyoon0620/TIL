public class StringImmutabilityExample {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = str1;

        System.out.println("Before modification:");
        System.out.println("str1: " + str1);
        System.out.println("str2: " + str2);

        str1 += " World";

        System.out.println("\nAfter modification:");
        System.out.println("str1: " + str1);
        System.out.println("str2: " + str2);
    }
}






# 이 예제는 다음과 같은 String의 불변성을 보여줍니다:

str1과 str2가 처음에는 같은 "Hello" 문자열을 참조합니다.
str1에 " World"를 추가할 때, 실제로는 새로운 String 객체가 생성됩니다.
str2는 여전히 원래의 "Hello" 문자열을 참조하고 있습니다.

이는 String 객체가 한 번 생성되면 그 내용이 변경될 수 없음을 보여줍니다. "수정"은 실제로 새로운 String 객체를 생성하는 것입니다.
