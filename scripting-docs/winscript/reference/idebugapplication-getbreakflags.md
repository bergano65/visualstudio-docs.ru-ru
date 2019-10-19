---
title: 'IDebugApplication:: Жетбреакфлагс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetBreakFlags
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a614429ebb8cc9271a0444536d14c45b69a9588f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574976"
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
Возвращает текущие флаги разрыва для приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pabf`  
 заполняет Текущие флаги разрыва для приложения.  
  
 `pprdatSteppingThread`  
 заполняет Текущий выполняющийся поток.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает текущие флаги разрыва для приложения.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Перечисление APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)