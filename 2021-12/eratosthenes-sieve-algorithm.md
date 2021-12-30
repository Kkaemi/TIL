# 에라토스테네스의 체

임의의 숫자 N까지의 소수를 모두 구하는 자바스크립트 코드

```javascript
const eratos = (n) => {
  // 1부터 N까지의 배열 생성
  // [ 1,2,3, ..., N ]
  const nums = Array.from({ length: n }, (_, idx) => idx + 1);
  
  // 2부터 N의 제곱근까지만 반복
  for (let i = 2; i < Math.sqrt(n); i++) {
  
    // 소수 2, 3, 5, ...
    const num = nums[i - 1];
    
    // 소수의 배수여서 0이 되버린 수 스킵
    if (!num) {
      continue;
    }
  
    // 소수의 배수 0으로 만들기
    for (let j = i - 1; j < nums.length; j+= num) {
    
      // 처음 숫자이면 스킵 ex) 2, 3, 5, ...
      if (nums[j] === num) {
        continue;
      }
      
      nums[j] = 0;
    }
  }
  
  // 1은 소수가 아니므로 지워준다.
  nums.shift();
  
  // 0이 되어버린 숫자들 정리
  return nums.filter(num => num);
}

// 100까지의 소수 구하기
// [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
eratos(100);
```

참고 : [위키피디아](https://ko.wikipedia.org/wiki/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98_%EC%B2%B4)
