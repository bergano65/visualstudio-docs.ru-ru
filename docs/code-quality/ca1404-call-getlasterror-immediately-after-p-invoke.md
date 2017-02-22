---
title: "CA1404: вызывайте GetLastError сразу после P/Invoke | Microsoft Docs"
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
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404: вызывайте GetLastError сразу после P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Выполняется вызов метода <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> или эквивалентной функции Win32 `GetLastError`, а непосредственно предшествующий вызов не является методом вызова неуправляемого кода.  
  
## Описание правила  
 Метод вызова платформы получает доступ к неуправляемому коду и определяется с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или атрибута <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  Как правило, в случае сбоя, неуправляемые функции вызывают функцию Win32 `SetLastError` для установки кода ошибки, связанной со сбоем.  Вызывающий метод ошибочной функции вызывает функцию Win32 `GetLastError` для извлечения кода ошибки и определения причины сбоя.  Код ошибки сохраняется для каждого потока и перезаписывается следующим вызовом `SetLastError`.  После вызова ошибочного метода вызова неуправляемого кода управляемый код может извлечь код ошибки путем вызова метода <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Поскольку код ошибки может быть перезаписан внутренними вызовами от других методов библиотеки классов, метод `GetLastError` или <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> следует вызвать непосредственно после вызова метода вызова неуправляемого кода.  
  
 Правило не учитывает вызовы следующих управляемых членов, когда они происходят между вызовом метода вызова неуправляемого кода и вызовом <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Эти члены не изменяют кода ошибки и полезны для определения успешности некоторых вызовов метода вызова неуправляемого кода.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## Устранение нарушений  
 Чтобы исправить эту ошибку, переместите вызов <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> так, чтобы он следовал сразу за вызовом метода вызова неуправляемого кода.  
  
## Отключение предупреждений  
 Предупреждение из этого правила можно отключить без последствий, если код между методом вызова неуправляемого кода и вызовом метода <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> не может явным или неявным образом вызвать изменение кода ошибки.  
  
## Пример  
 В следующем примере показан метод, который нарушает данное правило, и метод, удовлетворяющий ему.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## Связанные правила  
 [CA1060: переместите P\/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: необходимо наличие точек входа P\/Invoke](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401: методы P\/Invoke не должны быть видимыми](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101: укажите тип маршалинга для строковых аргументов P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: используйте управляемые эквиваленты API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)