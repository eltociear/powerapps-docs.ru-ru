---
title: Функция ShowError | Документация Майкрософт
description: Справочные сведения о функции ShowError в PowerApps, включая описание синтаксиса и примеры
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3ceb6e0bcac83bbd79d78dac859a7ddb7acf42a8
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61519775"
ms.PowerAppsDecimalTransform: true
---
# <a name="notify-function-in-powerapps"></a>Функция Notify в PowerApps
Отображает баннер с сообщением для пользователя.

## <a name="description"></a>Описание
Функция **Notify** отображает баннер с сообщением для пользователя в верхней части экрана поверх текущего содержимого.  

Используемые цвет и значок зависят от типа сообщения.   Тип определяется вторым аргументом функции.

| Аргумент NotificationType | Описание |
| --- | --- |
| **NotificationType.Error** | Выводится сообщение об ошибке. |
| **NotificationType.Information** (по умолчанию) | Выводится информационное сообщение.  |
| **NotificationType.Success** | Выводится сообщение об успешном выполнении. |
| **NotificationType.Warning** | Выводится предупреждение. |

Сообщения отображаются как при разработке, так и при использовании приложения.

Функция **Notify** может использоваться только в [формулах поведения](../working-with-formulas-in-depth.md).

Функцию **Notify** можно использовать совместно с функцией [**IfError**](function-iferror.md) для определения ошибок и выдачи пользовательских сообщений об ошибках.

PowerApps может также отправлять push-уведомления из функции **Notify** с помощью совершенно другого механизма.  Дополнительные сведения см. в статье [Отправка push-уведомлений в PowerApps](../add-notifications.md).

Функция **Notify** всегда возвращает *true*.

Примечание. Эта функция ранее называлось **ShowError** когда он может отображать только сообщения об ошибках.

## <a name="syntax"></a>Синтаксис
**Notify**(*Message*; [*NotificationType*])

* *Message* — обязательный аргумент.  Сообщение, отображаемое для пользователя.
* *NotificationType* — необязательный аргумент.  Тип сообщения для отображения из приведенной выше таблицы.  Тип по умолчанию — **NotificationType.Information**.  

## <a name="examples"></a>Примеры

### <a name="step-by-step"></a>Шаг за шагом

1. Добавьте элемент управления **Button** на экран.

2. Укажите следующее значение для свойства **OnSelect** элемента управления **Button**:

    **Notify(Hello; World)**

3. Нажмите кнопку.  

    При каждом нажатии на кнопку для пользователя будет отображаться информационное сообщение **Hello, World**.

    ![Вызов функции Notify из метода Button.OnSelect и отображение сообщения "Hello, World" в виде синего баннера в среде разработки](media/function-showerror/hello-world.png)

4. Измените тип сообщения на сообщение об ошибке.  Добавьте в формулу второй аргумент:

    **Notify("Hello, World"; NotificationType.Error)**

5. Нажмите кнопку.

    Теперь при каждом нажатии кнопки для пользователя будет отображаться сообщение об ошибке **Hello, World**.

    ![Вызов функции Notify из метода Button.OnSelect и отображение сообщения "Hello, World" в виде красного баннера в среде разработки](media/function-showerror/hello-world-error.png)

4. Измените тип сообщения на предупреждение.  Измените второй аргумент в формуле:

    **Notify("Hello, World"; NotificationType.Warning)**

5. Нажмите кнопку.

    Теперь при каждом нажатии кнопки для пользователя будет отображаться предупреждение **Hello, World**.

    ![Вызов функции Notify из метода Button.OnSelect и отображение сообщения "Hello, World" в виде оранжевого баннера в среде разработки](media/function-showerror/hello-world-warning.png)

4. Измените тип сообщения на сообщение об успешном выполнении.  Измените второй аргумент в формуле:

    **Notify("Hello, World"; NotificationType.Success)**

5. Нажмите кнопку.

    Теперь при каждом нажатии кнопки для пользователя будет отображаться сообщение об успешном выполнении **Hello, World**.

    ![Вызов функции Notify из метода Button.OnSelect и отображение сообщения "Hello, World" в виде зеленого баннера в среде разработки](media/function-showerror/hello-world-success.png)
