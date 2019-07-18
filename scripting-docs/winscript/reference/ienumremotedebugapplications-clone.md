---
title: IEnumRemoteDebugApplications::Clone | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Clone
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06b2eac008b0bccc3d0671e15658b5a189b5dcaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963277"
---
# <a name="ienumremotedebugapplicationsclone"></a>IEnumRemoteDebugApplications::Clone
Создает перечислитель с тем же состоянием, что и текущий перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppessd`  
 [out] Клон объекта перечислителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод создает перечислитель, который с тем же состоянием, что и текущий перечислитель.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)