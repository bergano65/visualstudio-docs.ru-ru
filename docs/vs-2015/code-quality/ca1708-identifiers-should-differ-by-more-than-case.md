---
title: 'CA1708: идентификаторы должны отличаться больше, чем регистр | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22a33c852b941b4c7e7398416aa1e74e69ff1786
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544044"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имена двух типов, членов, параметров или полных пространств имен идентичны, если они преобразуются в нижний регистр.

## <a name="rule-description"></a>Описание правила
 Идентификаторы пространств имен, типов, членов и параметров не могут отличаться только регистром знаков, поскольку языки программирования, поддерживаемые средой CLR, не обязательно учитывают регистр знаков. Например, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] является широко используемым языком без учета регистра.

 Это правило срабатывает только для открытых видимых элементов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите уникальное имя, если оно сравнивается с другими идентификаторами без учета регистра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Библиотека может быть непригодна для использования на всех языках, доступных в [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="example-of-a-violation"></a>Пример нарушения
 В следующем примере показано нарушение этого правила.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
