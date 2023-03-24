# FPS 게임 이상 유저 탐색

## :four_leaf_clover: 소개
- A게임은 최근 **신규 유저들이 증가**하면서 **버그 유저들도 함께 증가**해 **기존 이용자의 이탈률이 높아지는 문제**가 발생하고 있습니다.
- 버그 사용이 의심되는 유저를 색출하여 **게임을 정상화할 필요**가 있습니다.
- 버그가 의심되는 **유저의 행동 패턴을 정의**하고 **이상 유저를 검출**하려고 합니다.

----------------------------

## :four_leaf_clover: 결론
- **이동거리가 짧은 데 반해 무기 획득횟수가 많은** 유저를 색출했습니다.
- **이동거리는 짧은 데 반해 헤드샷킬(Headshotkills) 비율이 높은** 유저를 색출했습니다.
- **헤드샷킬(Headshotkills) 비율이 100%** 인 유저를 색출했습니다.
- **힐(Heals) 아이템 사용이 지나치게 높은** 유저를 색출했습니다.
- **힐(Heals) 아이템의 사용 없이 킬수가 높은** 유저를 색출했습니다.

<br/>
<br/>

--------------------------

## :four_leaf_clover: 모델링
**실제 인게임 플레이 경험을 바탕**으로 이상 유저를 정의했습니다.

<br/>
<br/>
<br/>

### 1) 이동거리는 짧으면서 무기 획득횟수가 많은 유저

<br/>

- **총 이동거리(탈것 + 도보 + 수영)가 하위 10%** 이면서 동시에 **무기획듯횟수가 상위 10%** 인 유저를 버그사용 의심 유저로 분류했습니다. (2,265명 1차 분류)
- 그 중에서 **무기획득 횟수가 50회 이상**인 유저를 이상유저로 정의했습니다. (최종 10명 색출)

<br/>

![image](https://user-images.githubusercontent.com/56102116/227458563-9946bdf6-2baf-455d-9dce-2f5595fae241.png)

<br/>
<br/>

### 2) 이동거리는 짧으면서 헤드샷킬 비율이 높은 유저

<br/>

- **총 이동거리(탈것 + 도보 + 수영)가 하위 10%** 이면서 동시에 **헤드샷킬 비율이 80%가 넘는** 유저를 버그사용 의심 유저로 분류했습니다. (9,276명 1차 분류)
- 그 중에서 **킬 수가 7 이상**인 유저를 이상유저로 정의했습니다. (최종 5명 색출)

<br/>

![image](https://user-images.githubusercontent.com/56102116/227459052-b8bdab18-a7bb-454a-ad1a-5fa2d9e6a36e.png)

<br/>
<br/>

### 3) 헤드샷킬 비율이 100%인 유저

<br/>

- **킬 수가 적으면서 헤드샷킬 비율이 100%인 유저는 다수** 존재할 수 있습니다.
- 따라서 **헤드샷킬 비율이 100%이면서 킬 수가 10 이상** 인 유저를 이상유저로 정의했습니다. (최종 8명 색출)

<br/>

![image](https://user-images.githubusercontent.com/56102116/227459447-d4414228-4946-4761-89c4-16f2f5da2d93.png)

<br/>
<br/>

### 4) 힐 아이템 사용이 지나치게 많은 유저

<br/>

- **힐(Heals) 아이템 사용횟수가 지나치게 많은** 유저는 버그 사용이 의심됩니다.
- **힐 아이템 사용횟수가 50회 이상**인 유저를 이상유저로 정의했습니다. (최종 3명 색출)

<br/>

![image](https://user-images.githubusercontent.com/56102116/227460321-e62f0464-f057-46d3-90f0-3b8e8233ae2f.png)

<br/>
<br/>

### 5) 힐 아이템의 사용없이 킬 수가 높은 유저

<br/>

- **힐(Heals) 아이템 사용횟수가 0** 이면서 **킬 수 평균의 3표준편차 이상** 인 유저를 버그사용 의심 유저로 분류했습니다. (8,238명 1차 분류)
- **힐 아이템 사용횟수가 0** 이면서 **킬 수가 30 이상** 인 유저를 이상유저로 정의했습니다. (최종 10명 색출)

<br/>

![image](https://user-images.githubusercontent.com/56102116/227461564-080228a5-d5e9-425a-bad7-3ef29aef7f00.png)

<br/>
<br/>


