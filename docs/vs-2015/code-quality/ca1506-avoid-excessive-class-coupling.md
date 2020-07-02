---
title: 'CA1506: Избегайте чрезмерного связывания классов | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545708"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506. Избегайте чрезмерной взаимозависимости классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип или метод связан с множеством других типов.

## <a name="rule-description"></a>Описание правила
 Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.

 Типы и методы, имеющие высокую степень взаимосвязей классов, могут быть трудно поддерживать. Рекомендуется использовать типы и методы, которые демонстрируют низкую связь и высокую степень связности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, попытайтесь изменить тип или метод, чтобы уменьшить число типов, с которыми он связан.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключите это предупреждение, если тип или метод по-прежнему считается обслуживаемым, несмотря на большое количество зависимостей от других типов.

## <a name="see-also"></a>См. также
 [Предупреждения о поддержке](../code-quality/maintainability-warnings.md) [, измеряющие сложность и удобство сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
