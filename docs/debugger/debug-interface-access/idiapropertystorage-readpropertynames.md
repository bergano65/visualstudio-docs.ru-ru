---
title: IDiaPropertyStorage::ReadPropertyNames | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1624e3577128556a098f96fd41c9ba1dc1eb84e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Извлекает соответствующие имена строки для заданного идентификаторов свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cpropid`  
 [in] Количество идентификаторов свойств в `rgpropid`.  
  
 `rgpropid`  
 [in] Массив идентификаторов свойств, для которого необходимо получить имена (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Массив имен свойств для указанного свойства идентификаторов. Массив должен быть предварительно выделить запрошенное число имен свойств и должен иметь возможность по крайней мере `cpropid``BSTR` строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Имя возвращаемого свойства освобождения (путем вызова `SysFreeString` функция) когда они больше не нужны.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)