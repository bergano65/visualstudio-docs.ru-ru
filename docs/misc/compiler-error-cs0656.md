---
title: "Ошибка компилятора CS0656 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0656
Отсутствует обязательный для компилятора член "объект.член"  
  
 Существует одна из следующих проблем:  
  
-   Установка среды CLR повреждена.  
  
-   Имеется ссылка на сборку, определяющая тип, который также находится в среде CLR. Однако тип сборки не определяет путь, который ожидает компилятор C\#.  
  
 Проверьте ссылки, чтобы убедиться, что используется правильная версия среды CLR.