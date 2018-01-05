---
title: "CA1043: Используйте целый или строковый аргумент для индексаторов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a75e3cc167f98763cfc0a1747b48e69987a9610b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: используйте целый или строковый аргумент для индексаторов
|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип содержит открытый или защищенный индексатора, который использует тип индекса, отличное от <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, или <xref:System.String?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Описание правила  
 Индексаторы, то есть индексированные свойства, следует использовать типы целочисленного или строкового индекса. Эти типы обычно используются для индексации структур данных и повышения удобства использования библиотеки. Использование <xref:System.Object> тип должен быть только в том случае, если во время разработки невозможно указать конкретный тип integer или string. Если для разработки требуются другие типы индекса, пересмотрите ли тип логическое хранилище данных. Если он не представляет логическое хранилище данных, используйте метод.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, изменить индекс для целочисленный или строковый тип или метод вместо индексатора.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила только после тщательной проверки необходимости использовать нестандартный индексатор.  
  
## <a name="example"></a>Пример  
 В следующем примере показано индексатор, который использует <xref:System.Int32> индекса.  
  
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1023: индексы не должны быть многомерными](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)