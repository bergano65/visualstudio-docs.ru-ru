---
title: CA1014. Помечайте сборки атрибутом CLSCompliantAttribute | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 324f52eaac86a6ff48b71a98714b866dfca8b239
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704268"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014. Пометьте сборки с помощью CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> атрибут, примененный к нему.

## <a name="rule-description"></a>Описание правила
 Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования. Хороший проект определяет, что все сборки явным образом указывать совместимость с CLS с <xref:System.CLSCompliantAttribute>. Если атрибут отсутствует в сборке, сборка не является совместимым.

 Это возможность CLS-совместимые сборки содержат типы или члены, которые не соответствуют типов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке. Вместо пометки всей сборки считается несоответствующим, следует определить, какие типы или члены типов не являются совместимыми и пометить их таким образом. Если это возможно необходимо предоставить CLS-совместимая альтернатива для несовместимых элементов таким образом, чтобы максимально широкой аудиторией доступны все функции сборки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если не хотите, чтобы сборка должна быть совместимым, примените атрибут и присвойте ему значение `false`.

## <a name="example"></a>Пример
 В следующем примере показано сборку, которая имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> применен атрибут, который они объявлены CLS-совместимыми.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Независимость от языка и независимые от языка компоненты](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
