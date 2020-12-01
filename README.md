### programmers - 두 개 뽑아서 더하기

[ 문제 설명 ]
정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

```
function solution(numbers) {
    let result  = [];
    for (let i = 0; i < numbers.length; i++) {
        for ( let j = i + 1; j < numbers.length; j++) { //서로 다른 인덱스에서 뽑아야 하므로 let j=i+1;
            const sum = numbers[i] + numbers[j]; // 두 개의 수를 뽑아 더해서 sum에 대입
            if (result.indexOf(sum) === -1) { //두 수를 뽑을 때 조건문을 이용해 result에 sum 값이 없으면 실행
                result.push(sum); //sum 배열 추가
            }
        }
    }
    result.sort((a,b) => a-b); // 오름차순 정렬
    return result;
}
```

```
//spread operation

function solution(numbers) {
    const temp = [];

    for (let i = 0; i < numbers.length; i++) {
        for (let j = i + 1; j < numbers.length; j++) {
            temp.push(numbers[i] + numbers[j]);
        }
    }

    const answer = [...new Set(temp)];

    return answer.sort((a, b) => a - b);
}
```

## stack & queue - 기능 개발


[ 문제 설명 ]
//1. 각 기능은 진도가 100%일 때 서비스 반영
//2. 진도 : progresses 속도: speeds
//3. 첫번째 기능이 끝나고 그 다음 내용 배포 가능 - return 2,1



```
function solution(progresses, speeds) {
  let arr = [];
  

   while(progresses.length > 0) {
       let count = 0;
    
        for(let i=0; i < progresses.length; i++) {
            progresses[i] += speeds[i];
     }

     while(progresses[0] >= 100) {
        progresses.shift();
        speeds.shift();
        count++;
     }
        
    if(count > 0) {
      arr.push(count);
    }
        
  }

  return arr;
}

// let progresses = [93,30,55];
// let speeds = [1,30,5];

// console.log(solution(progresses,speeds));
```




