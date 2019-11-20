Файлы PowerShell для средства Package Deployer доступны как пакет [NuGet](https://go.microsoft.com/fwlink/?linkid=859211). Чтобы их использовать, необходимо загрузить и извлечь его на локальный компьютер с помощью файла **nuget.exe.**<br/><br/>

Загрузите файл **nuget.exe** с сайта <https://www.nuget.org/downloads> и сохраните его на компьютере, например на диске **d:\\**. Затем выполните следующую команду в командной строке, чтобы извлечь содержимое пакета в папку, например **PD-PowerShell**, на компьютере.<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
После извлечения файлов PowerShell для средства Package Deployer перейдите в папку `[ExtractedLocation]\tools`, чтобы найти необходимые файлы. 
