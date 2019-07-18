---
title: Метод marker_series::write_alert | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d65bec449938a55ee9a415dd86db1ba07efbdb1b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54792851"
---
# <a name="markerserieswritealert-method"></a>Метод marker_series::write_alert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Записывает оповещение в файл трассировки визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `_Format`  
 Строка составного формата, содержащая текст, перемежаемый нулями или другими элементами форматирования, которые соответствуют объектам в списке аргументов.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также раздел  
 [Класс marker_series](../profiling/marker-series-class.md)
