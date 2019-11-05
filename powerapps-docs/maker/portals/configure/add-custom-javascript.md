---
title: Использование пользовательского JavaScript для портала | MicrosoftDocs
description: Инструкции по добавлению пользовательского JavaScript в форму на портале
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 42e31fc2ecb18d4f26327f8ccbeabe034d7a1700
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553654"
---
# <a name="add-custom-javascript"></a>Добавить пользовательский JavaScript

Запись шага веб-формы содержит поле с именем **Custom JavaScript** , которое можно использовать для хранения кода JavaScript, позволяющего расширить или изменить визуальное отображение или функцию формы.

Пользовательский блок JavaScript будет добавлен в нижнюю часть страницы непосредственно перед закрывающим элементом тега формы.

## <a name="form-fields"></a>Поля формы

ИДЕНТИФИКАТОРу входа HTML поля сущности присваивается логическое имя атрибута. Это позволяет легко выбирать поля, задавать значения или другие операции на стороне клиента с помощью [jQuery](https://jquery.com/).  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>Дополнительная проверка полей на стороне клиента
Иногда может потребоваться настроить проверку полей в форме. В следующем примере демонстрируется добавление пользовательского проверяющего элемента управления. В этом примере пользователю присваивается сообщение электронной почты, только если для поля предпочтительный метод контакта задано значение электронная почта.

> [!NOTE]
> Проверка полей на стороне клиента не поддерживается во вложенной сетке.

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>Общая проверка

При нажатии кнопки **далее**/**Submit** выполняется функция с именем **вебформклиентвалидате** . Этот метод можно расширить для добавления пользовательской логики проверки.

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>См. также

[Настройка портала](configure-portal.md)  
[Определение форм сущностей](entity-forms.md)  
[Шаги веб-форм для порталов](web-form-steps.md)  
[Тип шага вкладки "загрузить форму/загрузить"](load-form-step.md)  
[Тип шага перенаправления](add-redirect-step.md)  
[Условный тип шага](add-conditional-step.md)
