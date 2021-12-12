# Javascript에서 소수점 둘째자리까지 반올림 계산하기

```javascript
// 일반적으로 이렇게 100을 곱하고 반올림 후 다시 100으로 나눠준다.
Math.round(1.777 * 100) / 100 // return 1.78

// 하지만 1.005 같은 수는 1.01이 아닌 1을 반환한다.
Math.round(1.005 * 100) / 100 // return 1

// 이 문제를 해결하기 위해 Number.EPSILON을 더해주면 해결된다.
Math.round((1.005 + Number.EPSILON) * 100) / 100 // return 1.01
Math.round((1.255 + Number.EPSILON) * 100) / 100 // return 1.26

// 하지만 이렇게 해도 완벽하게 반올림되는 것은 아니다.
Math.round((1.3449999999999999 + Number.EPSILON) * 100) / 100 // return 1.35
```
