---
title: "Объект Debug (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Объект Debug (JavaScript)
Внутренний глобальный объект, отправляющий выходные данные отладчику.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>Примечания  
 Создавать экземпляр объекта Debug не нужно. Получить доступ ко всем его свойствам и методам можно путем вызова `function`.  
  
 Существуют различные способы отладки Internet Explorer и приложений [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . В приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] функции `write` и `writeln` объекта `Debug` выводят строки в окне **Выходные данные** Visual Studio во время выполнения. Дополнительные сведения об отладке [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] приложений, в разделе [отладка универсальных приложений Windows в Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md).  
  
 Для отладки скриптов Internet Explorer необходимо установить отладчик скриптов, а скрипт должен выполняться в режиме отладки. В состав Internet Explorer 8 и более поздних версий входит отладчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Если вы используете более раннюю версию Internet Explorer, см. раздел [Практическое руководство. Включение и запуск отладки скриптов из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Если отладка скрипта не производится, функции не оказывают никакого действия.  
  
## <a name="example"></a>Пример  
 В этом примере функция `write` используется для вывода значения переменной.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>Константы  
 [Константы Debug](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>Свойства  
 [Свойство Debug.debuggerEnabled](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Свойство Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>Функции  
 [Функция Debug.msTraceAsyncCallbackStarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Функция Debug.msTraceAsyncCallbackCompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Функция Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Функция Debug.msTraceAsyncOperationStarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Функция Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Функция Debug.write](../../javascript/reference/debug-write-function-javascript.md) &#124; [Функция Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Оператор debugger](../../javascript/reference/debugger-statement-javascript.md)