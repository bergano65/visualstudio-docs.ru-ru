---
title: "Предупреждение компилятора (уровень 2) CS0444 | Microsoft Docs"
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
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS0444
Предопределенный тип "имя\_типа1" не найден в пространстве имен "системное\_пространство\_имен1", но был найден в пространстве имен "системное\_пространство\_имен2"  
  
 Предопределенный объект, такой как <xref:System.Int32>, не был найден там, где компилятор ожидал найти его, но найден в пространстве имен "системное\_пространство\_имен2".  
  
 Эта ошибка может указывать, что платформа .NET Framework установлена неправильно. Чтобы устранить эту проблему, переустановите платформу .NET Framework.  
  
 Эта ошибка также может возникнуть при написании собственных библиотек базового класса. В этом случае для устранения ошибки заново выполните сборку mscorlib.