---
title: "CA2205: используйте управляемые эквиваленты API Win32 | Microsoft Docs"
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
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2205: используйте управляемые эквиваленты API Win32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Определен метод вызова платформы, при этом в библиотеке классов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] существует метод с эквивалентной функциональностью.  
  
## Описание правила  
 Метод вызова платформы используется для вызова функций неуправляемых DLL\-библиотек и определяется с помощью атрибута <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> или ключевого слова `Declare` в Visual Basic.  Неверно определенный метод вызова платформы может привести к ошибкам во время выполнения из\-за таких неполадок как неверно именованные функции, неправильное сопоставление типов данных параметров и возвращаемых значений, а также неверная спецификация полей \(соглашение о вызове и набор символов\).  Как правило, вместо определения и прямого вызова неуправляемого метода более простым и надежным решением является вызов эквивалентного управляемого метода, если он доступен.  Вызов метода вызова платформы также может привести к различным проблемам безопасности, которые придется решать.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила замените вызов неуправляемой функции вызовом ее управляемого эквивалента.  
  
## Отключение предупреждений  
 Предупреждения этого правила следует отключать, если предполагаемый для замены метод не обладает необходимой функциональностью.  
  
## Пример  
 В следующем примере показано определение метода вызова платформы, нарушающее это правило.  Кроме того, показаны вызовы метода вызова платформы и эквивалентный управляемый метод.  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## Связанные правила  
 [CA1404: вызывайте GetLastError сразу после P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: переместите P\/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: необходимо наличие точек входа P\/Invoke](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401: методы P\/Invoke не должны быть видимыми](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101: укажите тип маршалинга для строковых аргументов P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)