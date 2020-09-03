---
title: Функция Сккбегинбатч | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189563"
---
# <a name="sccbeginbatch-function"></a>Функция SccBeginBatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция запускает пакетную последовательность операций системы управления версиями. Для завершения пакета будет вызван [скцендбатч](../extensibility/sccendbatch-function.md) . Эти пакеты не могут быть вложенными.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Пакетная операция успешно началась.|  
|SCC_E_UNKNOWNERROR|Неконкретный сбой.|  
  
## <a name="remarks"></a>Remarks  
 Пакеты управления версиями используются для выполнения одних и тех же операций в нескольких проектах или нескольких контекстах. Пакеты можно использовать для исключения избыточных диалоговых окон для отдельных проектов из процесса выполнения пакетной операции. `SccBeginBatch`Функция и [скцендбатч](../extensibility/sccendbatch-function.md) используются в качестве пары функций для указания начала и конца операции. Они не могут быть вложенными. `SccBeginBatch` задает флаг, указывающий, что выполняется пакетная операция.  
  
 Во время выполнения пакетной операции подключаемый модуль системы управления версиями должен представлять максимум одно диалоговое окно для любого вопроса пользователя и применять ответ от этого диалогового окна во всех последующих операциях.  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
