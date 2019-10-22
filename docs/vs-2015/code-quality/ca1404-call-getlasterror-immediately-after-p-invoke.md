---
title: 'CA1404: вызов GetLastError сразу после P-Invoke | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661326"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: вызывайте GetLastError сразу после P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выполняется вызов метода <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> или эквивалентной функции `GetLastError` Win32, и вызов, который происходит непосредственно перед, не является методом вызова неуправляемого кода.

## <a name="rule-description"></a>Описание правила
 Метод вызова платформы обращается к неуправляемому коду и определяется с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или атрибута <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Как правило, при сбое неуправляемые функции вызывают функцию Win32 `SetLastError`, чтобы задать код ошибки, связанный с ошибкой. Вызывающая функция, вызвавшая ошибку, вызывает функцию Win32 `GetLastError` для получения кода ошибки и определения причины сбоя. Код ошибки поддерживается для каждого потока и перезаписывается при следующем вызове метода `SetLastError`. После вызова метода, вызвавшего сбой неуправляемого кода, управляемый код может получить код ошибки, вызвав метод <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Поскольку код ошибки может быть перезаписан внутренними вызовами из других методов библиотеки управляемых классов, метод `GetLastError` или <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> должен вызываться сразу после вызова метода неуправляемого вызова.

 Правило игнорирует вызовы к следующим управляемым членам, когда они происходят между вызовом метода неуправляемого кода и вызовом <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Эти члены не изменяют код ошибки и полезны для определения успешности некоторых вызовов метода вызова неуправляемого кода.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переместите вызов в <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>, чтобы он сразу после вызова метода вызова неуправляемого кода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если код между вызовом метода вызова неуправляемого кода и вызовом метода <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> не может явно или неявно привести к изменению кода ошибки.

## <a name="example"></a>Пример
 В следующем примере показан метод, нарушающий правило, и метод, который удовлетворяет правилу.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1060: переместите P/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: необходимо наличие точек входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: используйте управляемые эквиваленты API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
