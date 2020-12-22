# **使用PowerShell登入Teams**

  - **Step1. 載入Teams Module**<br>
  ```Import-Module MicrosoftTeams```<br>

  - **Step2. 登入Microsoft 365 (Global Admin)**<br>
  ```$sfbSession = New-CsOnlineSession```<br>

    ![GITHUB](image/image1.jpg "Connect Microsoft 365")<br>

  - **Step3. 載入PowerShell Session**<br>
  ```Import-PSSession $sfbSession -allowclobber```<br>
   
    ![GITHUB](image/image2.jpg "PowerShell Session Import")<br>
  
  - **Step4. 新增PSTN Gateway**<br>
  ```New-CsOnlinePSTNGateway -Identity ***yourdomain.com.tw*** -Enabled $true -SipSignalingPort 5109 -ForwardCallHistory $true```<br>
  
    請將yourdomain.com.tw，更換為TeleProvider提供的Sub-domain<br>
  
    ![GITHUB](image/image3.jpg "PowerShell Session Import")<br>
  
  - **Step5. 驗證SBC是否已存在於匹配清單之中**<br>
  ```Get-CsOnlinePSTNGateway -Identity yourdomain.com.tw```
 
    ![GITHUB](image/image4.jpg "PowerShell Session Import")<br>
  
