---
title: IDiaPropertyStorage::ReadMultiple | Документы Microsoft
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
ms.openlocfilehash: 1747d55de37777a9919f4709a62fbaff4b6d8a2a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
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
 [in] Число свойств, указанных в `rgpspec` массива. Если значение равно нулю, метод возвращает нет свойств, но возвращает `S_OK` как код успешного завершения.  
  
 `rgpspec`  
 [in] Массив свойств для чтения. Свойства задаются с Идентификатором свойства объекта или по имени необязательная строка. Не требуется указывать свойства в конкретном порядке в массиве. Массив может содержать повторяющиеся свойства, что Повторяющееся свойство значения при возвращении для простых свойств. Свойства простой не должны возвращать отказано в доступе при попытке открыть их еще раз. Массив может содержать сочетание идентификаторов свойства и строки. Этот массив должен иметь по крайней мере `cpspec` число значений свойств.  
  
 `rgvar`  
 [in, out] Массив `PROPVARIANT` структуры (в пространстве имен Microsoft.VisualStudio.OLE.Interop), которую можно заполнять значения для каждого свойства. Массив должен быть по крайней мере `cpspec` элементы в размере. Вызывающий объект необходимо инициализировать значения в массиве.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если не был найден один или несколько свойств. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если свойство не найдено, соответствующую запись в `rgvar` содержит массив `VARIANT` с типом `VT_EMPTY`.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)