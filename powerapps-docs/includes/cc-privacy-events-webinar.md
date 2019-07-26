---
ms.openlocfilehash: fa4a17c2a3131f49f8a702388bdb405661855c10
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2019
ms.locfileid: "61550026"
---
После принятия условий для управления событиями активируется функция интеграции веб-семинара. Функция интеграции веб-семинара использует поставщика веб-семинара партнера для проведения события или сеанса как веб-семинара. Чтобы использовать все службы поставщика веб-семинара, необходимо создать у него свою учетную запись. Единственная готовая в настоящее время служба поставщика веб-семинара партнера — это ON24. При использовании функции интеграции веб-семинара данные, необходимые для обеспечения и проведения веб-семинара, будут обрабатываться и храниться на [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)], а затем отправляться в ON24. К этим данным относятся регистрационные данные участников веб-семинара, такие как имена, адреса электронной почты и названия компаний. Кроме того, служба ON24 отправляет метрики веб-семинара, такие как длительность просмотра, на [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] через [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)].

Чтобы использовать остальную часть решения управления событиями, не нужно активировать функцию веб-семинара. Администратор может отключить функцию интеграции веб-семинара, удалив учетные данные из конфигурации веб-семинара.

Ниже приведены компоненты и службы [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)], используемые функцией интеграции веб-семинара.

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Что такое Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis))
  - Предоставляет ключ для шифрования и расшифровки учетных данных клиента ON24
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Общие сведения об Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview))
  - Обрабатывает и отправляет регистрационные данные и учетные данные веб-семинара на ON24
  - Получает метрики веб-семинара от On24 и отправляет их в [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] — хранит учетные данные клиента для ON24 (зашифрованные пользователем)