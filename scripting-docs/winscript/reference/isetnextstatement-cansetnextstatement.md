---
title: ISetNextStatement::CanSetNextStatement | Документация Майкрософт
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
ms.openlocfilehash: eb65faaf107c42b44201ea18c1150f8093b1654c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158949"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Этот метод определяет, можно ли задать точку выполнения, который определяет следующий оператор кода, который будет выполнен, в указанное расположение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 [in] Указатель на кадр стека.  
  
 `pCodeContext`  
 [in] Указатель на объект контекста кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Следующий оператор могут обновляться в контекст указанного кода.|  
|`S_FALSE`|Следующий оператор нельзя обновить до контекст указанного кода.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)