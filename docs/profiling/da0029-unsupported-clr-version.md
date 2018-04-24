---
title: 'DA0029: неподдерживаемая версия среды CLR | Документы Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad41dc48303fa836e4c15f0e450b3fade60ff646
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: неподдерживаемая версия среды CLR
|||  
|-|-|  
|Идентификатор правила|DA0029|  
|Категория|Использование средств профилирования|  
|Способ профилирования|Профилирование из командной строки|  
|Сообщение|В процессе сбора данных обнаружена неподдерживаемая версия среды CLR. Невозможно надлежащим образом устранить конфликт управляемых символов.|  
|Тип правила|Сведения.|  
  
## <a name="cause"></a>Причина  
 Предпринята попытка профилирования приложения, в котором используется платформа [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], не поддерживаемая Средствами профилирования.  
  
## <a name="rule-description"></a>Описание правила  
 Это предупреждение выдается по той причине, что Средствам профилирования не удается разрешить символы в управляемом коде, выполняющемся в приложении. Средства профилирования не могут разрешать символы управляемого кода в приложениях для платформы [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Отсутствует.