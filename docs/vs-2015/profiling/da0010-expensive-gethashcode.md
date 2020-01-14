---
title: DA0010. Затратный метод GetHashCode | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0a2947f0bd6758de62a4a11d78390d38a503271
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919032"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010. Затратный метод GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [DA0010: дорогостоящий GetHashCode](/visualstudio/profiling/da0010-expensive-gethashcode).  

|||  
|-|-|  
|ИД правила|DA0010|  
|Категория|Использование .NET Framework|  
|Методы профилирования|Дискретизация<br /><br /> Память .NET|  
|Message|Функции GetHashCode должны быть малозатратными и не должны выделять память. Если возможно, уменьшите сложность функции хэш-кода.|  
|Тип сообщения|Предупреждение|  
  
## <a name="cause"></a>Причина:  
 Вызовы метода GetHashCode типа составляют значительную часть данных профилирования, или метод выделяет память.  
  
## <a name="rule-description"></a>Описание правила  
 Хэширование — это метод для быстрого нахождения определенного элемента в большой коллекции. Так как хэш-таблицы могут быть очень большими и поддерживать высокую скорость доступа, хэш-таблицы должны быть чрезвычайно эффективны. Это требование подразумевает, что методы GetHashCode в .NET Framework не должны выделять память. Выделение памяти увеличивает нагрузку на сборщик мусора и повышает вероятность задержек метода, если станет необходимо выполнить сборку мусора в результате выполнения запроса на выделение памяти.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Упростите метод.
