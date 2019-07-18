---
title: CA1405. Базовые типы типу видимых COM должны быть видимыми для COM | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f284c0e6e57a2ca359e765992db3f2d599fec328
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705750"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Введение в интерфейс класса](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
