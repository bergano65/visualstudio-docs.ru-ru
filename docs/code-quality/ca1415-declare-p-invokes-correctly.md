---
title: "CA1415: правильно объявляйте методы P/Invoke | Microsoft Docs"
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
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415: правильно объявляйте методы P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Неразрывный \- Если P\/Invoke, который объявляет параметр, не может быть видим за пределами сборки.  Breaking \- Если P\/Invoke, который объявляет параметр, может быть видим за пределами сборки.|  
  
## Причина  
 Неправильно объявлен метод вызова платформы.  
  
## Описание правила  
 Метод вызова платформы получает доступ к неуправляемому коду и определяется с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  В настоящее время это правило ищет объявления методов вызова платформы, нацеленных на функции Win32, имеющих указатель на параметр структуры OVERLAPPED, если соответствующий управляемый параметр не является указателем на структуру <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, следует правильно объявлять метод вызова платформы.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показаны методы вызова платформы, нарушающие это правило и соответствующие ему.  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## См. также  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)