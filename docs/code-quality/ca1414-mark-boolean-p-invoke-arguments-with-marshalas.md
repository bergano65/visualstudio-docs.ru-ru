---
title: "CA1414: пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs | Microsoft Docs"
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
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414: пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Объявление метода вызова неуправляемого кода содержит параметр или возвращаемое значение типа <xref:System.Boolean?displayProperty=fullName>, однако к этому параметру или возвращаемому значению не применяется атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>.  
  
## Описание правила  
 Метод вызова платформы получает доступ к неуправляемому коду и определяется с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  <xref:System.Runtime.InteropServices.MarshalAsAttribute> задает поведение маршалинга, используемое для преобразования типов данных между управляемым и неуправляемым кодом.  Многие простые типы данных, такие как <xref:System.Byte?displayProperty=fullName> и <xref:System.Int32?displayProperty=fullName>, имеют единственное представление в неуправляемом коде, и для них не требуется указывать поведение маршалинга; среда CLR автоматически предоставляет правильное поведение.  
  
 Тип данных <xref:System.Boolean> имеет несколько представлений в неуправляемом коде.  Если атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute> не указан, поведение маршалинга, используемое по умолчанию, состоит в преобразовании типа данных <xref:System.Boolean> в тип <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Это 32\-разрядный целочисленный тип, который можно использовать далеко не во всех случаях.  Необходимо определить представление типа Boolean, требуемое для неуправляемого метода, и сопоставить его соответствующему значению <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Значение UnmanagedType.Bool представляет собой тип BOOL для системWin32, который всегда имеет размер 4 байта.  Для типа `bool` языка C\+\+ и других однобайтовых типов следует использовать значение UnmanagedType.U1.  Для получения дополнительной информации см. [Default Marshaling for Boolean Types](http://msdn.microsoft.com/ru-ru/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, примените атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute> к параметру или возвращаемому значению типа <xref:System.Boolean>.  Установите для этого атрибута соответствующее значение <xref:System.Runtime.InteropServices.UnmanagedType>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Даже если поведение маршалинга по умолчанию соответствует данному конкретному случаю, явное указание поведения повышает удобство поддержки кода.  
  
## Пример  
 В следующем примере показаны два метода вызова неуправляемого кода, помеченных соответствующими атрибутами <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## Связанные правила  
 [CA1901: объявления P\/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: укажите тип маршалинга для строковых аргументов P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## См. также  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/ru-ru/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)