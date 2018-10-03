---
title: DA0008. Собрано мало выборок | Документы Майкрософт
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
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 205bedf2baa7c9fa1e1c5f40ccbaa4041427074b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573231"
---
# <a name="da0008-few-samples-collected"></a>DA0008. Собрано несколько образцов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DA0008: собрано несколько образцов](https://docs.microsoft.com/visualstudio/profiling/da0008-few-samples-collected).  
  
ИД правила | DA0008 |  
| Категория | Использование средств профилирования |  
| Метод профилирования | Выборка |  
| Сообщение | Были собраны только небольшое число выборок. Рекомендуется использовать более высокую частоту выборки выполнения или быстрее для получения значительных результатов. |  
| Тип правила | Сведения |  
  
## <a name="cause"></a>Причина  
 В сеансе профилирования было собрано небольшое число выборок.  
  
## <a name="rule-description"></a>Описание правила  
 При использовании метода выборки следует собрать статистически значимое число выборок, чтобы данные отражали фактическое поведение программы. Чтобы свести к минимуму ошибки выборки, нужно собрать по крайней мере 1000 выборок данных по выполнению инструкции программы. Недостаточное количество выборок может привести к неправильным выводам при анализе данных профилирования.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Для получения статистически значимых результатов рекомендуется дольше выполнять процедуру профилирования приложения или увеличить частоту выборки. Дополнительные сведения об изменении частоты выборки в интегрированной среде разработки Visual Studio см. в разделе [Практическое руководство. Выбор событий выборки](../profiling/how-to-choose-sampling-events.md). Дополнительные сведения об изменении частоты выборки при использовании командной строки средств профилирования см. в разделе [Таймер](../profiling/timer.md) руководства [VSPerfCmd](../profiling/vsperfcmd.md).



