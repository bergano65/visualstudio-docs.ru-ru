---
title: "Объект, на который указывает ссылка, имеет значение Nothing | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Объект, на который указывает ссылка, имеет значение Nothing
Используемый объект имеет значение `Nothing`, но ожидается подходящее значение. Значение `Nothing` указывает на то, что объект не имеет значения либо потому, что значение не было присвоено, либо потому, что ему было присвоено значение `Nothing`.  
  
 **Идентификатор ошибки:** BC30760  
  
### Исправление ошибки  
  
1.  Проверьте объект, чтобы убедиться в том, что он объявлен внутри области видимости процедуры, в которой произошла ошибка.  
  
2.  Проверьте, какое значение было присвоено объекту.  
  
    > [!NOTE]
    >  Значение `Nothing` не эквивалентно нулю или пустой строке. Вы можете использовать `IsNothing` для проверки того, содержит ли объект значение `Nothing`.  
  
## См. также  
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [НЕ В СБОРКЕ. Функция IsNothing](http://msdn.microsoft.com/ru-ru/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)