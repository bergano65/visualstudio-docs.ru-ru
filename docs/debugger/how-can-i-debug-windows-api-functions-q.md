---
title: "Как отладить функции Windows API? | Microsoft Docs"
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
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API - интерфейсы, отладка"
  - "отладка [C++], функции Windows API"
  - "символы NT и отладка функций Windows API"
  - "функции Windows API, отладка"
  - "API Windows, отладка функций API"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Как отладить функции Windows API?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если нужно отладить функцию Windows API с загруженными символами NT, необходимо выполнить следующие действия.  
  
### Установка точки останова в функции Windows API с загруженными символами NT  
  
-   Введите имя функции вместе с именем DLL\-файла, в котором эта функция находится.  В 32\-разрядном коде используйте декорированную форму имени функции.  Например, чтобы задать точку останова на **MessageBeep**, необходимо ввести следующее.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Чтобы получить декорированное имя, см. раздел [Просмотр внутренних имен](http://msdn.microsoft.com/ru-ru/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)