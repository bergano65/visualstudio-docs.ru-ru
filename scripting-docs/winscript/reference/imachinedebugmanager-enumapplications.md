---
title: IMachineDebugManager::EnumApplications | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::EnumApplications
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a75af7e151ad233e1bd592203fb33d2cd7f5cbe
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149280"
---
# <a name="imachinedebugmanagerenumapplications"></a>IMachineDebugManager::EnumApplications
Возвращает перечислитель текущего списка выполняющихся приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppeda`  
 [out] Перечислитель, содержащий текущий список работающих приложений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает перечислитель текущего списка выполняющихся приложений. Интегрированная среда разработки отладчика использует этот метод для отображения и добавления приложений в целях отладки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)