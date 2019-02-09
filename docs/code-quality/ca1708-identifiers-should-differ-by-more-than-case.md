---
title: CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 204e19e6abb40b8b50af4bd8b206c643f44e08ba
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920084"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имена двух типов, членов, параметров или полное имя пространства имен идентичны в том случае, когда они преобразуются в нижний регистр.

## <a name="rule-description"></a>Описание правила
 Идентификаторы пространств имен, типов, членов и параметров не могут отличаться только регистром знаков, поскольку языки программирования, поддерживаемые средой CLR, не обязательно учитывают регистр знаков. Например [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] — это широко используемый язык, без учета регистра.

 Это правило срабатывает на только открытые члены.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя, которое является уникальным, при сравнении с другими идентификаторами без учета регистра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Библиотека может стать недоступной в некоторых языках платформы .NET Framework.

## <a name="example-of-a-violation"></a>Пример нарушения
 В следующем примере показано нарушение этого правила.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)