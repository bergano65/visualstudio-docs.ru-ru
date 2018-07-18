---
title: Функция SccBeginBatch | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5350484294d02356301839e38b97bea1d40ec27c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138240"
---
# <a name="sccbeginbatch-function"></a>Функция SccBeginBatch
Эта функция служит началом последовательности пакетных операций системы управления версиями. [SccEndBatch](../extensibility/sccendbatch-function.md) будет вызываться до конца пакета. Эти пакеты не могут быть вложенными.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Пакет управления успешно начата.|  
|SCC_E_UNKNOWNERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Пакеты управления источника используются для выполнения одинаковых операций по нескольким проектам или несколько контекстов. Пакеты можно использовать для устранения избыточных проекта диалоговые окна из взаимодействие с пользователем во время пакетной операции. `SccBeginBatch` Функции и [SccEndBatch](../extensibility/sccendbatch-function.md) используются как пара функций для определения начала и окончания операции. Они не могут быть вложенными. `SccBeginBatch` Задает флаг, указывающий, что пакетная операция находится в разработке.  
  
 Когда действует пакетной операции, подключаемый модуль системы управления версиями следует не более одного диалогового окна для каких-либо вопросов пользователь видит и применить ответ в этом диалоговом для всех последующих операций.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)