# [2021 Dev-Matching: 웹 백엔드 개발자(상반기)] 로또의 최고 순위와 최저 순위 (58%)

### 소요 시간 : 20분

```java
import java.util.*;
import java.util.stream.*;

/**
 * 민우의 로또 번호 lottos
 * 당첨 번호 win_nums
 * answer [최고순위, 최저순위]
 * 1. lottos, win_nums를 Set으로 바꾼다.
 * 2. 중복되는 수만큼 count 증가
 * 3-1. 0의 개수만큼 count증가 -> 최고순위
 * 3-2. count -> 최저순위
 */
class Solution {
    public int[] solution(int[] lottos, int[] win_nums) {

        int[] answer = new int[2];
        int count = 0;
        int countZero = 0;
        Set<Integer> win_set = Arrays.stream(win_nums).boxed().collect(Collectors.toSet());
        for (int lotto : lottos) {
            if (win_set.contains(lotto)) count++;
            if (lotto == 0) countZero++;
        }
        answer[0] = setRank(count + countZero);
        answer[1] = setRank(count);

        return answer;
    }

    public static int setRank(int count) {
        switch (count) {
            case 6:
                return 1;
            case 5:
                return 2;
            case 4:
                return 3;
            case 3:
                return 4;
            case 2:
                return 5;
            default:
                return 6;
        }
    }
}
```
