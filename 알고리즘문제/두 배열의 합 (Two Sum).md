문제: 두 배열의 합 (Two Sum)
정수로 이루어진 배열 nums와 정수 target이 주어졌을 때, 배열에서 두 수를 골라 더했을 때 target이 되는 두 수의 인덱스를 반환하세요.

조건:

각 입력에 정확히 하나의 답이 있다고 가정할 수 있습니다.
같은 요소를 두 번 사용할 수 없습니다.
입력 예시:

python
코드 복사
nums = [2, 7, 11, 15]
target = 9
출력 예시:

python
코드 복사
[0, 1]
(배열의 첫 번째 요소 2와 두 번째 요소 7을 더하면 9가 되므로, 인덱스 0과 1을 반환합니다.)

힌트:

딕셔너리(해시맵)를 사용하여 해결할 수 있습니다.
시간 복잡도를 최적화하려면, 배열을 한 번만 순회하여 답을 찾는 방법을 고려하세요.

이 문제는 딕셔너리(해시맵)를 사용하여 효율적으로 풀 수 있습니다. 딕셔너리를 사용하면 배열을 한 번만 순회하여 두 수의 합이 target이 되는 인덱스를 찾을 수 있습니다. 아래는 Python을 사용한 코드 예시입니다:

def twoSum(nums, target):
    # 딕셔너리 생성: 키는 숫자, 값은 해당 숫자의 인덱스
    num_map = {}
    
    # 배열을 순회하며 각 요소에 대해 작업 수행
    for i, num in enumerate(nums):
        # target에서 현재 숫자를 뺀 값
        complement = target - num
        
        # 만약 complement가 이미 딕셔너리에 존재한다면, 정답을 찾은 것
        if complement in num_map:
            return [num_map[complement], i]
        
        # 딕셔너리에 현재 숫자와 인덱스를 추가
        num_map[num] = i

# 예시 실행
nums = [2, 7, 11, 15]
target = 9
result = twoSum(nums, target)
print(result)  # 출력: [0, 1]

# 설명: 배열을 순회하면서, target에서 현재 숫자 num를 뺀 값을 complement로 계산합니다.
complement가 딕셔너리 num_map에 이미 존재하는지 확인합니다.
존재한다면, 해당 complement의 인덱스와 현재 인덱스를 반환합니다.
존재하지 않는다면, 현재 숫자와 인덱스를 딕셔너리에 추가합니다.
이 알고리즘의 시간 복잡도는 O(n)이며, n은 배열의 크기입니다. 배열을 한 번만 순회하기 때문에 매우 효율적입니다.
