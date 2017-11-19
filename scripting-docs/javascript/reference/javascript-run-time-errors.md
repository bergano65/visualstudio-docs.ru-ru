---
title: "Ошибки времени выполнения JavaScript | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT-32725
- VS.WebClient.Help.SCRIPT7002
- VS.WebClient.Help.SCRIPT1001
- VS.WebClient.Help.SCRIPT16389
- VS.WebClient.HelpSCRIPT50
- VS.WebClient.HelpSCRIPT70
- VS.WebClient.HelpSCRIPT87
- VS.WebClient.HelpSCRIPT65535
- VS.WebClient.HelpSCRIPT445
- VS.WebClient.HelpSCRIPT600
- VS.WebClient.HelpSCRIPT2343
- VS.WebClient.HelpSCRIPT122
- VS.WebClient.HelpSCRIPT28
- VS.WebClient.HelpSCRIPT16386
- VS.WebClient.HelpSCRIPT7015
- VS.WebClient.HelpSCRIPT3
- VS.WebClient.HelpSCRIPT16388
- VS.WebClient.HelpSCRIPT14
- VS.WebClient.HelpSCRIPT12030
- VS.WebClient.HelpSCRIPT12029
- VS.WebClient.HelpSCRIPT1001
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- run-time errors, JavaScript
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb75c59fae32911c3dd3a7468439a198d7191755
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-run-time-errors"></a>Ошибки времени выполнения JavaScript
Ошибки среды выполнения[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] представляют собой ошибки, возникающие при попытке сценария выполнить действие, невыполнимое для системы. Ошибки среды выполнения отображаются, например, при оценке выражений переменной или выделении памяти.  
  
## <a name="windows-runtime-errors"></a>Ошибки среды выполнения Windows  
 При использовании API среды выполнения Windows в приложении [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] могут отображаться ошибки JavaScript, преобразованные из ошибок HRESULT среды выполнения Windows. Ошибки HRESULT среды выполнения Windows в диапазоне после 0x80070000 преобразуются в ошибки JavaScript путем преобразования шестнадцатеричного значения нижних бит в десятичное значение. Например, ошибка HRESULT 0x80070032 преобразуется в десятичное значение 50 с созданием ошибки JavaScript SCRIPT50. Ошибка HRESULT 0x80074005 преобразуется в десятичное значение 16389 с созданием ошибки JavaScript SCRIPT16389.  
  
## <a name="errors"></a>Ошибки  
  
|Номер ошибки|Описание|  
|------------------|-----------------|  
|5|[Отказано в доступе](../../javascript/misc/access-is-denied.md)|  
|438|[Объект не поддерживает это свойство или метод](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Нет памяти|  
|5029|[Длина массива должна быть конечным положительным числом](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[Длине массива должно быть назначено конечное положительное число](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Ожидается объект массива или аргументов](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Ожидается логическое значение](../../javascript/misc/boolean-expected.md)|  
|5003|[Нельзя назначить результату функции](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[Нельзя назначить this](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Циклическая ссылка в аргументе значения не поддерживается](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Ожидается объект даты](../../javascript/misc/date-object-expected.md)|  
|5015|[Ожидается объект перечислителя](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Исключение возникло, но не перехвачено](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[В регулярном выражении ожидался символ ")"](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[Ожидалось "&#93;" в регулярном выражении](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[Функция не имеет допустимого объекта прототипа](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Ожидалась функция](../../javascript/misc/function-expected.md)|  
|5008|[Недопустимое назначение](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Недопустимый диапазон в наборе символов](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Недопустимый аргумент замены](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[Ожидался объект JavaScript](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Ожидалось число](../../javascript/misc/number-expected.md)|  
|5007|[Ожидался объект](../../javascript/misc/object-expected.md)|  
|5012|[Ожидался член объекта](../../javascript/misc/object-member-expected.md)|  
|5016|[Ожидался объект регулярного выражения](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Ожидалась строка](../../javascript/misc/string-expected.md)|  
|5017|[Ошибка синтаксиса в регулярном выражении](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[Число цифр дробной части вне диапазона](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[Точность вне диапазона](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[Декодируемый URI закодирован неправильно](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[Кодируемый URI содержит недопустимый символ](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Неопределенный идентификатор](../../javascript/misc/undefined-identifier.md)|  
|5018|[Непредвиденный квантификатор](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[Ожидался массив VBArray](../../javascript/misc/vbarray-expected.md)|  
  
## <a name="see-also"></a>См. также  
 [Синтаксические ошибки JavaScript](../../javascript/reference/javascript-syntax-errors.md)