---
title: 'Идебугсессионпровидерекс: Стартдебугсессион | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:StartDebugSession
apilocation:
- scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfe26265d56b2179feeac2a9802940258074b1c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574296"
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Инициирует сеанс отладки с указанным приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pda`  
 окне Указывает приложение отладки.  
  
 `fQuery`  
 окне Значение true указывает на запрос.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод инициирует сеанс отладки с указанным приложением. Отладчик должен вызвать `IRemoteDebugApplication::ConnectDebugger` перед возвратом из этого вызова.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугсессионпровидерекс](../../winscript/reference/idebugsessionproviderex-interface.md)  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)