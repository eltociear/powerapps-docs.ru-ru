---
title: Часто задаваемые вопросы о действиях и стене со временной шкалой | Документация Майкрософт
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e79412c79a3b2a6d5c7f7f51c8cfcad8e4f5cc78
ms.sourcegitcommit: 826bde1eab3dd32d7bf9fa3f43ea069694845597
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290971"
---
# <a name="frequently-asked-questions-about-activities-and-the-timeline-wall"></a>Часто задаваемые вопросы о действиях и стене со временной шкалой  

## <a name="is-a-title-required-when-adding-a-new-note"></a>Нужно ли указывать заголовок при добавлении новой заметки?

Нет. При добавлении заметки к действию поле заголовка помечается как обязательное, но оно таковым не является. Это известная проблема, которая возникает при использовании устаревшего веб-клиента.

## <a name="for-an-appointment-when-i-choose-the-option-to-save-as-draft-it-doesnt-show-that-the-appointment-has-been-saved-as-a-draft"></a>Если при сохранении сведений о встрече выбрать параметр *Сохранить как черновик*, нет указания на то, что такие сведения сохранены как черновик.

Если вы сохраняете сведения о встрече как черновик в устаревшем веб-клиенте, в заголовке не отображается запись **[DRAFT]**, указывающая на то, что эта информация сохранена как черновик.

## <a name="can-i-add-activities-to-read-only-records"></a>Можно ли добавлять действия к записям, доступным только для чтения?

Да. Можно добавлять действия к сущностям, доступным только для чтения, например к заметкам, телефонным звонкам, задачам и многому другому. 

## <a name="are-html-tags-supported-in-notes"></a>Поддерживает ли функция создания **заметок** теги HTML?

Нет. При создании действия заметки для любой записи или сущности HTML-теги не поддерживаются. Например, если вы добавите <TAG> </TAG> в поле заметки, этот тег будет отображаться как <TAG_XXX="XX"> </TAG>.

## <a name="how-can-i-improve-performance-on-timeline-wall"></a>Как повысить производительность стены со временной шкалой?

Чтобы повысить производительность стены со временной шкалой, можно оптимизировать объем данных, возвращаемых определенной записью сущности. 

1.  Настройте формы сущностей таким образом, чтобы отображались только сведения об используемых действиях.  Такое поведение можно задать на уровне формы.  Например, если для обращений вы не используете задачи, вы можете настроить стену со временной шкалой в форме обращения таким образом, чтобы сведения о задачах не отображались.
2.  Уменьшите количество записей, которые отображаются на стене со временной шкалой по умолчанию.  По умолчанию настроен возврат 10 записей. Если это значение будет больше, производительность может понизиться.  Не рекомендуем превышать значение по умолчанию. 

## <a name="activity-wall-is-not-supported-in-print-preview"></a>Стена с действиями не поддерживает режим предварительного просмотра.

Если в Dynamics 365 выбрать параметр **Предварительный просмотр**, **стена со временной шкалой** будет отсутствовать в списке доступных функций. Вы сможете просмотреть **заметки**, но сведения о задачах или сообщениях электронной почты отображаться не будут.




