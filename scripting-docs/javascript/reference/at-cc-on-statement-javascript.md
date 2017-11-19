---
title: "@cc_onОператор (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ccon-statement-javascript"></a>@cc_onОператор (JavaScript)
Активирует поддержку условной компиляции внутри комментариев скрипта.  
  
> [!WARNING]
>  Условная компиляция не поддерживается стандартном режиме Internet Explorer 11 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Она поддерживается в стандартном режиме Internet Explorer 10 и более ранних версий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>Примечания  
 Оператор `@cc_on` активирует условную компиляцию внутри комментариев скрипта.  
  
 Однако в скриптах, предназначенных для страниц ASP или ASP.NET и программ командной строки, переменные условной компиляции используются не так часто, поскольку характеристики компиляторов можно определить другими методами.  
  
 При создании скрипта для веб-страницы следует всегда помещать код условной компиляции в комментарии. Таким образом узлы, не поддерживающие условную компиляцию, смогут его пропустить.  
  
 Настоятельно рекомендуется помещать оператор `@cc_on` в комментарий, чтобы синтаксис скрипта был допустимым для браузеров, не поддерживающих условную компиляцию.  
  
 Условную компиляцию можно также включить с помощью оператора `@if` или `@set`, помещенного за пределами комментария.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `@cc_on`.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
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
 [@ifИнструкции](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Оператор](../../javascript/reference/at-set-statement-javascript.md)