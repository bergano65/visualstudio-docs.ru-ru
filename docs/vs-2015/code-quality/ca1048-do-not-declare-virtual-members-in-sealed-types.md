---
title: 'CA1048: не объявляйте виртуальные элементы в запечатанных типах | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f843efe0aa17b6e87fdb047e1f98a3715ae11af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603317"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: не объявляйте виртуальные элементы в запечатанных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый тип запечатан и объявляет метод, который одновременно `virtual` (`Overridable` в Visual Basic) и не является окончательным. Это правило не сообщает о нарушениях типов делегатов, которые должны следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
 Типы объявляют методы как виртуальные, чтобы наследующие типы могли переопределять реализацию виртуального метода. По определению нельзя наследовать от запечатанного типа, что делает виртуальный метод запечатанного типа бессмысленным.

 Visual Basic .NET и C# компиляторы не позволяют типам нарушать это правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте метод невиртуальным или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если оставить тип в его текущем состоянии, это может вызвать проблемы с обслуживанием и не дает никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
