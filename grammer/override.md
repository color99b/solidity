# Overide

- 상속받은 method, value 등의 이름을 같은 이름의 다른 내용으로 덮어씌우는 것.
- override 당하는쪽 method는 virtual 이라고 명시해야하고, override 하는 쪽은 override 라고 명시를 해야한다.

  - 명시는 접근연산자 다음, return 앞에 한다.

- ex :
  아버지의 돈 100을 자식이 상속받고, 상속받은돈 + 일당만큼의 합의 재산을 가져오는 함수를 만드는데, 이름은 똑같다.

```solidity
contract Father{

  string public familyName = "kim"
  string public givenName = "YoungJun"
  uint public money = 100;
  construtor(string memory _givenName) public {
    givenName = _givenName
  }

  function getFamilyName() view public returns(string memory){
    return familyName;
  }
  //givenName 가져오는 함수
   function getMoney() view public virtual returns(uint){
    return money;
  }

}
contract Son is Father("chorong") {
  uint public earning = 0;
  function work()public {
    earning += 100;
  }

     function getMoney() view public override returns(uint){
    return money+earning;
  }

}
```
