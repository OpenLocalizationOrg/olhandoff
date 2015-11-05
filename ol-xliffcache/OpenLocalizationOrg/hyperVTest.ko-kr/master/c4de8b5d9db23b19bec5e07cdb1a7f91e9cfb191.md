ms입니다. ContentId: B9414110-BEFD-423F-9AD8-AFD5EE612CDA
제목: 8 단계: Windows PowerShell을 사용한 실험

#8 단계: Windows PowerShell을 사용한 실험

Hyper-v를 배포, 가상 컴퓨터 만들기 및 이러한 가상 컴퓨터를 관리 하는 기본으로 살펴보았습니다 했으므로 자동화할 수 있는 방법을 다양 한 PowerShell 사용 하 여 이러한 활동을 살펴보겠습니다.

###Hyper-v 명령 목록을 반환 합니다.

1.  형식 Windows 시작 단추를 클릭 하십시오. **PowerShell**.
2.  Hyper-v PowerShell 모듈과 함께 사용할 수 있는 PowerShell 명령의 검색 가능한 목록을 표시 하려면 다음 명령을 실행 합니다.

 ```powershell
get-command –module hyper-v | out-gridview
 ```
다음과 같은 결과 얻게:

![](media\command_grid.png)

3. 특정 PowerShell 명령 사용에 대 한 자세한 내용을 보려면 `도움말 얻기`.
   인스턴스에 대 한 다음 명령을 실행에 대 한 정보를 반환 합니다는 `get vm` Hyper-v 명령 합니다.

  ```powershell
get-help get-vm
  ```
출력 명령, 필수 및 선택적 매개 변수는 어떤 및 사용할 수 있는 별칭을 구성 하는 방법을 보여줍니다.

![](media\get_help.png)


###가상 컴퓨터의 목록을 반환 합니다.

사용 하는 `get vm` 명령이 가상 컴퓨터의 목록을 반환 합니다.

1. PowerShell에서 다음 명령을 입력 합니다.

 ```powershell
get-vm
 ```
다음과 같이 표시 됩니다.

![](media\get_vm.png)

2. 반환할 전원이 켜진 가상 컴퓨터의 목록이 필터를 추가 하는 `get vm` 명령 합니다.
   Where 개체 명령을 사용 하 여 필터를 추가할 수 있습니다.
   필터링에 대 한 자세한 내용은 참조는 [는 Where-object를 사용 하 여](https://technet.microsoft.com/en-us/library/ee177028.aspx) 설명서입니다.

 ```powershell
 get-vm | where {$_.State –eq ‘Running’}
 ```
3.  꺼져 모든 가상 컴퓨터를 나열 하려면 꺼짐 상태, 다음 명령을 실행 합니다.
   이 명령은 'Running'에서 'Off'으로 변경 된 필터와 2 단계에서 명령의 복사본입니다.

 ```powershell
 get-vm | where {$_.State –eq ‘Off’}
 ```

###시작 하 고 가상 컴퓨터 종료

1. 특정 가상 컴퓨터를 시작 하려면 가상 컴퓨터의 이름으로 다음 명령을 실행 합니다.

 ```powershell
 Start-vm –Name <virtual machine name>
 ```

2. 현재 모든 전원이 가상 컴퓨터가 꺼져를 시작 하려면 해당 컴퓨터의 목록을 가져오고 목록 ' 시작 vm' 명령에 파이프:

  ```powershell
 get-vm | where {$_.State –eq ‘Off’} | start-vm
  ```
3. 실행 중인 모든 가상 컴퓨터를 종료 하려면이 실행 합니다.

  ```powershell
 get-vm | where {$_.State –eq ‘Running’} | stop-vm
  ```

###VM 검사점 만들기

PowerShell을 사용 하 여 검사점을 만들려면 사용 하 여 가상 컴퓨터를 선택 된 `get vm` 명령 및이를 사용 하는 파이프는 `검사점 vm` 명령 합니다.
마지막으로 사용 하 여 이름을 검사점 제공 `-snapshotname`.
전체 명령은 다음과 같습니다.

 ```powershell
 get-vm -Name <VM Name> | checkpoint-vm -snapshotname <name for snapshot>
 ```
예를들어 다음은 DEMOCP 이름의 검사점이입니다.

![](media\POSH_CP2.png)

###새 가상 컴퓨터 만들기

다음 예제에서는 새 가상 컴퓨터에는 PowerShell 환경 ISE (통합 스크립팅)를 만드는 방법을 보여줍니다.
이 간단한 예 이며에 추가 PowerShell 기능 및 고급 VM 배포를 포함 하도록 확장할 수 있습니다.

1. 시작 시에 PowerShell ISE 클릭을 열려면 입력 **PowerShell ISE**.
2. 가상 컴퓨터를 만들려면 다음 코드를 실행 합니다.
   참조는 [NEW-VM](https://technet.microsoft.com/en-us/library/hh848537.aspx) NEW-VM 명령에 대 한 자세한 정보에 대 한 설명서입니다.

  ```powershell
 $VMName = "VMNAME"

 $VM = @{
     Name = $VMName 
     MemoryStartupBytes = 2147483648
     Generation = 2
     NewVHDPath = "C:\Virtual Machines\$VMName\$VMName.vhdx"
     NewVHDSizeBytes = 53687091200
     BootDevice = "VHD"
     Path = "C:\Virtual Machines\$VMName "
     SwitchName = (get-vmswitch).Name[0]
 }

 New-VM @VM
  ```

##지금까지 및 참조

이 문서는 일부 샘플 시나리오는 물론 Hyper-v PowerShell 모듈 탐색기에 몇가지 간단한 단계 나타났습니다.
PowerShell Hyper-v 모듈에 대 한 자세한 내용은 대 한 참조는 [Windows PowerShell 참조의 Hyper-v Cmdlet](https://technet.microsoft.com/%5Clibrary/Hh848559.aspx).




