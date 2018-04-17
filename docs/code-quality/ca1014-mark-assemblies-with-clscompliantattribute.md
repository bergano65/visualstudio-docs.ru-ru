---
title: 'CA1014: Помечайте сборки атрибутом CLSCompliantAttribute | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0cd4c7927dea9ae876cb1cb53d44ddc7f9c6bba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: помечайте сборки атрибутом CLSCompliantAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Сборка не имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> атрибут, применяемый к нему.  
  
## <a name="rule-description"></a>Описание правила  
 Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования. Для правильной разработки все сборки должны явным образом указывать CLS-совместимости с <xref:System.CLSCompliantAttribute>. Если атрибут отсутствует в сборке, сборка несовместима.  
  
 Это возможность CLS-совместимые сборки содержат типы или члены, которые не являются совместимыми типов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте атрибут к сборке. Вместо пометки всю сборку как несовместимые, следует определить, какие типы или члены типов не являются совместимыми и пометить их таким образом. Если это возможно необходимо предоставить CLS-совместимая альтернатива для несовместимых элементов, чтобы все функциональные возможности сборки доступны широкой аудитории.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Если требуется, чтобы сборка была совместимой, примените атрибут и присвойте ему значение `false`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано сборку, которая имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> применен атрибут, объявляющий CLS-совместимыми.  
  
 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)