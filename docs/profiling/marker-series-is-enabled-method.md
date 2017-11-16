---
title: "Метод marker_series::is_enabled | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords: Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9de16a85ca956f3f8a488a76b50eb2738c705aca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="markerseriesisenabled-method"></a>Метод marker_series::is_enabled
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