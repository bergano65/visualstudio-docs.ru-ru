---
title: IDebugProperty::GetExtendedInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c66ea53bde17f2936567cd93ae0be166f35382ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925546"
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
 [in] Массив `GUID`s передается, чтобы можно было получить несколько элементов из расширенных сведений в то же время.  
  
 `pExtendedInfo`  
 [out] Возвращает массив `VARIANT`s, который может использоваться для получения этих данных расширенного свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс возвращает расширенные сведения для этого объекта. API существует только в целях получения информации, которая не совместима получить с помощью `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)