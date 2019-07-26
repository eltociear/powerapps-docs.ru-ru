---
ms.openlocfilehash: 215a6d9fb0890bd6d93843b0b649ada4203e5600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224208"
---
Получите файлы PowerShell для средства развертывания пакетов Package Deployer. Файлы PowerShell для средства Package Deployer доступны как [пакет NuGet](https://go.microsoft.com/fwlink/?linkid=859211). Чтобы их использовать, необходимо загрузить и извлечь его на локальный компьютер с помощью файла **nuget.exe**.<br/><br/>

Скачайте файл **nuget.exe** с <https://www.nuget.org/downloads> и сохраните его на компьютере, например на диске **d:\\** . Затем выполните следующую команду в командной строке, чтобы извлечь содержимое пакета в папку, например **PD-PowerShell**, на компьютере:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
После извлечения файлов PowerShell для средства Package Deployer перейдите в папку `[ExtractedLocation]\tools`. 
