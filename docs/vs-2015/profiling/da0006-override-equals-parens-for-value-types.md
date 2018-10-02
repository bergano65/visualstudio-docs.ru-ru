---
title: DA0006. Переопределение Equals() для типов значений | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4e7535775946c99d6b176f36ca10288a8bc9da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563872"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006. Переопределение Equals() для типов значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DA0006: переопределение Equals() для типов значений](https://docs.microsoft.com/visualstudio/profiling/da0006-override-equals-parens-for-value-types).  
  
ИД правила | DA0006 |  
| Категория |. Использование .NET Framework |  
| Методы профилирования | Выборка |  
| Сообщение | Переопределения Equals и оператор равенства для типов значений. |  
| Тип сообщения | Предупреждение |  
  
## <a name="cause"></a>Причина  
 Вызовы метода Equals или операторов равенства открытого типа составляют значительную часть данных профилирования. Рекомендуется использовать более эффективный метод.  
  
## <a name="rule-description"></a>Описание правила  
 В унаследованной реализации Equals для типов значений используется библиотека <xref:System.Reflection> и сравнивается содержимое всех полей типа. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если предполагается, что пользователи будут сравнивать, сортировать экземпляры или использовать их в качестве ключей хэш-таблиц, тип значения должен реализовывать Equals. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.  
  
 Дополнительные сведения о переопределении Equals и операторов равенства см. в разделе [Правила реализации метода Equals и оператора равенства (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Пример реализации Equals и операторов равенства см. в описании правила анализа кода [CA1815: следует переопределять равенства и равенства операторов в типах значений](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md).



