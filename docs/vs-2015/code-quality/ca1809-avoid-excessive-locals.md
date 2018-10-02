---
title: 'CA1809: Избегайте чрезмерного использования локальных переменных | Документация Майкрософт'
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
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c41836e2a7e7e5530d83ff0eaf854b88de42f38f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591702"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: избегайте чрезмерного использования локальных переменных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1809: Избегайте чрезмерного использования локальных переменных](https://docs.microsoft.com/visualstudio/code-quality/ca1809-avoid-excessive-locals).

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член содержит более 64 локальных переменных, некоторые из которых может быть созданный компилятором.

## <a name="rule-description"></a>Описание правила
 Обычно для оптимизации производительности рекомендуется хранить значение в регистр процессора, а не в памяти, что называется *регистре* значение. Среда CLR рассматривает до 64 локальных переменных в среде. Переменные, незарегистрированные помещаются в стек и должны быть перемещены Зарегистрируйтесь до манипуляции. Чтобы разрешить вероятность того, все локальные переменные регистрации, ограничить количество локальных переменных до 64.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполнить рефакторинг реализация, которую нужно использовать не более 64 локальных переменных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, или отключить правило, если производительность не является проблемой.

## <a name="related-rules"></a>Связанные правила
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)



