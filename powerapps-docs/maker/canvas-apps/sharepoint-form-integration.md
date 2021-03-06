---
title: Общие сведения об интеграции форм SharePoint | Документация Майкрософт
description: Возможности настраиваемых форм в SharePoint
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9befcf4cb0e7267820c62ab78a14ee28ba985490
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732379"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-sharepoint-forms-integration"></a>Общие сведения об интеграции форм SharePoint
Теперь можно легко [настроить любую форму списка SharePoint](customize-list-form.md) в Power Apps. В этой статье мы подробно рассмотрим, как работают эти формы и как их можно настроить.

Если вы уже настраивали форму для списка SharePoint, вероятно вы заметили, что созданная по умолчанию форма подходит для всех операций, включая создание, отображение или изменение элементов. Это возможно благодаря созданным формулам и элементу управления **SharePointIntegration**.

## <a name="understand-the-default-generated-form"></a>Общие сведения о созданной по умолчанию форме

Созданная по умолчанию форма состоит из следующих элементов управления и их соответствующих значений по умолчанию:

* **FormScreen1** — это [экран](controls/control-screen.md), на котором содержится форма.

* **SharePointForm1** — это [форма](working-with-forms.md), используемая для создания, отображения или изменения элемента списка.

    * **DataSource** — список, для которого настроена форма.

    * **Item** — выбранный в списке элемент. Этот элемент имеет значение First () в списке для удобства при работе в Power Apps Studio.

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected);First('*имя_вашего_списка*');SharePointIntegration.Selected)**

    * **OnSuccess** — когда элемент успешно создан или сохранен, настройки формы сбрасываются и SharePoint скрывает форму.

        **ResetForm(SharePointForm1);; RequestHide()**

* **SharePointIntegration** — элемент управления, отвечающий за взаимодействие пользовательских действий между SharePoint и Power Apps.

    * **DataSource** — список, для которого настроена форма.

        **'*YourListName*'**

    * **OnNew** — переводит **SharePointForm1** в режим создания.

        **NewForm(SharePointForm1)**

    * **OnView** — переводит **SharePointForm1** в режим просмотра.

        **ViewForm(SharePointForm1)**

    * **OnEdit** — переводит **SharePointForm1** в режим редактирования.

        **EditForm(SharePointForm1)**

    * **OnSave** — отправляет изменения в **SharePointForm1**. После успешной отправки формы выполняется формула **SharePointForm1.OnSuccess**.

        **SubmitForm(SharePointForm1)**

    * **OnCancel** — сбрасывает изменения в **SharePointForm1**. SharePoint всегда скрывает форму, когда пользователь нажимает кнопку **Отмена** в SharePoint.

        **ResetForm(SharePointForm1)**

Эти значения по умолчанию обеспечивают работу формы при работе в SharePoint. они изменяют режим формы Power Apps при взаимодействии пользователя с ним в SharePoint и гарантируют, что изменения отправляются в SharePoint.

## <a name="understand-the-sharepointintegration-control"></a>Общие сведения об элементе управления SharePointIntegration
Элемент управления **SharePointIntegration** взаимодействует с пользовательскими действиями SharePoint и Power Apps.

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>Доступ к свойствам элемента управления **SharePointIntegration** можно получить только в том случае, если форма выполняется в SharePoint, а не при настройке формы в Power Apps Studio. Эти свойства могут быть недоступны в **OnStart** или **OnVisible**. 

Элемент управления **SharePointIntegration** имеет следующие свойства:

**Selected** — элемент, выбранный в списке SharePoint.

**OnNew** — поведение приложения, когда пользователь нажимает кнопку **Создать** или открывает форму **Создание элемента** в SharePoint.

**OnView** — поведение приложения, когда пользователь выбирает **элемент** или открывает форму **Сведения об элементе** в SharePoint.

**OnEdit** — поведение приложения, когда пользователь нажимает кнопку **Изменить все** или открывает форму **Изменение элемента** в SharePoint.

**OnSave** — поведение приложения, когда пользователь нажимает кнопку **Сохранить** в SharePoint.

**OnCancel** — поведение приложения, когда пользователь нажимает кнопку **Отмена** в SharePoint.

**SelectedListItemID** — идентификатор элемента, выбранного в списке SharePoint.

**DataSource** — список, используемый для просмотра, изменения и создания записи в форме. Обратите внимание: если изменить это свойство, свойства **Selected** и **SelectedItemID** могут перестать работать.

## <a name="customize-the-default-form"></a>Настройка формы по умолчанию
Теперь, когда вы узнали больше о созданной по умолчанию форме и элементе управления **SharePointIntegration**, вы можете изменить формулы для дальнейшей настройки форм. При настройке форм следует учитывать следующее:

* Чтобы создать отдельные пользовательские интерфейсы для создания, отображения или изменения элементов, задайте формулы **OnNew**, **OnView** или **OnEdit** элемента управления **SharePointIntegration** для определения переменных или переходов между разными экранами.

* Используйте формулу **OnSave** элемента управления **SharePointIntegration** для настройки поведения приложения, когда пользователь нажимает кнопку **Сохранить** в SharePoint. Если у вас есть несколько форм, отправляйте изменения только для формы, используемой сейчас.

  > [!TIP]
  >    Задайте разные значения для переменной в формулах **OnNew**, **OnView** и **OnEdit**. Вы сможете использовать эту переменную в формуле **OnSave**, чтобы определить, какая форма используется.

* Необходимо добавить **RequestHide()** в формулу **OnSuccess** для всех форм. В противном случае SharePoint не будет знать, когда скрыть форму.

* Вы не можете управлять скрытием формы, когда пользователь нажимает кнопку **Отмена** в SharePoint. Поэтому сбросьте форму в формуле **OnCancel** элемента управления **SharePointIntegration**.

* Свойства элемента управления **SharePointIntegration** могут быть недоступны в **OnStart** или **OnVisible**. Эти события выполняются только один раз при загрузке списка. Формулы **OnNew**, **OnView** или **OnEdit** можно использовать для запуска логики перед каждым отображением формы пользователю. 
