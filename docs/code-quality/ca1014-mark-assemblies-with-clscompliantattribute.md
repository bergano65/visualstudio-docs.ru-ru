---
title: "CA1014: Помечайте сборки атрибутом CLSCompliantAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a870721f0bf7192b417d2105635c663fb69713c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 [Независимость от языка и независимые от языка компоненты](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)