---
title: "Объект Debug (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debug - объект"
  - "объект Debug, сведения об объекте Debug"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Объект Debug (JavaScript)
Внутренний глобальный объект, отправляющий выходные данные отладчику.  
  
## Синтаксис  
  
```  
Debug.function  
```  
  
## Заметки  
 Создавать экземпляр объекта Debug не нужно. Получить доступ ко всем его свойствам и методам можно путем вызова `function`.  
  
 Существуют различные способы отладки Internet Explorer и приложений [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. В приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] функции `write` и `writeln` объекта `Debug` выводят строки в окне **Выходные данные** Visual Studio во время выполнения. Дополнительные сведения об отладке приложений [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] см. в разделе [Отладка приложений в Visual Studio](../Topic/Debug%20Store%20apps%20in%20Visual%20Studio.md).  
  
 Для отладки скриптов Internet Explorer необходимо установить отладчик скриптов, а скрипт должен выполняться в режиме отладки. В состав Internet Explorer 8 и более поздних версий входит отладчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Если вы используете более раннюю версию Internet Explorer, см. раздел [Практическое руководство. Включение и запуск отладки скриптов из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Если отладка скрипта не производится, функции не оказывают никакого действия.  
  
## Пример  
 В этом примере функция `write` используется для вывода значения переменной.  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Константы  
 [Константы отладки](../../javascript/reference/debug-constants.md)  
  
## Свойства  
 [Свойство Debug.debuggerEnabled](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Свойство Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## Функции  
 [Функция Debug.msTraceAsyncCallbackStarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Функция Debug.msTraceAsyncCallbackCompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Функция Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Функция Debug.msTraceAsyncOperationStarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Функция Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Функция Debug.write](../../javascript/reference/debug-write-function-javascript.md) &#124; [Функция Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## См. также  
 [Оператор debugger](../../javascript/reference/debugger-statement-javascript.md)