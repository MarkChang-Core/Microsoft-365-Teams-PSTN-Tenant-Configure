# **使用PowerShell登入Teams**
### **Step1. 載入Teams Module**
PS> Import-Modulle MicrosoftTeams
![GITHUB]( 圖片網址 "圖片名稱")
### **Step2. 登入Microsoft 365 (Global Admin)**
PS> $sfbSession = New-CsOnlineSession
