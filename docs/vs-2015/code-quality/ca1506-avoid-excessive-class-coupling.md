---
title: CA1506. Избегайте чрезмерного соединения классов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 1c5a5e070892f7efc096b0f8e24952bb9d139969
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189289"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506. Избегайте чрезмерной взаимозависимости классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
