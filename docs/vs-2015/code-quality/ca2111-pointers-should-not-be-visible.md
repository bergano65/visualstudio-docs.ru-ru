---
title: 'CA2111: указатели не должны быть видимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0d5546c6f6a2f5dbd0c6063f4a1dfd40ce1d7bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658739"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: указатели не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытое или защищенное <xref:System.IntPtr?displayProperty=fullName> или <xref:System.UIntPtr?displayProperty=fullName> поле не доступно только для чтения.

## <a name="rule-description"></a>Описание правила
 <xref:System.IntPtr> и <xref:System.UIntPtr> являются типами указателей, которые используются для доступа к неуправляемой памяти. Если указатель не является частным, внутренним или предназначенным только для чтения, вредоносный код может изменить значение указателя, потенциально допуская доступ к произвольным расположениям в памяти или вызвать сбои приложения или системы.

 Если вы планируете защитить доступ к типу, содержащему поле указателя, см. раздел [CA2112: Secure Types не должен предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Защитите указатель, сделав его предназначенным только для чтения, внутренним или частным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если не полагаться на значение указателя.

## <a name="example"></a>Пример
 В следующем коде показаны указатели, которые нарушают и удовлетворяют правилу. Обратите внимание, что нечастные указатели также нарушают правило [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
