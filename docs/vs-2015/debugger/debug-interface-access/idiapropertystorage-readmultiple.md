---
title: 'Идиапропертистораже:: Реадмултипле | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538087"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает указанные свойства из текущего набора свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cpspec`  
 окне Количество свойств, указанных в `rgpspec` массиве. Если значение равно нулю, метод не возвращает свойства, но возвращает `S_OK` как код успешного выполнения.  
  
 `rgpspec`  
 окне Массив свойств для чтения. Свойства могут быть заданы либо с помощью идентификатора свойства, либо с помощью необязательного имени строки. Нет необходимости указывать свойства в каком-либо определенном порядке в массиве. Массив может содержать дублирующиеся свойства, что приводит к дублированию значений свойств при возврате для простых свойств. Непростые свойства должны возвращать отказ в доступе при попытке открыть их во второй раз. Массив может содержать сочетание идентификаторов свойств и строковых идентификаторов. Этот массив должен иметь по крайней мере `cpspec` ряд значений свойств.  
  
 `rgvar`  
 [вход, выход] Массив `PROPVARIANT` структур (в пространстве имен Microsoft. VisualStudio. OLE. Interop), который должен быть заполнен значениями для каждого свойства. Размер массива должен быть не меньше `cpspec` элементов. Вызывающему объекту не нужно инициализировать значения в массиве.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает, `S_FALSE` Если одно или несколько свойств не были найдены. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если свойство не найдено, соответствующая запись в `rgvar` массиве содержит объект `VARIANT` с типом `VT_EMPTY` .  
  
## <a name="see-also"></a>См. также:  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
