---
title: "IDebugProperty::GetExtendedInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Возвращает расширенные сведения для свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cInfos`  
 [in] Счетчик расширенных сведений об объектах.  
  
 `rgguidExtendedInfo`  
 [in] Массив `GUID`s передается, чтобы несколько объектов расширенных сведения можно получить в то же время.  
  
 `pExtendedInfo`  
 [out] Возвращает массив `VARIANT`s, который может использоваться для получения сведений о расширенных свойствах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимую `HRESULT`, обычно `S_OK`.  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс возвращает расширенные сведения для этого объекта. API существует только с целью получения информации, которая непригодны для извлекаемых с помощью `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)