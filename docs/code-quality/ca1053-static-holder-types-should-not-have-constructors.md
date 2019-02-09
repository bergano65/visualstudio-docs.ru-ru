---
title: CA1053. Типы со статическими заполнителями не должны иметь конструкторы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da5edc8f31510fa01d2132735ede502ad7f6ad6a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922606"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053. Типы со статическими заполнителями не должны иметь конструкторы

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 В открытом или вложенном открытом типе объявляются только статические элементы и имеется открытый или защищенный конструктор по умолчанию.

## <a name="rule-description"></a>Описание правила
 Конструктор не нужен, поскольку при вызове статических членов не требуется экземпляр типа. Кроме того так как тип не имеет нестатических членов, создание экземпляра не предоставляет доступ к любому из элементов этого типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите конструктор по умолчанию или сделать ее частной.

> [!NOTE]
>  Некоторые компиляторы автоматически создает открытый конструктор по умолчанию, если тип не определены другие конструкторы. Если это происходит с типом, добавьте закрытый конструктор по умолчанию для устранения нарушения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Наличие конструктора предполагает, что тип не является статическим типом.

## <a name="example"></a>Пример
 В следующем примере тип, который нарушает это правило. Обратите внимание, что в исходном коде нет конструктора по умолчанию. Когда этот код компилируется в сборку, компилятор C# вставит конструктор по умолчанию, которые будут нарушать это правило. Чтобы исправить эту ошибку, объявите закрытый конструктор.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]