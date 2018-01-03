---
title: "DA0010. Затратный метод GetHashCode | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ff2dbc1d98375b7199ab710412639fe4333c342d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="da0010-expensive-gethashcode"></a>DA0010. Затратный метод GetHashCode
|||  
|-|-|  
|Идентификатор правила|DA0010|  
|Категория|Использование .NET Framework|  
|Методы профилирования|Дискретизация<br /><br /> Память .NET|  
|Сообщение|Функции GetHashCode должны быть малозатратными и не должны выделять память. Если возможно, уменьшите сложность функции хэш-кода.|  
|Тип сообщения|Предупреждение|  
  
## <a name="cause"></a>Причина  
 Вызовы метода GetHashCode типа составляют значительную часть данных профилирования, или метод выделяет память.  
  
## <a name="rule-description"></a>Описание правила  
 Хэширование — это метод для быстрого нахождения определенного элемента в большой коллекции. Так как хэш-таблицы могут быть очень большими и должны поддерживать очень высокую интенсивность доступа, они должны быть крайне эффективными. Это требование подразумевает, что методы GetHashCode в .NET Framework не должны выделять память. Выделение памяти увеличивает нагрузку на сборщик мусора и повышает вероятность задержек метода, если станет необходимо выполнить сборку мусора в результате выполнения запроса на выделение памяти.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Упростите метод.