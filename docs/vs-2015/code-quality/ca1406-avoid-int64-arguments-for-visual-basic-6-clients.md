---
title: 'CA1406: Избегайте аргументов Int64 для клиентов Visual Basic 6 | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534918"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406. Не используйте аргументы Int64 для клиентов Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип, который специально помечен как видимый для модели COM, объявляет член, принимающий <xref:System.Int64?displayProperty=fullName> аргумент.

## <a name="rule-description"></a>Описание правила
 COM-клиенты VisualBasic 6 не могут получать доступ к 64-разрядным целым числам.

 По умолчанию следующие элементы видимы для COM: сборки, открытые типы, члены открытых экземпляров в открытых типах и все члены открытых типов значений. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значением, `false` а тип должен быть помечен <xref:System.Runtime.InteropServices.ComVisibleAttribute> значением `true` .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила для параметра, значение которого всегда может быть выражено в виде 32-разрядного целого числа, измените тип параметра на <xref:System.Int32?displayProperty=fullName> . Если значение параметра может быть больше, чем может быть выражено в виде 32-разрядного целого числа, измените тип параметра на <xref:System.Decimal?displayProperty=fullName> . Обратите внимание, что <xref:System.Single?displayProperty=fullName> и, и <xref:System.Double?displayProperty=fullName> теряют точность в верхних диапазонах <xref:System.Int64> типа данных. Если элемент не должен быть видимым для COM, пометьте его <xref:System.Runtime.InteropServices.ComVisibleAttribute> значением `false` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если известно, что Visual Basic 6 клиентов COM не будет обращаться к типу.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407. Не используйте статические члены в типах, видимых для COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017. Пометьте сборки с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также
 Взаимодействие с [типом данных Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [неуправляемого кода](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
