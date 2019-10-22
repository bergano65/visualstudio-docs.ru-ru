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
ms.openlocfilehash: c20ea7bd7bba6f221395c7e2c21d6c1dcc241fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661294"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: не следует использовать аргументы Int64 для клиентов Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип, который специально помечен как видимый для модели COM, объявляет член, принимающий аргумент <xref:System.Int64?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Visual Basic 6 COM-клиентов не может получить доступ к 64-разрядным целым числам.

 По умолчанию следующие элементы видимы для COM: сборки, открытые типы, члены открытых экземпляров в открытых типах и все члены открытых типов значений. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>, для которой задано значение `false`, а тип должен быть помечен <xref:System.Runtime.InteropServices.ComVisibleAttribute>ным значением `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила для параметра, значение которого всегда может быть выражено в виде 32-разрядного целого числа, измените тип параметра на <xref:System.Int32?displayProperty=fullName>. Если значение параметра может быть больше, чем может быть выражено в виде 32-разрядного целого числа, измените тип параметра на <xref:System.Decimal?displayProperty=fullName>. Обратите внимание, что обе <xref:System.Single?displayProperty=fullName> и <xref:System.Double?displayProperty=fullName> теряют точность в верхних диапазонах <xref:System.Int64>ного типа данных. Если элемент не должен быть видимым для COM, пометьте его <xref:System.Runtime.InteropServices.ComVisibleAttribute> значением `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если известно, что Visual Basic 6 клиентов COM не будет обращаться к типу.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также раздел
 Взаимодействие с [типом данных Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [неуправляемого кода](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
