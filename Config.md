# **Create a trunk and provision users**

  - **Step1. 載入Teams Module**<br>
  ```Import-Module MicrosoftTeams```<br>

  - **Step2. 登入Microsoft 365 (Global Admin)**<br>
  ```$sfbSession = New-CsOnlineSession```<br>

    ![GITHUB](image/image1.jpg "Connect Microsoft 365")<br>

  - **Step3. 載入PowerShell Session**<br>
  ```Import-PSSession $sfbSession -allowclobber```<br>
   
    ![GITHUB](image/image2.jpg "PowerShell Session Import")<br>
  
  - **Step4. 新增PSTN Gateway**<br>
  ```New-CsOnlinePSTNGateway -Identity ***yoursubdomain.com.tw*** -Enabled $true -SipSignalingPort 5109 -ForwardCallHistory $true```<br>
  
    請將yoursubdomain.com.tw，更換為TeleProvider提供的Sub-domain<br>
  
    ![GITHUB](image/image3.jpg "PowerShell Session Import")<br>
  
  - **Step5. 驗證SBC是否已存在於匹配清單之中**<br>
  ```Get-CsOnlinePSTNGateway -Identity yourdomain.com.tw```
 
    ![GITHUB](image/image4.jpg "PowerShell Session Import")<br>
  
  - **Step6. 增加Usage**<br>
  ```Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="Unrestricted"}```
 
  - **Step7. 驗證增加後的Usage**<br>
  ```Get-CsOnlinePstnUsage -Identity Global```
  
    ![GITHUB](image/image5.jpg "PowerShell Session Import")<br>

  - **Step8. 設定語音路由規則**<br>
  ```New-CsOnlineVoiceRoutingPolicy "Unrestricted" -OnlinePstnUsages "Unrestricted"```
  
    ![GITHUB](image/image6.jpg "PowerShell Session Import")<br>

  - **Step9. 驗證新的語音路由規則**<br>
  ```Get-CsOnlineVoiceRoutingPolicy```
  
    ![GITHUB](image/image7.jpg "PowerShell Session Import")<br>
    
  - **Step10. 新增語音路由**<br>
  ```New-CsOnlineVoiceRoute -Identity "Unrestricted" -NumberPattern ".*" -OnlinePstnGatewayList yoursubdomain.com.tw -Priority 1 -OnlinePstnUsages "Unrestricted"```
  
    請將yoursubdomain.com.tw，更換為TeleProvider提供的Sub-domain<br>
  
    ![GITHUB](image/image8.jpg "PowerShell Session Import")<br>    

  - **Step11. 驗證新的語音路由**<br>
  ```Get-CsOnlineVoiceRoute -Identity “Unrestricted"```
  
    ![GITHUB](image/image9.jpg "PowerShell Session Import")<br>    
  
    
