---
title: 'CA1719: Имена параметров не должны совпадать с именами элементов | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 74897625a8d8fced4a87a6e5d722d9edf04769b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828224"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: имена параметров не должны совпадать с именами элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя видимого элемента соответствует при сравнении без учета регистра, имя одного из своих параметров.

## <a name="rule-description"></a>Описание правила
 Имя параметра должно передавать смысловое значение параметра, а имя члена — смысловое значение члена. Они могут совпадать лишь в очень редких случаях. Присвоение параметру имени содержащего его члена кажется неестественным и затрудняет использование библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя параметра, которое не соответствует имени члена.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для разработки новых приложений, не известные сценарии возникнуть, когда необходимо подавить предупреждение из этого правила. Для доставки библиотек, возможно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)



