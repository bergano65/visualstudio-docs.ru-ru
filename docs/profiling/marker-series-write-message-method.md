---
title: Метод marker_series::write_message | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0419ec814c7b2538633ab9a1e266ec12ad066ff9
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="markerserieswritemessage-method"></a>Метод marker_series::write_message
Записывает сообщение в файл трассировки визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `_Format`  
 Строка составного формата, содержащая текст, перемежаемый нулями или другими элементами форматирования, которые соответствуют объектам в списке аргументов.  
  
 `_Importance`  
 Уровень важности.  
  
 `_Category`  
 Категория.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также  
 [Класс marker_series](../profiling/marker-series-class.md)