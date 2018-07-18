---
title: IDiaPropertyStorage::Enum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: f0fe51224a4b4a5abc73a3edb7a2caf239d32efb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459094"
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