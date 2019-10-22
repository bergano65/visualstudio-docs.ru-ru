---
title: 'CA2222: не уменьшайте видимость унаследованного члена | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3dda56e6980133b0e33893fbb814c4a3a7008c49
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656061"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: не уменьшайте видимость унаследованных членов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Частный метод в незапечатанном типе имеет сигнатуру, идентичную общедоступному методу, объявленному в базовом типе. Частный метод не является окончательным.

## <a name="rule-description"></a>Описание правила
 Не следует изменять модификатор доступа для унаследованных членов. Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен. Если член является закрытым и тип является незапечатанным, наследуемые типы могут вызывать последнюю открытую реализацию метода в иерархии наследования. Если необходимо изменить модификатор доступа, то либо метод должен быть помечен как Final, либо его тип должен быть запечатанным, чтобы предотвратить переопределение метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените доступ, не являющийся частным. Кроме того, если ваш язык программирования поддерживает его, можно сделать метод окончательным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
