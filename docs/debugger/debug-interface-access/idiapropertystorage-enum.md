---
title: IDiaPropertyStorage::Enum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ef00407d42ec534c509e4e38de0ca0538edcbcf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Возвращает перечислитель для свойств в этом наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppenum`  
 [out] Возвращает `IEnumSTATPROPSTG` объекта (в пространстве имен Microsoft.VisualStudio.OLE.Interop), представляющий перечисление свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)