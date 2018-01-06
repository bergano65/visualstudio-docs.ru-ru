---
title: "Функция SccBeginBatch | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBeginBatch
helpviewer_keywords: SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d6415953a350321cb13f2705fa2bb182c278faa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Пакет управления успешно начата.|  
|SCC_E_UNKNOWNERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Пакеты управления источника используются для выполнения одинаковых операций по нескольким проектам или несколько контекстов. Пакеты можно использовать для устранения избыточных проекта диалоговые окна из взаимодействие с пользователем во время пакетной операции. `SccBeginBatch` Функции и [SccEndBatch](../extensibility/sccendbatch-function.md) используются как пара функций для определения начала и окончания операции. Они не могут быть вложенными. `SccBeginBatch`Задает флаг, указывающий, что пакетная операция находится в разработке.  
  
 Когда действует пакетной операции, подключаемый модуль системы управления версиями следует не более одного диалогового окна для каких-либо вопросов пользователь видит и применить ответ в этом диалоговом для всех последующих операций.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)