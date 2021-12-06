# Throttle과 Debounce

Throttle과 Debounce는 함수가 호출되는 빈도를 제어하는 방법입니다. 자주 발생하는 DOM 이벤트로 인한 성능 저하를 막기 위해 이벤트 콜백 함수 호출 빈도를 제어하는 방법으로 많이 사용합니다.  

- Throttle은 일정 주기마다 한 번씩 이벤트가 발생하도록 하는 방법입니다.
- Debounce는 일정 주기의 시작 혹은 끝에 한 개의 이벤트만 발생하도록 하는 방법입니다.


### Throttle과 Debounce를 사용하는 이유

사용자의 한 번의 드래깅으로 수많은 스크롤 이벤트가 발생합니다. 스크롤바를 드래그하는 것만으로 초당 30개 이상의 이벤트가 발생할 수 있습니다. 

이로 인해 수많은 스크롤 이벤트에 대한 콜백(callback)이 발생하고 콜백을 수행하는 일에 큰 리소스가 소모됩니다. 이와 같이 과도한 이벤트 발생으로 이벤트 핸들러가 DOM 조작과 같은 무거운 계산을 수행하여 성능 저하가 일어나는 것을 방지하기 위해 이벤트 발생 빈도를 제어하는 throttle과 debounce를 사용합니다.  


### Debounce

Debounce는 여러번 잇달아 발생하는 이벤트를 그룹으로 묶어 처음 혹은 마지막 이벤트 발생 시에 함수를 트리거하는 방법입니다. 함수를 use case마다 한 번만 트리거하고 싶을 때 사용합니다. 

예를 들어, 유저가 키보드를 입력하는 중에는 이벤트를 처리하지 않다가 타이핑이 끝났을 때 값을 받아올 수 있습니다. 혹은 브라우저 윈도우 사이즈를 바꿀 때, 마지막으로 발생한 resize 이벤트에서 값을 받아올 수 있습니다.


### Throttle

Throttle은 특정 주기를 정해 한 주기 내에서 이벤트가 한 번만 트리거되도록 처리하는 방법입니다. 주기를 조절할 수 있으며, 트위터에서 스크롤 관련 버벅임이 발생했을 때 [존 레식이 해결책으로 제안한 방법론](https://johnresig.com/blog/learning-from-twitter/)입니다. 

예를 들어, 무한 스크롤링 페이지에서 페이지 바닥까지 남은 거리 값을 계산하기 위해 일정 주기마다 스크롤 이벤트를 처리하는 throttle을 사용합니다. 일정 주기마다 페이지 바닥까지 얼마나 떨어져있는지를 확인하여 유저가 페이지 바닥에 도달했을 때 다음 콘텐츠를 볼 수 있도록 할 수 있습니다. 

만약 debounce를 이용해 구현한다면 마지막 스크롤 이벤트에서만 값을 받기 때문에 유저가 페이지 바닥에 도달했을 때 data를 fetching하기 시작해 사용자 경험을 떨어뜨릴 것입니다. 


## 정리

- Throttle과 Debounce는 함수가 호출되는 빈도를 제어하는 방법이다.
- Throttle은 특정 주기마다 한 번 함수를 호출할 때 사용한다.
- Debounce는 잇달아 호출되는 함수 중 처음 혹은 마지막 함수만 호출할 때 사용한다.
- Throttle은 적어도 일정 주기마다(e.g., 300 ms) 함수 실행을 보장하지만, debounce는 보장하지 않습니다.
- debounce는 연달아 발생한 이벤트는 모두 무시하고 특정 시간 사이에 어떤 이벤트도 발생하지 않았을 때 이벤트 함수를 호출합니다.

## 참고 자료

* https://css-tricks.com/debouncing-throttling-explained-examples/
* https://webclub.tistory.com/607
* https://www.freecodecamp.org/news/javascript-debounce-example/