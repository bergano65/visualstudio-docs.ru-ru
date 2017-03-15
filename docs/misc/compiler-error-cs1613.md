---
title: "Ошибка компилятора CS1613 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1613
Управляемый класс\-оболочка coclass "класс" для интерфейса "интерфейс" не найден \(возможно, была пропущена ссылка на сборку\).  
  
 Предпринята попытка создать экземпляр COM\-объекта из интерфейса. Интерфейс имеет атрибуты **ComImport** и `CoClass`, однако компилятору не удается найти тип, предоставленный для атрибута `CoClass`.  
  
 Чтобы устранить эту неполадку, можно попробовать выполнить указанные ниже действия.  
  
-   Добавьте ссылку на сборку, которая содержит кокласс \(в большинстве случаев интерфейс и кокласс должны находиться в одной сборке\). Дополнительные сведения см. в разделе [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) или [Диалоговое окно "Добавление ссылки"](http://msdn.microsoft.com/ru-ru/2feb0fe2-0805-4cc9-8cba-b0315849dfb7).  
  
-   Исправьте атрибут `CoClass` интерфейса.  
  
 В приведенном ниже примере демонстрируется правильное применение атрибута **CoClassAttribute**.  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```