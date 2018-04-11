---
title: '@set Оператор (JavaScript) | Документы Microsoft'
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
- '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="set-statement-javascript"></a>@set Оператор (JavaScript)
Создает переменные, используемые вместе с операторами условной компиляции.  
  
> [!WARNING]
>  Условная компиляция не поддерживается стандартном режиме Internet Explorer 11 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Она поддерживается в стандартном режиме Internet Explorer 10 и более ранних версий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Параметры  
 *varname*  
 Обязательно. Допустимое имя переменной [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Должно всегда предваряться знаком "@".  
  
 `term`  
 Обязательно. Ноль или более унарных операторов, за которыми следует константа, переменная условной компиляции или выражение в скобках.  
  
## <a name="remarks"></a>Примечания  
 В коде условной компиляции поддерживаются числовые и логические переменные. Строки не поддерживаются. Переменные, созданные с помощью оператора `@set`, обычно используются в операторах условной компиляции, но могут применяться и в любом другом коде [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Ниже приведены примеры объявлений переменных.  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Следующие операторы можно использовать в выражениях, заключенных в скобки.  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Если переменная используется до своего определения, ее значение равно `NaN`. Проверку на наличие значения `NaN` можно выполнить с помощью оператора `@if`:  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Этот метод дает правильный результат, поскольку `NaN` является единственным значением, которое не равно самому себе.  
  
## <a name="requirements"></a>Требования  
 Поддерживается во всех версиях Internet Explorer, но не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Инструкции](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Оператор](../../javascript/reference/at-if-statement-javascript.md)