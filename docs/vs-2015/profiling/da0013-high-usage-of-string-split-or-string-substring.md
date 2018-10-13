---
title: DA0013. Интенсивное использование String.Split или String.Substring | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e738444b2a8e3e888da406097e94fbc9e10a28
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198696"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: интенсивное использование String.Split или String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ИД правила | DA0013 |  
| Категория |. Руководство по использованию .NET Framework |  
| Методы профилирования | Выборка |  
| Сообщение | Рекомендуется снизить использование функций String.Split и String.Substring. |  
| Тип правила | Предупреждение |  
  
## <a name="cause"></a>Причина  
 Вызовы методов System.String.Split и System.String.Substring составляют значительную часть данных профилирования. Рекомендуется использовать метод System.String.IndexOf или System.String.IndexOfAny при проверке существования подстроки в строке.  
  
## <a name="rule-description"></a>Описание правила  
 Метод Split обрабатывает объект типа "строка" и возвращает массив строк, содержащих подстроки исходной строки. Функция выделяет память для возвращаемого объекта типа "массив" и для новых объектов типа "строка" для каждого элемента массива. Аналогичным образом метод Substr обрабатывает объект типа "строка" и возвращает новую строку, эквивалентную подстроке, которая была запрошена.  
  
 Если приложение критично к управлению выделением памяти, рассмотрите возможность использования других методов вместо String.Split и String.Substr. Например, можно использовать метод IndexOf или IndexOfAny для поиска конкретной подстроки в строке символов без создания нового экземпляра класса String.  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Дважды щелкните сообщение в окне "Список ошибок", чтобы перейти к представлению [Сведения о функциях](../profiling/function-details-view.md) выборки данных профилирования. Проверьте вызовы функций, чтобы найти участки программы, в которых наиболее часто используются методы System.String.Split и System.String.Substr. По возможности старайтесь использовать методы IndexOf и IndexOfAny для поиска нужной подстроки в строке символов без создания нового экземпляра класса String.



