---
title: 'CA1506: Избегайте чрезмерного соединения классов | Документация Майкрософт'
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
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2f96701ccecdd5e3859dcc434a748200f7fd784
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591105"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: избегайте чрезмерного соединения классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1506: Избегайте чрезмерного соединения классов](https://docs.microsoft.com/visualstudio/code-quality/ca1506-avoid-excessive-class-coupling).

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип или метод связана с другими типами.

## <a name="rule-description"></a>Описание правила
 Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.

 Типы и методы, которые с высокой степенью взаимозависимости классов может быть трудно поддерживать. Рекомендуется использовать типы и методы, которые характерны для низкой увязки и высокой связности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, попробуйте изменить тип или метод, чтобы уменьшить количество типов, к которым она связана.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключите это предупреждение, когда тип или метод считается обслуживаемым несмотря на большое количество зависимостей от других типов.

## <a name="see-also"></a>См. также
 [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md) [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



