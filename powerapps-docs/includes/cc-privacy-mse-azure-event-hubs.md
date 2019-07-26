---
ms.openlocfilehash: 29226cfe8ab5c0ad01b785cfdaeec2e12a230dd7
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225322"
---
Если подключить Social Engagement к [Центрам событий Azure](https://azure.microsoft.com/documentation/articles/event-hubs-overview/), данные из социальных сетей будут передаваться потоком в Центры событий с помощью правил автоматизации. В Центрах событий Azure хранятся данные социальных сетей, которые передавались потоком из Social Engagement в течение [предварительно заданного периода времени](https://azure.microsoft.com/documentation/articles/event-hubs-availability-and-support-faq/). Любое приложение, которое может ожидать передачи данных в центр событий, сможет получить доступ к этим данным, а также хранить и обрабатывать их.  
  
 Обратите внимание, что данные социальных сетей, отправленные из Social Engagement, включают сведения о публикации в социальной сети (автор и текст) а также расширенные сведения, такие как язык, расположение, тональность, теги и т. д. Подробные сведения о содержимом публикации в социальной сети, которое передается в Центры событий, см. в статье [Справочник по JSON для событий Social Engagement](http://go.microsoft.com/fwlink/p/?LinkId=786643).