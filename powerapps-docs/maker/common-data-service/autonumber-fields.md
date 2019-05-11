---
title: Автоматическая нумерация полей в Common Data Service | MicrosoftDocs
description: 'Узнайте, как создавать, контролировать и использовать поля с автоматической нумерацией'
keywords: ''
ms.date: 02/26/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: daemelia
ms.assetid: null
ms.author: daemelia
manager: kvivek
ms.reviewer: Mattp123
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="autonumber-fields"></a>Поля с автоматической нумерацией

Поля с автоматической нумерацией — это поля, которые автоматически формируют алфавитно-цифровые строки, когда они создаются. Создатели могут настраивать формат этих полей на свое усмотрение, а затем они полагаются на систему для генерации соответствующих значений, которые автоматически заполняют поля во время выполнения.

Хотя поля с автоматической нумерацией формально являются простыми текстовыми полями с дополнительной функцией, [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) упрощают эту концепцию, просто представляя **Автономер** как отдельный тип данных в категории **Текст**. Важно отметить, что [классический обозреватель решений](use-solution-explorer.md#classic-solution-explorer) не поддерживает создание или управление полями с автоматической нумерацией.

Для создания полей с автонумерацией выполните те же действия, что и для [создания полей](create-edit-field-portal.md#create-a-field), и просто выберите **Автонумерация** в раскрывающемся списке **Тип данных**. 

Можно также включить функцию автонумерации для существующего текстового поля, открыв поле и выбрав **Автонумерация** в раскрывающемся списке **Тип данных**. Аналогично, функцию автоматической нумерации также может отключить в любое время, открыв поле и выбрав другой параметр в раскрывающемся списке **Тип данных**.

## <a name="autonumber-types"></a>Типы автонумерации

Чтобы упросить создание полей с автонумерацией, существует несколько заранее определенных типов автонумерации по умолчанию, чтобы охватить самые распространенные сценарии. 

### <a name="string-prefixed-number"></a>Номер со строкой префикса

Самый распространенный формат автонумерации — номер с простой строкой префикса. При выборе этого типа автонумерация будет состоять из автоматически увеличивающегося числа и необязательной строки постоянного префикса. Например, номер со строкой префикса с префиксом *Contoso* формировал бы такие записи, как *Contoso-1000*, *Contoso-1001*, *Contoso-1002* и т. д.

### <a name="date-prefixed-number"></a>Номер с префиксом в виде даты

Другой общий формат автонумерации — номер с префиксом в виде даты. При выборе этого типа автонумерация будет состоять из автоматически увеличивающегося числа и префикса в виде форматированной даты. Часть записи, содержащая дату, будет отражать текущую дату и время создания записи в формате времени UTC. Мы предоставили несколько различных форматов даты на выбор.
Например, номер в префиксом в виде даты будет формировать такие записи, как *2019-26-02-1000*, *2019-27-02-1000*, *2019-28-02-1000*, и т. д., в зависимости от текущей даты и выбранного формата даты.

### <a name="custom"></a>Настраиваемый

Для более опытных разработчиков со специальными случаями применения предусмотрена возможность полной настройки требуемого формата поля с автоматической нумерацией. Формат может включать в себя строковые константы, автоматически увеличивающиеся числа, форматированные даты или случайные алфавитно-цифровые последовательности.
Дополнительные сведения о том, как определить настраиваемые форматы, см. в разделе [Параметры AutoNumberFormat](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/create-auto-number-attributes#autonumberformat-options).

## <a name="seed-values"></a>Начальные значения

Начальное значение поля с автонумерацией — это начальный номер, который используется в цифровой части формата. Например, если требуется, чтобы поле автонумерации создавало такие записи, как *Contoso-1000*, *Contoso-1001*, *Contoso-1002* и т. д., требуемое начальное значение равно 1000, потому что это значение, с которого начинается числовая последовательность. Поля автонумерации имеют начальное значение по умолчанию 1000, однако можно задать настраиваемое начальное значение при необходимости. 


> [!IMPORTANT]
> Назначение настраиваемого начального значения поддерживается только при создании нового поля автонумерации. 
>
> Задание начального значения только изменяет текущее значение номера для указанного атрибута в текущей среде. Оно не предполагает общего начального значения для атрибута. Начальное значение не включается в решение при импорте в другую среду. 

## <a name="create-an-autonumber-field"></a>Создание поля с автоматической нумерацией
  
1.  Войдите на [портал PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
  
2.  В левой области разверните **Данные** и выберите **Сущности**.
  
3.  Выберите сущность, к которой требуется добавить поле с автоматической нумерацией, затем выберите вкладку **Поля**.
  
4.  На панели инструментов выберите **Добавить поле**.  
  
5.  В правой области введите **Отображаемое имя** и выберите **Автонумерация** для параметра **Тип данных**.

    > [!div class="mx-imgBorder"] 
    > ![](media/create-autonumber-field.png "Создание поля с автоматической нумерацией")
  
6. Если требуется, задайте необязательные поля. Дополнительные сведения: [Создание и изменение полей](create-edit-field-portal.md#create-a-field)

7. Выберите тип автонумерации или сохраните параметр по умолчанию **Номер со строкой префикса**.

8. Настройте начальное значение или оставьте значение по умолчанию **1000**.

9. Выберите **Готово**.

## <a name="see-also"></a>См. также
 [Создание и изменение полей для Common Data Service с помощью портала PowerApps](create-edit-field-portal.md)