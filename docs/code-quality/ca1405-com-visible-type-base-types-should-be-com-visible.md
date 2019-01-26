---
title: CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a94654475432706592c3cd2845488163529ca260
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943225"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Категория|Microsoft.Interoperability|
|Критическое изменение|DependsOnFix|

## <a name="cause"></a>Причина
 Отображается тип объектов модели компонентов (COM) является производным от типа, который не является видимыми для COM.

## <a name="rule-description"></a>Описание правила
 Когда видимым для модели COM тип добавляет члены в новой версии, необходимо придерживаться строгих правил, чтобы избежать нарушения COM-клиентам, которые привязаны к текущей версии. Тип, невидимый для COM предполагается, что он не должны удовлетворять правилам управления версиями COM при добавлении новых членов. Однако если видимыми для COM тип является производным от типа невидимым COM и предоставляет интерфейс <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ClassInterfaceType> (по умолчанию), все открытые члены базового типа (если только они специально помечены как COM невидимым, который будет избыточное) предоставляются COM. Если базовый тип добавляет новые члены в более поздние версии, могут нарушать работу всех клиентов COM, которые привязаны к интерфейсу класса, производного типа. Видимые COM-типы должны наследовать только от видимых COM типах чтобы уменьшить вероятность нарушения работы клиентов COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте видимыми для COM базовых типов или производного типа COM невидимым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)