---
title: 'CA1048: Не объявляйте виртуальные члены в запечатанных типах | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3ff0bb128c72f5483c9169a98c6fc41ec3057e54
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591705"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: не объявляйте виртуальные элементы в запечатанных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1048: не объявляйте виртуальные члены в запечатанных типах](https://docs.microsoft.com/visualstudio/code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types).

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый тип является запечатанным и объявляет метод, который является одновременно `virtual` (`Overridable` в Visual Basic) и не последним. Это правило не учитывает нарушения для типов делегата, которые необходимо следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
 Типы объявляют методы как виртуальные, чтобы наследующие типы могли переопределять реализацию виртуального метода. По определению не может наследовать от запечатанного типа, что делает виртуальный метод запечатанного типа бессмысленным.

 Компиляторы Visual Basic .NET и C# не разрешать типы нарушение этого правила.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделать метод невиртуальным или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Тип в ее текущем состоянии может привести к проблемам обслуживания и не предоставляет никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере тип, который нарушает это правило.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]



