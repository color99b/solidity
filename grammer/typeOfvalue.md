# 자료형

- data에 의한 데이터타입 : 값 자체를 저장함

  - 기본 데이터 타입은 parameter나 return될때 default가 memory 이기때문에 memory 굳이 추가하지 않아도 된다.

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

  - array : 다른 언어와 마찬가지로 탐색, 길이, 수정, 추가, 삭제 등이 가능하다.
    하지만 solidity에서는 array 보다 mapping을 사용한다. 사용하게 되면 권장길이는 50이하이다.
    - 이유는 탐색때문인데, mapping(key의 hash와 value)형태가 아닌 배열은 index가 존재하고, index에 따라 차례대로 탐색이 가능하다. 이는 dos 공격에 취약하며, 탐색을 반복시키면 가스값이 오른다.
    - ex: 자료형[ (size | "") ] 접근연산자 (valueName)
    ```solidity
    contract a {
      uint[] public ageArray;
    }
    ```
    - delete : 해당 value를 0으로 만든다. (배열의 길이 수정 x : pop, shift와 다름)
      - ex: delete 배열명[index];
      ```solidity
      // ageArray = [1, 5, 6, 7] , length = 4이다.
      delete ageArray[2];  //
      // delte 후 ageArray = [1, 5, 0, 7] , length = 4이다.
      ```

- reference에 의한 데이터타입 : 값이 저장된 주소값을 저장함

  - string : 포인터 개념으로 string이 js처럼 딱 저장되는 게 아니라 저장되는 위치의 시작주소를 나타내는 것이기 때문에
    solidity 에서는 단순비교나 단순 명시(매개변수로 받을때, returns 자료형 명시할때)를 할 수 없다. (keccak 등으로 hash화후 비교를 하던가) (memory를 붙여서 사용한다.)

    ```solidity
    function get_string(
      string memory _str
    ) public pure returns (string memory) {
      return _str;
    }
    ```

      <br>

- mapping에 의한 데이터타입 : {key : value} 상태로 저장하고, 이때의 key는 입력한 data를 기준으로 hash화 하여 저장.
- 저장방식이 reference vs data 로 따지면 data기 때문에, 원본을 바꿔도 mapping data에는 영향이 미치지 않는다.

  - 기본문법 : mapping(key값의 type => value값의 type) [접근지정자] [mapping value 이름]
  - key와 value로 이루어져있기에 length가 존재하지 않는다.

  ```solidity
  contract a {
    mapping(uint => uint) private ageList;

    function setAgeList(uint _index, uint _age) public {
      ageList[_index] = _age;
    }

    function getAge(uint _index) public view returns (uint) {
      return ageList[_index];
    }
  }
  ```
