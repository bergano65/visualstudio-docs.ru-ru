---
title: 'IDebugApplication:: Аддстаккфрамесниффер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a461c24b6f62f1e0ece88915e097faf0c59f15e7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575035"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Добавляет поставщик перечислителя кадра стека в это приложение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdsfs`  
 окне Поставщик перечислителя кадров стека для добавления в это приложение.  
  
 `pdwCookie`  
 заполняет Файл cookie, используемый для удаления этого поставщика перечислителя кадров стека из приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Хотя обработчики языка обычно вызывают этот метод для предоставления кадров стека отладчику, другие сущности могут предоставлять фреймы стека.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugApplication:: ремовестаккфрамесниффер](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [Интерфейс IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)