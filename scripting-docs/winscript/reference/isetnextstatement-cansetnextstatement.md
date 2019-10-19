---
title: 'Исетнекстстатемент:: Кансетнекстстатемент | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56cf0b2e4afd7a86a087b37be4b23758a5b59720
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571839"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Этот метод определяет, может ли точка выполнения, определяющая следующий оператор кода для выполнения, быть задана в указанном расположении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 окне Указатель на объект кадра стека.  
  
 `pCodeContext`  
 окне Указатель на объект контекста кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Следующий оператор можно обновить до указанного контекста кода.|  
|`S_FALSE`|Следующий оператор не может быть обновлен до указанного контекста кода.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)