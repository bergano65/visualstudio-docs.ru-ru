---
title: CA1040. Не используйте пустые интерфейсы
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8d8691cd2f51cbee2150da05a7421d79d5d602a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954160"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040. Не используйте пустые интерфейсы

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Интерфейс не объявляет никаких членов или не реализует двух или нескольких других интерфейсов.

## <a name="rule-description"></a>Описание правила
 Интерфейсы определяют члены, предоставляющие поведение или соглашение об использовании. Функциональность, описанная интерфейсом, может быть использована любым типом вне зависимости от расположения типа в иерархии интерфейса. Тип реализует интерфейс путем предоставления реализаций для членов интерфейса. Пустой интерфейс не определяет никаких элементов. Таким образом он не определяет контракт, который может быть реализован.

 Если прототип содержит пустой интерфейсы, типы должны быть реализованы, как маркер или идентифицировать группу типов, возможно, вы используете интерфейс. Если этот код будет выполняться во время выполнения, правильный способ выполнения этой задачи является использование настраиваемого атрибута. Используйте наличие или отсутствие атрибута или свойства атрибута, для определения целевых типов. Если определение должно произойти во время компиляции, а затем можно использовать пустой интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите интерфейс или добавлять к нему. Если пустой интерфейс используется для обозначения набора типов, замените интерфейс настраиваемого атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, когда интерфейс используется для идентификации набора типов во время компиляции.

## <a name="example"></a>Пример
 В следующем примере пустой интерфейс.

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]