# 자료형

- data에 의한 데이터타입 : 값 자체를 저장함

  - boolean : true or false (||, &&, ! 와 같은 연산자 사용가능)

  ```solidity
  bool public b1 = !fase;
  ```

  - bytes : 1~32 bytes 까지 저장을 할 수 있다.

  ```solidity
  bytes4 public bt = 0x1235678; //4btyes만 저장한다.
  bytes public bt2 = "String"; // string이 bytes화 되어 16진수로 저장된다.
  ```

  - address : 지갑계정주소
    ```solidity
    address public addr = 0x~~~; //20bytes 로 16진수 0x다음 문자열길이가 40
    ```
  - int, uint : 뒤에 숫자로 범위를 정해주지 않으면 256이 default이다. (uint asd == uint256 asd)
    - int8 : -2^7 ~ 2&7 -1 //부호가 있는 정수
    - uint8 : 0~ 2^8-1 // 부호가 없는 정수

- reference에 의한 데이터타입 : 값이 저장된 주소값을 저장함
  - string : 포인터 개념으로 string이 js처럼 딱 저장되는 게 아니라 저장되는 위치의 시작주소를 나타내는 것이기 때문에
    solidity 에서는 단순비교나 단순 명시(매개변수로 받을때, returns 자료형 명시할때)를 할 수 없다. (keccak 등으로 hash화후 비교를 하던가) (memory를 붙여서 사용한다.)
    ```solidity
    function get_string(string memory _str) public pure returns (string memory){
      return _str;
    }
    ```
- mapping에 의한 데이터타입 : {key : value} 상태로 저장하고, 이때의 key는 입력한 data를 기준으로 hash화 하여 저장.
