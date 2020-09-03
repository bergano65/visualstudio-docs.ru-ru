---
title: 'CA1034: вложенные типы не должны быть видимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04a982c993ffbb04a3e7600dfb93a00e80727b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542172"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034. Вложенные типы не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит объявление видимого извне типа. Из этого правила исключены вложенные перечисления и защищенные типы.

## <a name="rule-description"></a>Описание правила
 Вложенный тип — это тип, объявленный в области другого типа. Вложенные типы полезны для инкапсуляции закрытых сведений о реализации содержащего типа. В силу этого вложенные типы не должны быть видимыми для внешнего кода.

 Не используйте внешние видимые вложенные типы для логической группировки или избежание конфликтов имен. Вместо этого используйте пространства имен.

 Вложенные типы включают понятие доступности членов, которые некоторые программисты не понимают четко.

 Защищенные типы можно использовать в подклассах и вложенных типах в сценариях предварительной настройки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если вложенный тип не должен быть видимым извне, измените доступность типа. В противном случае удалите вложенный тип из его родителя. Если целью вложенности является категоризация вложенного типа, используйте пространство имен для создания иерархии.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
