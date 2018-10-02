---
title: Перечисление marker_importance | Документы Майкрософт
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
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1564de8b63efa48ad83b1aa09f1fce75ff3fbd75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571109"
---
# <a name="markerimportance-enumeration"></a>Перечисление marker_importance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [перечисление marker_importance](https://docs.microsoft.com/visualstudio/profiling/marker-importance-enumeration).  
  
Представляет уровень важности маркера визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
|`critical_importance`|Указывает, что маркер имеет критическую важность.|  
|`high_importance`|Указывает, что маркер имеет высокую важность.|  
|`low_importance`|Указывает, что маркер имеет низкую важность.|  
|`normal_importance`|Указывает, что маркер имеет обычную важность.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также  
 [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)



