---
title: '@ifОператор (JavaScript) | Документы Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634054"
---
# <a name="if-statement-javascript"></a>@ifОператор (JavaScript)
Выполняет ту или иную группу операторов в зависимости от значения выражения.  
  
> [!WARNING]
>  Условная компиляция не поддерживается стандартном режиме Internet Explorer 11 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Она поддерживается в стандартном режиме Internet Explorer 10 и более ранних версий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>Параметры  
 *Условие1, условие2*  
 Необязательно. Выражение, которое можно привести к логическому выражению.  
  
 `text1`  
 Необязательно. Текст для синтаксического анализа, если `condition1` — **true**.  
  
 `text2`  
 Необязательно. Текст для синтаксического анализа, если `condition1` — **false** и `condition2` — **true**.  
  
 `text3`  
 Необязательно. Текст для синтаксического анализа, если оба `condition1` и `condition2` , **false**.  
  
## <a name="remarks"></a>Примечания  
 При написании оператора `@if` нет необходимости размещать каждое предложение на отдельной строке. Можно использовать несколько  **@elif**  предложения. Тем не менее все  **@elif**  предложения должны следовать после ограничения  **@else**  предложения.  
  
 Оператор `@if` обычно используется, чтобы определить, какой текст из нескольких вариантов следует вывести.  
  
 В скриптах, написанных для страниц ASP и ASP.NET, а также в программах командной строки переменные условной компиляции обычно не используются. Это связано с тем, что возможности компиляторов можно определить другими методами.  
  
 При создании скрипта для веб-страницы следует всегда помещать код условной компиляции в комментарии. Таким образом узлы, не поддерживающие условную компиляцию, смогут его пропустить.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование  **@if...@elif... @else... @end**  инструкции.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>Требования  
 Поддерживается во всех версиях Internet Explorer, но не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onИнструкции](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set Оператор](../../javascript/reference/at-set-statement-javascript.md)