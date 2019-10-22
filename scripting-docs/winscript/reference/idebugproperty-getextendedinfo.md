---
title: 'IDebugProperty:: Жетекстендединфо | Документация Майкрософт'
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
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562390"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Получает расширенные сведения для свойства.  
  
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
 окне Число объектов расширенной информации.  
  
 `rgguidExtendedInfo`  
 окне Передается массив `GUID`s, чтобы можно было получить одновременно несколько элементов расширенной информации.  
  
 `pExtendedInfo`  
 заполняет Возвращает массив `VARIANT`s, который можно использовать для получения сведений о расширенных свойствах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="remarks"></a>Заметки  
 Этот интерфейс получает расширенные сведения для этого объекта. API существует только в целях извлечения сведений, которые не могут быть извлечены при использовании `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)