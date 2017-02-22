---
title: "Диалоговое окно &quot;Не удается изменить значение&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Не удается изменить значение - диалоговое окно"
  - "переменные [отладчик], редактирование"
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Диалоговое окно &quot;Не удается изменить значение&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Ошибка  
 `The value of this variable cannot be changed`  &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 Это окно сообщения появляется при попытке поменять содержимое переменной на недопустимое значение в окне отладчика \(окно "Видимые переменные", "Контрольные значения" или "Локальные переменные"\) или в диалоговом окне "Быстрая проверка".  Например, данное окно сообщения отображается при попытке задать целочисленной переменной значение символьной строки.  
  
## Решение  
 Следует убедиться, что данные, вводимые в окне отладчика или диалоговом окне "Быстрая проверка", представляют собой допустимое значение для задаваемой переменной.  
  
## См. также  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)