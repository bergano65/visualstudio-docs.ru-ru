---
title: Функция SccEndBatch | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 6b7fc5afbc5b1a084f0c5d84f5daf1cb7f257364
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869431"
---
# <a name="sccendbatch-function"></a>Функция SccEndBatch
Эта функция завершается пакет операций системы управления версиями. Эти пакеты не могут быть вложенными.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
## <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Пакет успешно завершения операции.|  
|SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Пакеты управления источника используются выполнения же операций системы управления версиями для нескольких проектов или в нескольких контекстах. Пакеты можно использовать во избежание избыточных диалоговым окнам от работы во время пакетной операции. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) и `SccEndBatch` функции используются как пара для указания начала и окончания операции. Они не могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)