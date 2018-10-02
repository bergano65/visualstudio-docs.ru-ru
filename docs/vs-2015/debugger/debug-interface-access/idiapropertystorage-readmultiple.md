---
title: IDiaPropertyStorage::ReadMultiple | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7acd4d11167adfc086aa462f51324a80a79e0e4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563739"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaPropertyStorage::ReadMultiple](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage-readmultiple).  
  
Чтение указанного свойства из текущего набора свойств.  
  
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



