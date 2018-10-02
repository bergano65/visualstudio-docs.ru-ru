---
title: 'CA2121: Статические конструкторы должны быть частными | Документация Майкрософт'
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
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b7052a25df5e736276b458247eb625ab584d473
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591597"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: статические конструкторы должны быть частными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2121: статические конструкторы должны быть частными](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private).

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип имеет статический конструктор, который не является закрытым.

## <a name="rule-description"></a>Описание правила
 Статический конструктор, также известный как конструктор класса, используется для инициализации типа. Система вызывает статический конструктор перед созданием первого экземпляра типа или ссылкой на любые статические члены. Пользователь имеет не контролирует, когда вызывается статический конструктор. Если статический конструктор не является закрытым, он может быть вызван кодом, находящимся за пределами системы. В зависимости от операций, выполняемых в конструкторе, это может стать причиной непредвиденного поведения

 Это правило применяется компиляторами C# и Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Нарушения обычно вызваны одной из следующих действий:

-   Определен статический конструктор для типа и не поступивший закрытый.

-   Компилятор языка программирования добавлен статический конструктор по умолчанию к типу и не поступивший закрытый.

 Чтобы устранить нарушение первого типа, сделайте ваш статический конструктор закрытым. Чтобы устранить второго типа, добавьте закрытый статический конструктор для данного типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать эти нарушения. Если программе требуется явный вызов в статическом конструкторе, весьма вероятно, что проект содержит серьезные недостатки и должны быть проверены.



