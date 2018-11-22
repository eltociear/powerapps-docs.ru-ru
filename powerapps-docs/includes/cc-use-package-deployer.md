Средство Package Deployer доступно как [пакет NuGet](https://go.microsoft.com/fwlink/?linkid=859205). Чтобы использовать Package Deployer, необходимо загрузить и извлечь его на локальный компьютер с помощью файла **nuget.exe.**<br/><br/>

Загрузите файл **nuget.exe** с сайта <https://www.nuget.org/downloads> и сохраните его на компьютере, например на диске **d:\\**. Затем выполните следующую команду в командной строке, чтобы извлечь содержимое пакета в папку, например **PD**, на компьютере.<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
После извлечения средства Package Deployer перейдите в папку `[ExtractedLocation]\tools`, чтобы найти файл **PackageDeployer.exe**. 
