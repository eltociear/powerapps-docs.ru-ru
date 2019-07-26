---
ms.openlocfilehash: a108a9ee6f9033851b2f55beb071a1e7cae254dd
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224239"
---
Средство Package Deployer доступно в виде [пакета NuGet](https://go.microsoft.com/fwlink/?linkid=859205). Чтобы воспользоваться Package Deployer, необходимо скачать и распаковать средство на локальном компьютере с помощью **nuget.exe**.<br/><br/>

Скачайте файл **nuget.exe** с <https://www.nuget.org/downloads> и сохраните его на компьютере, например на диске **d:\\** . Затем выполните следующую команду в командной строке, чтобы извлечь содержимое пакета в папку, например **PD**, на вашем компьютере:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
Распаковав средство Package Deployer, перейдите в папку `[ExtractedLocation]\tools` и найдите файл **PackageDeployer.exe**. 
