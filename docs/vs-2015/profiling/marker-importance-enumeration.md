---
title: Перечисление marker_importance | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54779041"
---
# <a name="markerimportance-enumeration"></a>Перечисление marker_importance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представляет уровень важности маркера визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="values"></a>Значения  
  
|name|Описание|  
|----------|-----------------|  
|`critical_importance`|Указывает, что маркер имеет критическую важность.|  
|`high_importance`|Указывает, что маркер имеет высокую важность.|  
|`low_importance`|Указывает, что маркер имеет низкую важность.|  
|`normal_importance`|Указывает, что маркер имеет обычную важность.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также раздел  
 [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)
