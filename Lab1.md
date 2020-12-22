# **使用PowerShell登入Teams**

  建議使用PowerShell ISE操作，並已系統管理員身分執行PowerShell ISE

  - **Step1. 載入Teams Module**
  ```Import-Module MicrosoftTeams```<br>

  - **Step2. 登入Microsoft 365 (Global Admin)**
  ```$sfbSession = New-CsOnlineSession```<br>

    ![GITHUB](image/image1.jpg "Connect Microsoft 365")<br>

  - **Step3. 載入PowerShell Session**
  ```Import-PSSession $sfbSession -allowclobber```<br>
  
  - **Step4. 新增PSTN Gateway**
  ```New-CsOnlinePSTNGateway -Identity ***yourdomain.com.tw*** -Enabled $true -SipSignalingPort 5109 -ForwardCallHistory $true```
  請將yourdomain.com.tw，更換為TeleProvider提供的Sub-domain<br>
