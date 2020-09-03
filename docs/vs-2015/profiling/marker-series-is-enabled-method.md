---
title: Метод marker_series::is_enabled | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ccef8ebbf63835a71027643b518280d5f4f867b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156415"
---
# <a name="marker_seriesis_enabled-method"></a>Метод marker_series::is_enabled
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
  
## <a name="see-also"></a>См. также:  
 [Класс marker_series](../profiling/marker-series-class.md)
