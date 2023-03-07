# Solidity

- 정의 : smart contracts 개발을 위한 고급 언어

- gas : smart contracts 를 사용하는데 드는 비용(수수료)

  - 공식문서에 smart contracts 에서 사용하는 method 종류에 따라 드는 gas량이 정해져있음
  - smart contracts 코드 길이가 길어질수록 gas가 오르기 때문에 gas를 덜 오르게 코딩하는 것이 solidity 의 과제

- ether 단위

  - 1ether = 10^9 Gwei = 10^18 wei
  - 0.000000000000000001 ether = 10^-18 = 1 wei
  - Gwei : 가스를 낼 때 사용하는 단위

- 저장영역
  - storage : 대부분의 변수, 함수들이 저장되고, 영구적인 저장으로 가스 비용이 비싸진다.
  - memory : 함수내에서만 사용하고 함수가 끝나면 더 이상 저장하지 않는다. 함수의 파라미터, 리턴, 래퍼런스 type등이 주로 이용된다.
  - colldata : external function 의 파라미터에서 주로 사용
  - stack : EVM ( Ethereum Virtual Machine) 에서 stack data를 관리할 때 쓰는 영역

# Smart contracts

- 정의 : 미리 정의해둔 상태를 만족한다면 블록체인안에 저장된 프로그램이 자동적으로 작동하게하는 것
