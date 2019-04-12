---
title: Создание и изменение полей для Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 02/08/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: d88677fa-2caf-47b0-aec6-10a25a7ec9c3
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="how-to-create-and-edit-fields"></a>Создание и изменение полей

В Common Data Service поля определяют отдельные элементы данных, которые можно использовать для хранения данных в сущности. Иногда разработчики называют поля *атрибутами*. 
  
Прежде чем создать настраиваемое поле, подумайте, будет ли существующее поле отвечать вашим требованиям. Дополнительные сведения: [Создание новых или использование существующих метаданных](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Имеется два конструктора, которые можно использовать для создания или изменения полей:

|Дизайнер| Описание|
|--|--|
|[Портал PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Обеспечивает простое модернизированное взаимодействие, но некоторые специальные параметры недоступны.<br />Дополнительные сведения: [Создание и изменение полей для Common Data Service с помощью портала PowerApps](create-edit-field-portal.md)|
|Обозреватель решений|Не так прост, но предоставляет больше гибкости для менее распространенных требований.<br />Дополнительные сведения: [Создание и изменение полей для Common Data Service с помощью обозревателя решений PowerApps](create-edit-field-solution-explorer.md) |

> [!NOTE]
> Можно также создать поля в среде с помощью следующих действий.
> - В управляемых моделью приложениях выберите **Создать поле** в редакторе форм.
> - Импорт решения, которое содержит определение полей.
> - Используйте Power Query для создания новых сущностей и из заполнения данными.<br />Дополнительные сведения: [Добавление данных в сущность в Common Data Service для приложений с помощью Power Query](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Разработчик может использовать [службы метаданных](/powerapps/developer/common-data-service/use-web-services#metadata-services), чтобы создать программу для создания и обновления полей.

Информация в этом разделе поможет вам выбрать конструктор для использования. 

Следует использовать портал PowerApps для создания и редактирования полей Common Data Service, кроме случаев, когда необходимо выполнить любое из следующих требований:

- Создание настраиваемого поля подстановки. 
   - Дополнительные сведения: [Различные типы поисков](types-of-fields.md#different-types-of-lookups)
- Создание поля в решении, отличном от решения по умолчанию Common Data Service. 
   - Дополнительные сведения: [Обзор решений](solutions-overview.md)
- Определение переходов причин состояния. 
   - Дополнительные сведения: [Определение переходов причин состояния для обращения или настраиваемых сущностей](define-status-reason-transitions.md)
- Изменение нескольких полей одновременно.
- Включение аудита. 
   - Дополнительные сведения: [Обзор аудита](../../developer/common-data-service/auditing-overview.md)
- Включение безопасности на уровне полей. 
   - Дополнительные сведения см. в разделе [Сущности безопасности на уровне полей](../../developer/common-data-service/field-security-entities.md).
- Выбор того, следует ли отображать поле в глобальном фильтре при интерактивном взаимодействии. 
   - Дополнительные сведения: [Настройка панелей мониторинга интерактивного взаимодействия управляемых моделью приложений](../model-driven-apps/configure-interactive-experience-dashboards.md)
- Выбор того, можно ли сортировать поле на панелях мониторинга интерактивного взаимодействия. 
   - Дополнительные сведения: [Настройка панелей мониторинга интерактивного взаимодействия управляемых моделью приложений](../model-driven-apps/configure-interactive-experience-dashboards.md)
- Задание уровня требования поля как "Бизнес-рекомендация". 
   - Дополнительные сведения: [Создание бизнес-правил и рекомендаций для применения логики в форме управляемого моделью приложения](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
- Задание управляемых свойств поля. 
   - Дополнительные сведения: [Задание управляемых свойств для полей](set-managed-properties-for-field.md)

> [!NOTE]
> Можно создать поле поиска на портале PowerApps или в обозревателе решений, создав отношение "один-ко-многим" в сущности. Но только обозреватель решений предлагает параметр для создания этого отношения во время создания поля.

## <a name="community-tools"></a>Средства сообщества

**[Attribute Manager](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)** — это средство, которое сообщество XrmToolbox разработало для Common Data Service. Дополнительные средства разработки от сообщества см. в разделе [Средства разработчика](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools).

> [!NOTE]
> Средства сообществ не являются продуктом корпорации Майкрософт, и на них не распространяется поддержка. При наличии вопросов по средству обращайтесь к его издателю. Дополнительные сведения: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>См. также  
[Создание и изменение полей для Common Data Service с помощью портала PowerApps](create-edit-field-portal.md)<br />
[Создание и изменение полей для Common Data Service с помощью обозревателя решений PowerApps](create-edit-field-solution-explorer.md)<br />
[Типы полей и типы данных полей](types-of-fields.md)<br />
[Документация для разработчиков. Работа с метаданными атрибута](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)
 
