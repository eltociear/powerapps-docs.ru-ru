---
title: "\"Песочница\" для языка определения отчетов | Документация Майкрософт"
ms.custom: ''
ms.date: 09/30/2017
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ec72014-9f0c-4964-ac67-24419b054e91
caps.latest.revision: 13
author: Mattp123
ms.author: matp
manager: annbe
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d5a74785ed33c8c4591717dc062ac741a8dceb87
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115717"
---
# <a name="rdl-sandboxing"></a>"Песочница" для языка определения отчетов 

В Common Data Service отчеты выполняются в режиме песочницы. Это осуществляется путем включение песочницы для языка определения отчетов (RDL) в SQL Server Reporting Services. "Песочница" для языка определения отчетов позволяет обнаруживать и ограничивать использование определенных типов ресурсов. Поэтому некоторые функциональные возможности в приложениях на основе модели Power Apps могут быть недоступны. Дополнительные сведения см. в разделе [MSDN: Включение и отключение песочницы для языка определения отчетов](https://msdn.microsoft.com/library/ee210591.aspx).  
  
 Текущие параметры конфигурации "песочницы" для языка определения отчетов в Common Data Service описаны в следующих разделах данной темы.  
    
<a name="BKMK_Max"></a>   
## <a name="limits-of-the-array-result-length-and-string-result-length"></a>Ограничение длины результата типа массива и длины результата типа строки  
 Максимальное число элементов, разрешенное в возвращаемом значении типа массива для выражения языка определения отчетов увеличено с 250 до 102400. Максимальное число элементов, разрешенное в возвращаемом значении типа строки для выражения языка определения отчетов также увеличено с 250 до 102400. Это позволяет включать изображения и эмблемы размером до 75 КБ, которые будут храниться в базе данных в кодировке Base64.  
  
 Для параметра MaxResourceSize задано значение 2000. Это позволяет включить в отчет внешние изображения размером до 1500 КБ. Дополнительные сведения: [TechNet: Добавление внешнего изображения (построитель отчетов Report Builder и SSRS)](https://technet.microsoft.com/library/dd220527.aspx)  
  
<a name="BKMK_Allowed"></a>   
## <a name="allowed-types-and-denied-members"></a>Разрешенные типы и запрещенные участники  
 Функция песочницы для языка определения отчетов позволяет создавать список одобренных типов и список запрещенных участников. Список одобренных типов называется списком разрешения. Список запрещенных участников, которые не допускаются в выражениях языка определения отчетов, называется списком блокировки.  
  
 Следующая таблица содержит список разрешенных типов и запрещенных участников, доступных в режиме песочницы в Common Data Service.  
  
|Разрешенные типы|Запрещенные участники|  
|-------------------|--------------------|  
|`System.Array`|CreateInstance|  
||Finalize|  
||GetType|  
||MemberwiseClone|  
||Изменение размера|  
|||  
|`System.DateTime`|FromBinary|  
||GetDateTimeFormats|  
||GreaterThan|  
||GreaterThanOrEqual|  
|||  
|||  
|`System.Object`|GetType|  
||MemberwiseClone|  
||ReferenceEquals|  
|||  
|`System.DbNull`|Finalize|  
||MemberwiseClone|  
||GetObjectData|  
||GetTypeCode|  
|||  
|`System.Math`|BigMul|  
||DivRem|  
||IEEERemainder|  
||E|  
||PI|  
||Pow|  
|`System.String`||  
|`System.TimeSpan`|часов|  
||TicksPerDay|  
||TicksPerHour|  
||TicksPerMillisecond|  
||TicksPerMinute|  
||TicksPerSecond|  
||Zero|  
||TryParse|  
||TryParseExact|  
|`System.Convert`|ChangeType|  
||IConvertible.ToBoolean|  
||IConvertible.ToByte|  
||IConvertible.ToChar|  
||IConvertible.ToDateTime|  
||IConvertible.ToDecimal|  
||IConvertible.ToDouble|  
||IConvertible.ToInt16|  
||IConvertible.ToInt32|  
||IConvertible.ToInt64|  
||IConvertible.ToSByte|  
||IConvertible.ToSingle|  
||IConvertible.ToType|  
||IConvertible.ToUInt16|  
||IConvertible.ToUInt32|  
||IConvertible.ToUInt64|  
|`System.StringComparer`|Создание|  
||Finalize|  
|||  
|`System.TimeZone`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`System.Uri`|Unescape|  
||Разбор|  
||ESCAPE|  
||Finalize|  
|||  
|`System.UriBuilder`|Finalize|  
|||  
|`System.Globalization.CultureInfo`|ClearCachedData|  
|||  
|`System.Text.RegularExpressions.Match`|Нет значения|  
||NextMatch|  
||Результат|  
||Synchronized|  
|||  
|||  
|`System.Text.RegularExpressions.Regex`|CacheSize|  
||CompileToAssembly|  
||GetGroupNames|  
||GetGroupNumbers|  
||GetHashCode|  
||Unescape|  
||UseOptionC|  
||UseOptionR|  
||capnames|  
||caps|  
||capsize|  
||capslist|  
||roptions|  
||pattern|  
||factory|  
||IsMatch|  
||Matches|  
||Iserializable.GetObjectData|  
||InitializeReferences|  
||RightToLeft|  
||Параметры|  
|||  
|||  
|`Microsoft.VisualBasic.Constants`|vbAbort|  
||vbAbortRetryIgnore|  
||vbApplicationModal|  
||vbArchive|  
||vbBinaryCompare|  
||vbCancel|  
||vbCritical|  
||vbDefaultButton1|  
||vbDefaultButton2|  
||vbDefaultButton3|  
||vbExclamation|  
||vbFormFeed|  
||vbGet|  
||vbHidden|  
||vbHide|  
||vbHiragana|  
||vbIgnore|  
||vbInformation|  
||vbKatakana|  
||vbLet|  
||vbLinguisticCasing|  
||vbMaximizedFocus|  
||vbMinimizedFocus|  
||vbMinimizedNoFocus|  
||vbMsgBoxHelp|  
||vbMsgBoxRight|  
||vbMsgBoxRtlReading|  
||vbMsgBoxSetForeground|  
||vbNo|  
||vbNormal|  
||vbNormalFocus|  
||vbNormalNoFocus|  
||vbObjectError|  
||vbOK|  
||vbOKCancel|  
||vbOKOnly|  
||vbQuestion|  
||vbReadOnly|  
||vbRetry|  
||vbRetryCancel|  
||vbSet|  
||vbSystem|  
||vbSystemModal|  
||VbTypeName|  
||vbVolume|  
||Zero|  
|`Microsoft.VisualBasic.ControlChars`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Conversion`|Err|  
||ErrorToString|  
||Fix|  
|||  
|`Microsoft.VisualBasic.DateInterval`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Financial`|Finalize|  
||GetType|  
||MemberwiseClone|  
||IRR|  
||NPV|  
||MIRR|  
|||  
|||  
|`Microsoft.VisualBasic.Interaction`|AppActivate|  
||Beep|  
||CallByName|  
||Команда|  
||CreateObject|  
||Environ|  
||Finalize|  
||GetAllSettings|  
||GetObject|  
||GetSetting|  
||GetType|  
||InputBox|  
||MemberwiseClone|  
||MsgBox|  
||SaveSetting|  
||Shell|  
||Выбрать|  
||Переключатель|  
|||  
|||  
|`Microsoft.VisualBasic.Information`|Erl|  
||Err|  
||IsError|  
||IsDBNull|  
||Lbound|  
||Ubound|  
||SystemTypeName|  
|||  
|`Microsoft.VisualBasic.Strings`|Finalize|  
||GetType|  
||MemberwiseClone|  
||Lset|  
||Rset|  
|||  
|`Microsoft.Crm.Reporting.RdlHelper`||  
  
<a name="BKMK_Denied"></a>   
## <a name="common-denied-members"></a>Общие запрещенные участники  
 В следующей таблице перечислены запрещенные участники в общих разрешенных типах:  
  
||  
|-|  
|DateString|  
|Длительность|  
|Equality|  
|Равно|  
|Erl|  
|Фильтровать|  
|GetChar|  
|GroupNameFromNumber|  
|GroupNumberFromName|  
|Int|  
|MaxValue|  
|MinValue|  
|Negate|  
|Таймер|  
|TimeString|  
|ToBinary|  
|Finalize|  
|GetType|  
|MemberwiseClone|  
  

