---
title: Функция SccGetEvents | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79e517d87acd61eafcd2eb0a12f5a8978912db81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetevents-function"></a>Функция SccGetEvents
Эта функция извлекает события в очереди состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 lpFileName  
 [in, out] Буфер, который подключаемый модуль системы управления версиями помещает возвращенным именем (до _MAX_PATH символов).  
  
 lpStatus  
 [in, out] Возвращает код состояния (см. [код состояния файла](../extensibility/file-status-code-enumerator.md) возможные значения).  
  
 pnEventsRemaining  
 [in, out] Возвращает число записей останется в очереди, после этого вызова. Это число имеет большой размер, вызывающий объект может потребоваться вызвать [SccQueryInfo](../extensibility/sccqueryinfo-function.md) для получения всех данных за один раз.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Получите события успешно выполнен.|  
|SCC_E_OPNOTSUPPORTED|Эта функция не поддерживается.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция вызывается во время простоя обработки, чтобы увидеть, были обновлений состояния для файлов в системе управления версиями. Подключаемый модуль системы управления версиями хранит состояние всех файлов, которые, как известно, и при каждом изменении состояния, указывается для подключаемого модуля, состояние и связанный файл хранятся в очереди. Когда `SccGetEvents` вызывается верхней очереди извлекается и возвращается. Эта функция будет ограничен вернуть только ранее кэшированные данные и должен иметь очень быстрое (то есть без чтения диска или запрашивает состояние системы управления версиями); в противном случае производительность интегрированной среды разработки может начать снижаться.  
  
 Если состояние не обновлялось отчет, подключаемый модуль системы управления версиями сохраняет пустую строку в буфере, на который указывает `lpFileName`. В противном случае подключаемый модуль сохраняет полный путь файла, для которого сведения о состоянии изменилась и возвращает код состояния, соответствующие (одно из значений, описанные в [код состояния файла](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)