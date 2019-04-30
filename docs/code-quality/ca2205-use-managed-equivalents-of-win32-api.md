---
title: CA2205. Используйте управляемые эквиваленты Win32 API
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b049f55d9361b409504cd798b7c878efb5c79ee6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806812"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205. Используйте управляемые эквиваленты Win32 API

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Неуправляемого определен метод, и существует метод с эквивалентной функциональностью в библиотеке классов .NET Framework.

## <a name="rule-description"></a>Описание правила

Неуправляемого метода используется для вызова неуправляемой функции DLL и определяется с помощью <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут, или `Declare` в Visual Basic. Это некорректно определенная платформа вызова метода может вызывать исключения среды выполнения из-за проблем, таких как неверно именованные функции, неправильное сопоставление типов данных параметров и возвращаемых значений и неверная спецификация полей, например соглашение о вызовах и символ набор. Если он доступен, это проще и ошибкам для вызова эквивалентного управляемого метода вместо определения и вызова неуправляемого метода напрямую. Вызов платформы вызов метода также может привести к дополнительным проблемам с безопасностью, которые следует учитывать.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, замените вызов неуправляемой функции с помощью вызова его управляемого эквивалента.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, если метод в качестве замены не предоставляет необходимую функциональность.

## <a name="example"></a>Пример

В следующем примере показан платформы вызвать определение метода, который нарушает правило. Кроме того вызовы платформы вызова метода и показаны эквивалентные управляемый метод.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1404: Вызывайте GetLastError сразу после P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Переместите P/Invokes в класс NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Должны существовать точки входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)