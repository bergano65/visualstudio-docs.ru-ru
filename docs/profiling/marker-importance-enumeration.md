---
title: "Перечисление marker_importance | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords: Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae7bb9f300a1d57707966a3b4dbae202eea78d8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="markerimportance-enumeration"></a>Перечисление marker_importance
Представляет уровень важности маркера визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="values"></a>Значения  
  
|name|Описание:|  
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