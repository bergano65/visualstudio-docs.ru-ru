---
title: "CA1409: видимые COM-типы должны быть создаваемыми | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409: видимые COM-типы должны быть создаваемыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Ссылочный тип, который специально помечен как видимый для модели COM, содержит открытый параметризованный конструктор, но не содержит открытого конструктора по умолчанию \(без параметров\).  
  
## Описание правила  
 Тип без открытый конструктор по умолчанию нельзя создать с клиента COM.  Однако такой тип по\-прежнему доступен для COM\-клиентов, если для создания типа и передачи его клиенту доступны другие средства \(например использование возвращаемого значения вызываемого метода\).  
  
 Данное правило пропускает типы, производные от класса <xref:System.Delegate?displayProperty=fullName>.  
  
 По умолчанию для модели COM видимы следующие объекты: сборки, общие типы, члены общих экземпляров в общих типах и все элементы общих типов значений.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте открытый конструктор по умолчанию или удалите из типа атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>.  
  
## Отключение предупреждений  
 Отключение предупреждений данного правила безопасно в том случае, если предоставлены другие средства создания и передачи объектов COM\-клиенту.  
  
## Связанные правила  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## См. также  
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)