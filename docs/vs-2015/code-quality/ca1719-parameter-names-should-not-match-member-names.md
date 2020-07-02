---
title: 'CA1719: имена параметров не должны совпадать с именами членов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545370"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719. Имена параметров не должны совпадать с именами членов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя видимого извне элемента совпадает с именем одного из его параметров в сравнении без учета регистра.

## <a name="rule-description"></a>Описание правила
 Имя параметра должно передавать смысловое значение параметра, а имя члена — смысловое значение члена. Они могут совпадать лишь в очень редких случаях. Присвоение параметру имени содержащего его члена кажется неестественным и затрудняет использование библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя параметра, не совпадающее с именем члена.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для новой разработки нет известных сценариев, при которых необходимо отключить предупреждение из этого правила. Для доставки библиотек может потребоваться отключить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707. Идентификаторы не должны содержать символы подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
