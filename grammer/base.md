# 기본 문법

- 첫 줄은 무조건 license 명시
  ```solidity
  // SPDX-License-Identifier: MIT
  ```
  - identifier 와 : 사이에는 공백이 오면 안된다.
- 두 번째 줄은 version 명시
  ```solidity
  pragma solidity >=0.7.0 <0.9.0;
  pragma solidity ^0.8.18;
  ```
  위 두 개중 하나 사용
