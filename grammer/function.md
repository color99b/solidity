# 함수

- 기본 틀

```solidity
function 이름 () 접근연산자 {
  내용
}
```

- 유형

  - 1. Parameter 와 return 이 없는 경우 : 단순 변수 변경 등

    ```solidity
    uint public a = 3;
    function changeValue () public {
      a=5;
    }
    ```

  - 2. Parameter는 있고 return 값이 없는 경우
    ```solidity
    function changeValue2(uint _value) public {
      a = _value;
    }
    ```
  - 3. parameter 도 있고 return 도 있는 경우

    ```solidity
    function changeValue3 (uint _value) public returns (리턴할값의 type) {

    }

     function changeValue3 (uint _value) public returns (uint256) {
      a = _value;
      return a;
    }
    ```

- pure vs view vs none
  - pure : function 밖의 변수들을 읽지 못하고, 변경도 불가능한 순수함수
  - view : 밖의 변수들을 읽을 수 있으나 변경 불가능
  - none(명시없음) : function 밖의 변수들을 읽어서, 변경까지 한다.
  - pure와 view는 함수의 결과값이 명시가 되는데 명시하지 않으면 return으로 담아줘야한다.

```solidity
uint256 public a =1;

function read_a() public view returns(uint256){
  return a+2; // a의 값을 변경하는 것이 아닌 단순 return
}

function read_a2() public pure returns(uint256){
  uint256 b = 1;
  return 4+2+b;
}

function read_a3() public returns(uint256){
  a=13;
  return a;
}
```
