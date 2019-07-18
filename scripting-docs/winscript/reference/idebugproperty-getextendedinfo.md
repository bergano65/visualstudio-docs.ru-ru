---
title: IDebugProperty::GetExtendedInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 707474f786a8f88c0e08d887f2c2b09c8aaedc8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979127"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Возвращает расширенные сведения для свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Массив `GUID`s передается, чтобы можно было получить несколько элементов из расширенных сведений в то же время.  
  
 `pExtendedInfo`  
 [out] Возвращает массив `VARIANT`s, который может использоваться для получения этих данных расширенного свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс возвращает расширенные сведения для этого объекта. API существует только в целях получения информации, которая не совместима получить с помощью `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)