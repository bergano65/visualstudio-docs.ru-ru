---
title: 'CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac8412e242f7d69ea657d5b7f74fa83ffbff5acc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM
|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Категория|Microsoft.Interoperability|
|Критическое изменение|DependsOnFix|

## <a name="cause"></a>Причина
 Видимый тип объектов модели компонентов (COM) является производным от типа, который не является видимым для COM.

## <a name="rule-description"></a>Описание правила
 Когда видимым для модели COM тип добавляет участников в новой версии, необходимо придерживаться строгим правилам, чтобы избежать нарушения COM-клиенты, которые привязаны к текущей версии. Тип, невидимый для COM, следование не должен следовать правилам управления версиями COM при добавлении новых членов. Однако если видимыми для COM тип является производным от типа невидимой COM и предоставляет интерфейс класса <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ClassInterfaceType> (по умолчанию), все открытые члены базового типа (если только они специально помечены как COM невидимым, который излишне) предоставляются COM. Если базовый тип добавляет новые члены в последующих версиях, могут нарушать работу всех клиентов COM, связанных с интерфейсом класса производного типа. Видимые COM-типы должны наследовать только от видимых COM типах снижения риска нарушения COM-клиентам.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, сделайте базовые типы видимыми для COM или производный тип COM невидимой.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано тип, нарушающий правило.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>См. также
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)