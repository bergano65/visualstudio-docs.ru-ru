---
title: 'CA1404: Вызывайте GetLastError сразу после P-Invoke'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4b2150782833d66f4fe9372c434ba5c95eee9dc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: вызывайте GetLastError сразу после P/Invoke
|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выполняется вызов <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> метода или эквивалентные Win32 `GetLastError` функции и вызов, который поступает непосредственно перед не к платформе вызова метода.

## <a name="rule-description"></a>Описание правила
 Платформа вызывать неуправляемый код метода доступа и определяется с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута. Как правило, после сбоя, неуправляемые функции вызывают Win32 `SetLastError` функцию, чтобы задать код ошибки, связанной со сбоем. Код, вызывающий сбой функция вызывает функцию Win32 `GetLastError` функцию, чтобы получить код ошибки и определить причину сбоя. Код ошибки сохраняется для каждого потока и перезаписывается при следующем вызове `SetLastError`. После вызова к платформе не удалось вызвать метод, управляемого кода можно получить код ошибки, вызвав <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> метод. Так как код ошибки может быть перезаписана при внутренних вызовов от других методов библиотеки управляемого класса, `GetLastError` или <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> метод должен вызываться сразу после вызова метода для платформы.

 Правило не учитывает следующие вызовы управляемых элементов при их возникновении между вызовами функций платформы вызова метода и возврата вызова <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Ошибка не изменяйте эти элементы кода и полезны для определения успешности некоторых вызовов метода вызова неуправляемого кода.

-   <xref:System.IntPtr.Zero?displayProperty=fullName>

-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, переместить вызов <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> его сразу после вызова платформы вызова метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, если код между методом вызова неуправляемого кода и <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> вызов метода не может явным или неявным образом вызвать изменение кода ошибки.

## <a name="example"></a>Пример
 В следующем примере показано метод, который нарушает правила и метод, соответствующий этому правилу.

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1060: Переместите P/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [: CA1400 точек входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: используйте управляемые эквиваленты API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)