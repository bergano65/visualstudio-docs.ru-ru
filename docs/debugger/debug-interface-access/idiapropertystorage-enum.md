---
title: IDiaPropertyStorage::Enum | Документация Майкрософт
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
ms.openlocfilehash: 2ff182c2600a41a0e7c13ed460418e93f88baaed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871645"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Получает перечислитель для свойств в этом наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppenum`  
 [out] Возвращает `IEnumSTATPROPSTG` объект (в пространстве имен Microsoft.VisualStudio.OLE.Interop), представляющий перечисление свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)