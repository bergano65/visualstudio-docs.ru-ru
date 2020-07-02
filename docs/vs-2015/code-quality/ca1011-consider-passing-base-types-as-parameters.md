---
title: 'CA1011: рассмотрите возможность передачи базовых типов в качестве параметров | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f689dfd6c1d39bbd03d522a33ed8c5639a3da9f8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545487"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011. Попробуйте передать базовые типы в качестве параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Объявление метода включает формальный параметр, который является производным типом, а метод вызывает только члены базового типа параметра.

## <a name="rule-description"></a>Описание правила
 Если в объявлении метода в качестве параметра указан базовый тип, любой тип, производный от базового, можно передать методу в качестве соответствующего аргумента. Если аргумент используется внутри тела метода, конкретный метод, который выполняется, зависит от типа аргумента. Если дополнительные функциональные возможности, предоставляемые производным типом, не требуются, использование базового типа позволяет более широко использовать метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените тип параметра на его базовый тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила.

- Если метод требует конкретной функциональности, предоставляемой производным типом

   \- или -

- чтобы обеспечить передачу в метод только производного типа или более производного типа.

  В таких случаях код будет более надежным из-за проверки строгого типа, предоставляемой компилятором и средой выполнения.

## <a name="example"></a>Пример
 В следующем примере показан метод, `ManipulateFileStream` , который можно использовать только с <xref:System.IO.FileStream> объектом, который нарушает это правило. Второй метод, `ManipulateAnyStream` , удовлетворяет правилу, заменяя <xref:System.IO.FileStream> параметр с помощью <xref:System.IO.Stream> .

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1059. Члены не должны предоставлять определенные конкретные типы](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
