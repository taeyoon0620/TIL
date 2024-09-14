문제: 회문 문자열(palindrome) 확인
회문이란 앞에서 읽으나 뒤에서 읽으나 같은 문자열을 말합니다. 주어진 문자열이 회문인지 확인하는 코드를 작성하세요. 대소문자는 구분하지 않으며, 공백은 무시합니다.

예시
입력: "A man a plan a canal Panama"
출력: true
요구사항
공백과 특수 문자는 무시합니다.
대소문자는 구분하지 않습니다.

public class PalindromeCheck {

    public static boolean isPalindrome(String str) {
        // 입력 문자열을 소문자로 변환하고, 알파벳과 숫자만 남긴다.
        String filteredStr = str.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        
        // 좌우에서 동시에 비교하여 회문 여부 확인
        int left = 0;
        int right = filteredStr.length() - 1;
        
        while (left < right) {
            if (filteredStr.charAt(left) != filteredStr.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        
        return true;
    }

    public static void main(String[] args) {
        String testStr = "A man a plan a canal Panama";
        
        if (isPalindrome(testStr)) {
            System.out.println("회문입니다.");
        } else {
            System.out.println("회문이 아닙니다.");
        }
    }
}


설명:
입력 문자열에서 알파벳과 숫자가 아닌 문자는 모두 제거하고, 소문자로 변환합니다.
첫 번째 문자와 마지막 문자를 비교하며, 하나씩 중앙으로 이동하면서 문자가 동일한지 확인합니다.
만약 한 번이라도 다른 문자가 발견되면 false를 반환하고, 끝까지 같으면 true를 반환합니다.
