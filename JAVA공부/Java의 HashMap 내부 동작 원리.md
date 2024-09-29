Java의 HashMap 내부 동작 원리

# 면접 질문 예시:
HashMap이 내부적으로 어떻게 동작하나요?
HashMap에서 충돌이 발생하면 어떻게 처리하나요?
HashMap의 시간 복잡도는 어떻게 되나요?

# 개념 설명:
HashMap은 키-값 쌍으로 데이터를 저장하는 자료구조로, 내부적으로 배열과 연결 리스트(Java 8 이후에는 트리 구조)로 구현되어 있습니다.
키의 hashCode() 메서드를 사용하여 배열의 인덱스를 결정하고, 그 위치에 데이터를 저장합니다.
만약 동일한 해시코드 값을 가진 두 개의 키가 있으면 충돌이 발생합니다. 충돌은 체이닝 방식(배열 인덱스에 연결 리스트나 트리로 노드를 연결)으로 처리합니다.


import java.util.HashMap;
import java.util.Map;

public class HashMapExample {
    public static void main(String[] args) {
        // HashMap 생성
        Map<String, Integer> map = new HashMap<>();

        // 요소 추가
        map.put("Apple", 100);
        map.put("Banana", 200);
        map.put("Orange", 300);

        // HashMap의 특정 키 조회
        System.out.println("Value for key 'Apple': " + map.get("Apple"));
        
        // 요소 제거
        map.remove("Banana");

        // 요소 출력
        System.out.println("All elements in the map:");
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }

        // 충돌을 일으킬 수 있는 키 테스트
        System.out.println("\nSimulating Hash Collision:");
        String key1 = "FB";   // These keys have the same hash code in some versions of Java
        String key2 = "Ea";

        map.put(key1, 1);
        map.put(key2, 2);

        System.out.println("Value for key 'FB': " + map.get(key1));
        System.out.println("Value for key 'Ea': " + map.get(key2));
    }
}
코드 설명:
HashMap의 기본 사용법:

put(key, value)를 통해 값을 추가하고, get(key)를 통해 값을 조회할 수 있습니다.
키가 중복될 경우, 마지막으로 삽입된 값이 기존 값을 덮어씁니다.
충돌 시뮬레이션:

key1과 key2는 해시 충돌을 일으킬 수 있는 두 개의 문자열입니다. 그러나 HashMap은 충돌이 발생해도 키의 equals() 메서드를 이용해 구분하여 저장하고 조회합니다.
주요 질문에 대한 답변:
HashMap의 충돌 처리 방식: 해시 충돌이 발생하면 해당 버킷에서 연결 리스트(또는 트리)를 사용하여 데이터를 저장합니다. Java 8 이후에는 충돌이 많아지면 성능을 향상시키기 위해 연결 리스트 대신 트리로 전환됩니다.
HashMap의 시간 복잡도: 일반적으로 HashMap의 get()과 put() 연산은 O(1)의 시간 복잡도를 가집니다. 그러나 해시 충돌이 많을 경우 성능이 저하될 수 있으며, 최악의 경우에는 O(n)이 될 수 있습니다.





