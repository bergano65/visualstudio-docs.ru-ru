---
title: CA1404. Вызывайте GetLastError сразу после P/Invoke
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ab789e578dd8603f604cdb00aa5d236250d13670
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235055"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404. Вызывайте GetLastError сразу после P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Выполняется вызов <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> метода или эквивалентной функции Win32 `GetLastError` , и вызов, который происходит непосредственно перед, не является методом вызова неуправляемого кода.

## <a name="rule-description"></a>Описание правила
Метод вызова платформы обращается к неуправляемому коду и определяется с помощью `Declare` ключевого слова в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута. Как правило, при сбое неуправляемые функции вызывают функцию Win32 `SetLastError` , чтобы задать код ошибки, связанный с ошибкой. Вызывающая функция, вызвавшая ошибку, вызывает `GetLastError` функцию Win32 для получения кода ошибки и определения причины сбоя. Код ошибки поддерживается для каждого потока и перезаписывается при следующем вызове метода `SetLastError`. После вызова метода, вызвавшего сбой неуправляемого кода, управляемый код может получить код ошибки, <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> вызвав метод. Поскольку код ошибки может быть перезаписан внутренними вызовами из других методов библиотеки управляемых классов, `GetLastError` метод или <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> следует вызывать сразу после вызова метода неуправляемого вызова.

Правило игнорирует вызовы следующих управляемых членов, когда они происходят между вызовом метода неуправляемого кода и вызовом <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Эти члены не изменяют код ошибки и полезны для определения успешности некоторых вызовов метода вызова неуправляемого кода.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, переместите вызов в <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> , чтобы он сразу после вызова метода вызова неуправляемого кода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если код между вызовом метода вызова неуправляемого кода и <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> вызовом метода не может явно или неявно привести к изменению кода ошибки.

## <a name="example"></a>Пример
В следующем примере показан метод, нарушающий правило, и метод, который удовлетворяет правилу.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1060: Перемещение P/Invoke в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400 Должны существовать точки входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401 Методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101 Задание маршалирования для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205 Использование управляемых эквивалентов API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)