---
title: 'CA1014: Пометка сборок с помощью CLSCompliantAttribute | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c6dc131a2bb5f0c54943213fbb42561a0c72d95c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545474"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014. Пометьте сборки с помощью CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 К сборке не <xref:System.CLSCompliantAttribute?displayProperty=fullName> применен атрибут.

## <a name="rule-description"></a>Описание правила
 Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования. Хороший дизайн определяет, что все сборки явно указывают на соответствие CLS <xref:System.CLSCompliantAttribute> . Если атрибут отсутствует в сборке, сборка не соответствует требованиям.

 CLS-совместимая сборка может содержать типы или члены типов, которые не соответствуют требованиям.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут в сборку. Вместо того чтобы пометить всю сборку как несоответствующую, следует определить, какие члены типа или типа не соответствуют требованиям, и пометить эти элементы как таковые. По возможности следует предоставить CLS-совместимую альтернативу для несоответствующих членов, чтобы максимально доступная аудитория могла обращаться ко всем функциональным возможностям сборки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если вы не хотите, чтобы сборка была совместимой, примените атрибут и задайте для него значение `false` .

## <a name="example"></a>Пример
 В следующем примере показана сборка с <xref:System.CLSCompliantAttribute?displayProperty=fullName> примененным атрибутом, который объявляет CLS-совместимый.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>См. также:
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Независимость от языка и независимые от языка компоненты](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
