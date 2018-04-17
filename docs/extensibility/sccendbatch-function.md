---
title: Функция SccEndBatch | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec549b5bb0a6c48946edf59f0ab1423cea0ac704
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sccendbatch-function"></a>Функция SccEndBatch
Эта функция завершает пакет операций системы управления версиями. Эти пакеты не могут быть вложенными.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Пакет успешно подтвердила операций.|  
|SCC_E_UNKNOWNERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Пакеты управления источника используются для выполнения одной операции системы управления версиями в нескольких проектах или несколько контекстов. Пакеты можно использовать для устранения избыточных диалоговые окна из взаимодействие с пользователем во время пакетной операции. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) и `SccEndBatch` функции используются как пара для указания начала и окончания операции. Они не могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)