---
title: IDiaPropertyStorage::ReadMultiple | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b8be22e2a855f19c412725833fa18e182ebff6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904058"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Чтение указанного свойства из текущего набора свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cpspec`  
 [in] Число свойств, указанных в `rgpspec` массива. Если значение равно нулю, метод возвращает нет свойств, но возвращает `S_OK` как код успешного выполнения.  
  
 `rgpspec`  
 [in] Массив свойств для чтения. Свойства могут быть указаны с Идентификатором свойства объекта или имени необязательная строка. Это не требуется указывать свойства в определенном порядке в массиве. Массив может содержать повторяющиеся свойства, что повторяющиеся значения при возвращении для простых свойств. Свойства non-simple должны возвращать отказано в доступе при попытке открыть их еще раз. Массив может содержать смесь идентификаторы свойств и строковых идентификаторов. Этот массив должен иметь по крайней мере `cpspec` число значений свойств.  
  
 `rgvar`  
 [in, out] Массив `PROPVARIANT` структуры (в пространстве имен Microsoft.VisualStudio.OLE.Interop), который подлежит заполнению значения для каждого свойства. Размер массива должен быть по крайней мере `cpspec` элементов в размер. Вызывающему объекту не требуется для инициализации значений в массиве.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если один или несколько свойств не найден. В противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если свойство не найдено, соответствующая запись в `rgvar` массив содержит `VARIANT` с типом `VT_EMPTY`.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)