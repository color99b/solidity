# Event

- solidity 에는 print, console.log 개념이 없기에 event라는 것을 발생시킨다.
- event가 발생하면 log가 블록에 저장되어 언제든지 가공할 수 있게 된다.
- 정의방법 : event [이벤트명] (출력하고 싶은 parameter)
- 사용방법 : emit [이벤트명] (정의한 parameter와 맞는 typeOfvalue 와 valueName)
- block 의 log 안에 남게되어 block의 log를 조회하면 된다.
- ex:

```solidity
contract A {
  event info(string name, uint money);

  function sendMoney() public {
    emit info("KYJ", 200);
  }
}
```

## index

- 특정한 이벤트를 콕 집어서 그 이벤트의 값을 가져올 때 사용
- 블록에 담기는 정보는 똑같지만, 추후에 다른 method로 접근할때 index를 명시하면 index가 붙은 value로만 조회가능해진다. -> 메모리 최적화
- ex:

  ```solidity
  contract A {
    event info(uint num, string str);
    event info2(uint indexed num, string str);

    uint num = 0;

    function pushEvent(string memory _str) public {
      emit info(num, _str);
      emit info2(num, _str);
      num++;
    }
  }
  ```
