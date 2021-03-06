# TDD

TDD(Test Driven Development)란 본격적인 개발에 들어가기 전에 테스트
계획 및 코드를 작성하는 것을 의미한다. 테스트가 개발을 이끌어 나가는 것이다.
예를들어, 개발 중 에러가 발생했을 때 소규모 개발에서는 큰 문제가 되지는 않지만,
대규모의 개발 상황에서는 수 많은 모듈과 함수간 종속성들이 굉장히 많은 시간을 괴롭히게 된다.
이러한 문제점을 해결하기 위해서 테스트 주도 개발이 등장했다.

나는 pytest를 사용할 것이다.
https://binux.tistory.com/47

일단, monkeypatch.setattr 살펴보자. 
이것은 어떤것을 하냐면, mocking이다. Mocking은 실제 값이 아닌 가짜 값을 만들어내는 것이다.

음 예를들면 Upload 클래스가 있다.

Class Upload    
|_ Def Extract   
|_ Def Transform   
|_ Def Load

이렇게 되어있을 때 나는 Transform 부분만 테스트하고 싶다. 하지만 함수의 종속성으로 인하여
Transform에서 사용되는 data는 Extract로 부터 참조되며 Extract에서 추출되는 data는 
특정 라이브러리의 기능을 참조한다. 나는 Transform 부분만 테스트하고 싶지만 이런 경우에 Extract부터
특정 라이브러리으 기능까지 테스트해야되는 상황에 처한 것이다. 이런 경우에 이제 Mocking이라는 기술을 쓴다.
pytest에서도 제공하는 function이 있지만, 단순한 예를 하나 들자면 정답과 인풋값을 csv파일이나 등등으로 미리 만들어서
로컬에서 참조하도록 코드를 작성하면 된다.

하지만 이때, 테스트 코드에서 원코드를 실행할 때 원코드의 Extract가 실행 되기 때문에
monkeypatch.setattr 같은 기능으로 해당 function을 사용하지 않고 넘겨주는 기능을 넣어줘야한다.

***
# each map
each map을 알아야한다. 
음 지금 내가 하는 것은 DB -> transform -> DB 적재이다.
transform에서 전처리 및 parsing을 해주는데, transform에서 이뤄지는 작업은
모든 Dataframe이 메모리 상으로 올라가게 된다. 작은 task면 문제없이 실행 되겠지만,
큰 규모의 task는 메모리를 많이 차지하게 되어 에러가 날 수 있다.
이럴 때 사용 하는 것이 each map이다.
each map은 dataframe에서 row 별로 메모리 상으로 올린다.
이후 해당 row에서 특정 처리를 진행 후에 buffer로 옮긴 뒤 DB로 적재를 한다.
이 때 조심해야 하는 부분은 seperate다. row에서 컬럼으로 구분하는 seperate값을 잘 이용해야지 에러가 나지 않을 것이다.

***
즉! pytest 부분을 더 공부하고 적절한 testset을 생각해보고, testcode를 작성해보자!