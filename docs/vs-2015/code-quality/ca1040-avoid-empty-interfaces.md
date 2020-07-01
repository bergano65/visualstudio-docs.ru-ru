---
title: 'CA1040: избегайте пустых интерфейсов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548256"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040. Не используйте пустые интерфейсы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Интерфейс не объявляет ни одного члена или не реализует два или больше других интерфейсов.

## <a name="rule-description"></a>Описание правила
 Интерфейсы определяют члены, предоставляющие поведение или соглашение об использовании. Функциональность, описанная интерфейсом, может быть использована любым типом вне зависимости от расположения типа в иерархии интерфейса. Тип реализует интерфейс путем предоставления реализаций для членов интерфейса. Пустой интерфейс не определяет никаких членов. Поэтому он не определяет контракт, который может быть реализован.

 Если проект включает пустые интерфейсы, которые должны быть реализованы типами, то, вероятно, вы используете интерфейс в качестве маркера или способ для обнаружения группы типов. Если эта идентификация будет происходить во время выполнения, то правильный способ сделать это — использовать настраиваемый атрибут. Для определения целевых типов используйте атрибут присутствие или отсутствие атрибута или свойства атрибута. Если идентификация должна происходить во время компиляции, можно использовать пустой интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите интерфейс или добавьте в него элементы. Если для обозначения набора типов используется пустой интерфейс, замените интерфейс пользовательским атрибутом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если интерфейс используется для обнаружения набора типов во время компиляции.

## <a name="example"></a>Пример
 В следующем примере показан пустой интерфейс.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
