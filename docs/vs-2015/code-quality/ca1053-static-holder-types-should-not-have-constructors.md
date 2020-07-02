---
title: 'CA1053: типы статических владельцев не должны иметь конструкторы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 29cc322dd59dc0de66af8f92a46524d15b0022c7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539585"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053. Типы со статическими заполнителями не должны иметь конструкторы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 В открытом или вложенном открытом типе объявляются только статические элементы и имеется открытый или защищенный конструктор по умолчанию.

## <a name="rule-description"></a>Описание правила
 Конструктор не нужен, поскольку при вызове статических членов не требуется экземпляр типа. Кроме того, поскольку тип не имеет нестатических членов, создание экземпляра не обеспечивает доступ ни к одному из членов типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите конструктор по умолчанию или сделайте его частным.

> [!NOTE]
> Некоторые компиляторы автоматически создают открытый конструктор по умолчанию, если тип не определяет какие-либо конструкторы. Если это так с типом, добавьте закрытый конструктор по умолчанию, чтобы устранить нарушение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Наличие конструктора предполагает, что тип не является статическим.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило. Обратите внимание, что в исходном коде нет конструктора по умолчанию. При компиляции этого кода в сборку компилятор C# вставит конструктор по умолчанию, который нарушает это правило. Чтобы исправить это, объявите закрытый конструктор.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
