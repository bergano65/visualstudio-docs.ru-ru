---
title: CA1404. Вызывайте GetLastError сразу после P / Invoke | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e33c724d2cebb9423f2e475d95bf42ac5e2cc966
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200305"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404. Вызывайте GetLastError сразу после P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выполняется вызов для <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> метода или эквивалентные Win32 `GetLastError` функция и вызов, который поступает непосредственно перед не на платформу вызова метода.

## <a name="rule-description"></a>Описание правила
 Вызов метода доступа неуправляемого кода платформы и определяется с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибута. Как правило, в случае сбоя неуправляемых функций вызова Win32 `SetLastError` функцию для задания кода ошибки, связанное с ошибкой. Вызывающий объект функции, завершившейся сбоем вызывает Win32 `GetLastError` функцию, чтобы извлечь код ошибки и определить причину сбоя. Код ошибки сохраняется для каждого потока и перезаписывается при следующем вызове `SetLastError`. После вызова неудачных платформы вызова метода, управляемого кода можно получить код ошибки, вызвав <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> метод. Так как код ошибки может быть перезаписана при внутренних вызовов из других методов библиотеки управляемых классов, `GetLastError` или <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> метод должен вызываться сразу после вызова метода для платформы.

 Правило не учитывает вызовы следующие управляемые члены при их возникновении между вызовами функций для платформы вызова метода и вызова <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Эти члены не изменяйте ошибки кода и полезны для определения успешности некоторых вызовов метода неуправляемого кода.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, переместите вызов <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> сразу же после вызова платформы вызова метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если код между методом вызова неуправляемого кода и <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> вызов метода не может явно или неявно привести изменение кода ошибки.

## <a name="example"></a>Пример
 В примере показан метод, который нарушает правило и метод, соответствующий этому правилу.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1060: Переместите P/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Должны существовать точки входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: МЕТОДЫ P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Используйте управляемые эквиваленты Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
