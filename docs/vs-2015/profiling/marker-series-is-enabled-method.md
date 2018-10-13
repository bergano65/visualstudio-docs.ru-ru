---
title: Метод marker_series::is_enabled | Документы Майкрософт
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
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 774b1281209787a19cdd83e4ef1019e4bf63591c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263800"
---
# <a name="markerseriesisenabled-method"></a>Метод marker_series::is_enabled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет, разрешен ли поставщик данным сеансом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `_Importance`  
 Уровень важности.  
  
 `_Category`  
 Категория.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также  
 [Класс marker_series](../profiling/marker-series-class.md)



