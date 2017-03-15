---
title: "Операторы атрибута сборки или модуля в файле должны указываться до объявлений | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30637"
  - "bc30637"
helpviewer_keywords: 
  - "BC30637"
ms.assetid: 80242581-fa8a-4903-9395-6f7ad1610231
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы атрибута сборки или модуля в файле должны указываться до объявлений
Объявления глобальных атрибутов должны находиться в начале файла исходного кода после операторов `Option` и `Imports`, но перед любыми другими операторами.  
  
 **Идентификатор ошибки:** BC30637  
  
### Исправление ошибки  
  
1.  Поместите глобальные атрибуты, такие как `<Module:>` и `<Assembly:>`, в начало файла исходного кода.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [НЕ В СБОРКЕ. Глобальные атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/253a32d8-1531-4504-b687-088554ab71d2)