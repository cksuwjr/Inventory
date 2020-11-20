# Inventory 간단한 인벤토리 구현
<br>
<br>
- Unity 2019.4.13f1 에서 구현됨.<br>
<br>

## ex)
<div>
<img width="350" src="https://user-images.githubusercontent.com/63836325/99794986-64a71300-2b6e-11eb-983f-389ae739f546.PNG">
<img width="350" src="https://user-images.githubusercontent.com/63836325/99794994-6670d680-2b6e-11eb-8016-8ea25f0724f3.PNG">
<img width="350" src="https://user-images.githubusercontent.com/63836325/99795007-68d33080-2b6e-11eb-8248-5c46b1f750bf.PNG">
</div>
<h2>★ 2020-11-18 ★ <br></h2>
<br>
실행시 인벤토리 슬롯 자동 생성<br>
아이템 습득시 인벤토리에 저장<br>
동일 아이템은 개수 증가 처리, 다른 아이템은 다른 슬롯으로 이동<br>
<br>
인벤토리 개수 8개로 설정됨. 개수 설정 가능(C#코드 내부에서)<br>
인벤토리 개수 초과해서 아이템 획득시 <br>
해당 아이템 획득 못하게 설정<br>
<br>
획득시 텍스트 발생<br>
<br>
<br>
<h2>★ 2020-11-20 ★ <br></h2>
<br>
Assets 폴더 안의 Resources 안에 Inventory 폴더 생성 및 관련 파일 정리<br>
<br>
이제 Resources안의 Inventory 폴더만 복사해서 다른 유니티 프로젝트에 붙여넣으면<br>
바로 인벤토리 기능을 사용할 수 있다. <br>
<br>
<br>
여기있는 README.md 파일을 읽지않고 Resources 내부의 Inventory만 복사해서 쓸 수 있는 사람이나<br>
나중에 혹시 까먹게 될 나를 대비해서 그 폴더 안에도 따로 ReadMe.txt를 작성해놓았다.
<br>
<br>
ReadMe.txt의 내용은 아래와 같이 작성했다..<br>
<br>
<h5>〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓 필독!! 〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓<br></h5>
● Input_this_into_Scene 안에 있는 프리팹들을 작동시킬 Scene안에 꼭!! 넣어주세요.<br>
● 이 Inventory 폴더는 Resources 폴더 안에 들어있어야합니다.<br>
● Player에게 Player태그를 꼭 넣어주세요. 그렇지 않으면 아이템이 먹어지지 않습니다.<br>
<br>
     위 조건이 만족해야 정상 동작합니다.<br>
     (코드 내부의 경로를 그렇게 지정해놓았습니다.)<br>
<br>
● i 키를 누르면 인벤토리를 열 수 있습니다.<br>
● 플레이어 위치에 따라 아이템이 스폰되기 때문에 높이가 안맞을 수도 있습니다.<br>
    코드에서 직접 조정해주세요.  <br>
<br>
<h5>〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓 폴더별 설명 〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓<br></h5>
● Input_this_into_Scene : 위 1과 같습니다.<br>
● Items :     <br>
○ Image : 아이템 프리팹 제작에 사용된 사진 파일들을 보관<br>
○ Prefabs : Items 폴더내의 리소스들로 만든 프리팹들 보관<br>
○ Materials : 아이템 프리팹 제작에 사용된 Material 보관 <br>
● Scripts : Item 및 Inventory 제작에 사용된 코드들 보관.<br>
● Slot : Inventory 에 추가될 Slot 프리팹 보관<br>
<br>
<h5>〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓 스크립트별 설명 〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓〓<br></h5>
<br>
● GameMessage.cs  :  아이템 획득시 문구를 띄웁니다. <br>
 ○ 인벤토리ONOFF에 따라 위치가 달라집니다.<br>
 ○ Item.cs로부터 msg를 전달받아 화면에 띄웁니다.<br>
 ○ 코드 변경시 : 띄울 위치 조정 및 시간조정이 가능합니다.<br>
<br>
● InventoryManager.cs  :  인벤토리 내에 슬롯을 생성합니다.<br>
 ○ Scene이 시작되면 슬롯을 생성하고 ItemDatabase.cs를 초기화합니다.<br>
 ○ 코드 변경시 : 인벤토리 내 슬롯 생성 위치 조정 가능 및 슬롯 생성 개수 지정 가능<br>
<br>
● InventoryOnOFF.cs  :  인벤토리 OnOff를 가능하게 합니다. <br>
 ○ 코드 변경시 : 인벤토리 OnOff 를 실행하는 키를 변경가능합니다.<br>
<br>
● Item.cs  :  아이템 고유 이름을 지정하고 인벤토리 내의 슬롯을 채웁니다.<br>
 ○ 아이템 습득시 띄울 문구를 GameMessage.cs로 전달합니다. <br>
 ○ 즉, 아이템 습득시 띄워지는 메시지를 조정 가능합니다.<br>
 ○ 코드 변경시 : 아이템을 채우는 메서드의 알고리즘 조정과 아이템 태그별 이름 설정이 가능합니다.<br>
<br>
● ItemDatabase.cs  :  아이템 별 Slot.cs 의 Contained에 따라 슬롯의 이미지를 변경합니다.<br>
 ○ 코드 변경시 : Contained의 번호에 따른 아이템 슬롯에 띄울 이미지 조정이 가능합니다.<br>
<br>
● ItemSpawner.cs  :   플레이어 근처에 아이템을 무작위로 스폰합니다.<br>
 ○ 코드 변경시 : 스폰 개수, 타입, 위치 조정이 가능합니다.<br>
<br> 
● Slot.cs  :  아이템의 고유 정보를 담을 수 있습니다.<br>
 ○ 코드 변경시 : 담을 고유 정보를 변경, 추가할 수 있습니다.<br>
<br>
<br>
