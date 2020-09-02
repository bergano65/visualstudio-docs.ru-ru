---
title: IDiaPropertyStorage::ReadPropertyNames | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537424"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает соответствующие имена строк для заданных идентификаторов свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cpropid`  
 окне Количество идентификаторов свойств в `rgpropid` .  
  
 `rgpropid`  
 окне Массив идентификаторов свойств, для которых необходимо получить имена ( `PROPID` определяется в втипес. h как `ULONG` ).  
  
 `rglpwstrName`  
 [вход, выход] Массив имен свойств для заданных идентификаторов свойств. Массив должен быть предварительно выделен для хранения запрошенного числа имен свойств и должен иметь возможность хранить по меньшей мере `cpropid``BSTR` строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Возвращаемые имена свойств должны быть освобождены (путем вызова `SysFreeString` функции), когда они больше не нужны.  
  
## <a name="see-also"></a>См. также:  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
