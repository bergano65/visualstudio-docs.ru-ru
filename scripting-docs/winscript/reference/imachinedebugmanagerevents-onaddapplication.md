---
title: "IMachineDebugManagerEvents::onAddApplication | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onAddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onAddApplication
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 887ce7f723713c335d72a6353c20765c7b695031
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagereventsonaddapplication"></a>IMachineDebugManagerEvents::onAddApplication
Обрабатывает событие, при добавлении приложения с запуском список приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pda`  
 [in] Приложения, который был добавлен с запуском список приложений.  
  
 `dwAppCookie`  
 [in] Файл cookie, когда приложение был добавлен в список приложений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод указывает, что приложение был добавлен с запуском список приложений.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)