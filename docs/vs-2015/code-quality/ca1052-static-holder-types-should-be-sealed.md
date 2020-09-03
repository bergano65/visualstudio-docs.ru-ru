---
title: 'CA1052: типы статических владельцев должны быть запечатаны | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539754"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052. Типы со статическими заполнителями должны быть запечатаны
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит только статические члены и не объявлен с [запечатанным](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) модификатором ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)).

## <a name="rule-description"></a>Описание правила
 Это правило предполагает, что тип, содержащий только статические члены, не предназначен для наследования, поскольку тип не предоставляет никаких функциональных возможностей, которые могут быть переопределены в производном типе. Тип, который не предназначен для наследования, должен быть помечен `sealed` модификатором, чтобы запретить его использование в качестве базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте тип как `sealed` . Если вы нацеливание на [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 или более раннюю версию, лучшим подходом является пометка типа как `static` . Таким образом, не нужно объявлять закрытый конструктор, чтобы предотвратить создание класса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, только если тип предназначен для наследования. Отсутствие `sealed` модификатора предполагает, что тип является полезным в качестве базового типа.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показан тип, нарушающий правило.

### <a name="code"></a>Код
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Исправить с помощью модификатора static

### <a name="description"></a>Описание
 В следующем примере показано, как устранить нарушение этого правила, пометив тип `static` модификатором.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1053. Типы со статическими заполнителями не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
