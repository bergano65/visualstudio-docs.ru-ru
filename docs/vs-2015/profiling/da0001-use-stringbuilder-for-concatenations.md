---
title: DA0001. Использование StringBuilder для объединений | Документы Майкрософт
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
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c177af60768da4a4360fbeed8e2664129bd9681f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561452"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001. Использование StringBuilder для объединений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [DA0001: использование StringBuilder для объединений](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|Идентификатор правила|DA0001|  
|Категория|Использование .NET Framework|  
|Методы профилирования|Дискретизация<br /><br /> Инструментирование|  
|Сообщение|Рекомендуется использовать класс StringBuilder для объединения строк.|  
|Тип сообщения|Предупреждение|  
  
## <a name="cause"></a>Причина  
 Вызовы метода System.String.Concat составляют значительную часть данных профилирования. Для построения строк из нескольких сегментов рекомендуется использовать класс <xref:System.Text.StringBuilder>.  
  
## <a name="rule-description"></a>Описание правила  
 Объект <xref:System.String> является неизменяемым. Таким образом, любые изменения в строке приводят к созданию нового объекта типа string и необходимости удаления исходного объекта при сборке мусора. Выполнение операции происходит одинаково как при явном вызове метода String.Concat, так и при использовании операторов объединения строк, таких как + или +=. Производительность программы может снизиться, если эти методы вызываются слишком часто, например, при добавлении символов в строку в цикле с большим числом итераций.  
  
 Класс StringBuilder является изменяемым объектом и, в отличие от System.String, большинство методов для работы с классом StringBuilder, изменяющих экземпляр этого класса, возвращают ссылку на тот же экземпляр. Можно вставлять символы или добавлять текст в экземпляр класса StringBuilder, удалять или заменять символы в этом экземпляре. При этом не требуется размещение нового экземпляра и удаление исходного.  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Дважды щелкните сообщение в окне "Список ошибок", чтобы перейти к представлению [Сведения о функциях](../profiling/function-details-view.md) выборки данных профилирования. Найдите участок программы, в котором наиболее часто используются операции объединения строк. Для выполнения сложных операций со строками, а также частых операций объединения строк используйте класс StringBuilder.  
  
 Дополнительные сведения о работе со строками см. в подразделе [Строковые операции](http://go.microsoft.com/fwlink/?LinkId=177816) в разделе [Глава 5. Улучшение производительности управляемого кода](http://go.microsoft.com/fwlink/?LinkId=177817) в библиотеке шаблонов и методик Microsoft.

