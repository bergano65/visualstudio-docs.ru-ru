---
title: 'CA1053: типы статических владельцев не должны иметь конструкторы'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b490fb4a6ad5ffe510f7a443758bc53f5f8f0d99
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: типы статических владельцев не должны иметь конструкторы
|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 В открытом или вложенном открытом типе объявляются только статические элементы и имеется открытый или защищенный конструктор по умолчанию.

## <a name="rule-description"></a>Описание правила
 Конструктор не нужен, поскольку при вызове статических членов не требуется экземпляр типа. Кроме того так как тип не имеет нестатических членов, создание экземпляра не предоставляют доступ к любой из членов типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите конструктор по умолчанию или сделайте его частным.

> [!NOTE]
>  Некоторые компиляторы автоматически создают общий конструктор по умолчанию, если тип не определяет никакие конструкторы. Если это так, с типом, добавьте закрытый конструктор по умолчанию для устранения нарушения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Наличие конструктора предполагает, что тип не является статическим типом.

## <a name="example"></a>Пример
 В следующем примере показано тип, нарушающий это правило. Обратите внимание, что в исходном коде отсутствует конструктор по умолчанию. Если этот код компилируется в сборку, компилятор C# вставит конструктор по умолчанию, которые будут нарушать это правило. Чтобы исправить эту ошибку, объявите закрытый конструктор.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]