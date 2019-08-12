---
title: CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 56e6e7a53f5f8b07d1afc8b68ef641c576524316
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922057"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|депендсонфикс|

## <a name="cause"></a>Причина
Видимый тип модели COM является производным от типа, который не является видимым для COM.

## <a name="rule-description"></a>Описание правила
Когда видимый тип COM добавляет элементы в новую версию, он должен соблюдать строгие правила, чтобы избежать нарушения работы COM-клиентов, привязанных к текущей версии. Тип, невидимый для COM, предполагает, что он не должен следовать этим правилам управления версиями COM при добавлении новых членов. Однако если видимый тип com является производным от невидимого типа COM и предоставляет интерфейс <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> класса или <xref:System.Runtime.InteropServices.ClassInterfaceType> (значение по умолчанию), все открытые члены базового типа (если они не помечены как невидимые как com, которые будут избыточными) предоставляются для COM. Если базовый тип добавляет новые члены в последующей версии, все COM-клиенты, которые привязаны к интерфейсу класса производного типа, могут прерываться. Видимые типы COM должны быть производными только от видимых типов COM, чтобы снизить вероятность нарушения работы клиентов COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, сделайте базовые типы видимыми для COM или производным от него типом COM.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)