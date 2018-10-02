---
title: 'CA1053: Типы статических владельцев не должны иметь конструкторы | Документация Майкрософт'
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
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb4d397a5262245771ffd54aadc08a29c5cfcee8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591201"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: типы статических владельцев не должны иметь конструкторы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1053: типы статических владельцев не должны иметь конструкторы](https://docs.microsoft.com/visualstudio/code-quality/ca1053-static-holder-types-should-not-have-constructors).

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

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]



