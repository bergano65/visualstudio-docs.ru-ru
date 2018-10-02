---
title: 'CA1012: Абстрактные типы не должны иметь конструкторы | Документация Майкрософт'
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
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 692dfc0ad69cf4d71d82953e2cc9965733915dc6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591645"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: абстрактные типы не должны иметь конструкторы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1012: абстрактные типы не должны иметь конструкторы](https://docs.microsoft.com/visualstudio/code-quality/ca1012-abstract-types-should-not-have-constructors).

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип является абстрактным и имеет открытый конструктор.

## <a name="rule-description"></a>Описание правила
 Конструкторы абстрактных типов могут быть вызваны только производными типами. Открытые конструкторы создают экземпляры типа. Невозможно создавать экземпляры абстрактного типа; абстрактный тип с открытым конструктором является недопустимым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, защищать конструктор, или не объявите тип как абстрактный.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Абстрактный тип имеет открытый конструктор без параметров.

## <a name="example"></a>Пример
 Следующий пример содержит абстрактный тип, который нарушает это правило.

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение устраняется путем изменения специальных возможностей конструктора из `public` для `protected`.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]



