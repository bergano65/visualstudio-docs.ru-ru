---
title: "DA0029: неподдерживаемая версия среды CLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# DA0029: неподдерживаемая версия среды CLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Идентификатор правила|DA0029|  
|Категория|Использование средств профилирования|  
|Метод профилирования|Профилирование из командной строки.|  
|Сообщение|В процессе сбора данных обнаружена неподдерживаемая версия среды CLR.  Невозможно надлежащим образом устранить конфликт управляемых символов.|  
|Тип правила|Сведения.|  
  
## Причина  
 Предпринята попытка профилирования приложения, в котором используется платформа [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], не поддерживаемая средствами профилирования.  
  
## Описание правила  
 Это предупреждение выдается, поскольку средства профилирования не смогут устранить конфликт символов в управляемом коде, выполняющемся в приложении.  Средства профилирования не могут устранять конфликт символов управляемого кода в приложениях для платформы [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## Устранение нарушений  
 Нет.