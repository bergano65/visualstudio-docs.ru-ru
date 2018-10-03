---
title: Функция SccGetEvents | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e73fea52d207d4f9834d5c3eabb15bf733c7e23
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561716"
---
# <a name="sccgetevents-function"></a>Функция SccGetEvents
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccGetEvents](https://docs.microsoft.com/visualstudio/extensibility/sccgetevents-function).  
  
Эта функция извлекает событие состояния в очереди.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 lpFileName  
 [in, out] Буфер, который подключаемый модуль системы управления версиями помещает имя возвращенного файла (до _MAX_PATH символов).  
  
 lpStatus  
 [in, out] Возвращает код состояния (см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md) возможные значения).  
  
 pnEventsRemaining  
 [in, out] Возвращает число записей останется в очереди, после этого вызова. Если это число велико, вызывающий объект может понадобиться вызвать [SccQueryInfo](../extensibility/sccqueryinfo-function.md) для получения всех сведений за один раз.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Получение событий выполнено успешно.|  
|SCC_E_OPNOTSUPPORTED|Эта функция не поддерживается.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция вызывается во время простоя обработки, чтобы увидеть, были обновлений состояния для файлов в системе управления версиями. Подключаемый модуль системы управления версиями поддерживает состояние всех файлов, которые, как известно, и каждый раз, когда изменение состояния указано для подключаемого модуля, состояние и связанного файла хранятся в очереди. Когда `SccGetEvents` вызывается верхней извлекается и возвращается элемент очереди. Эта функция ограничен для возврата только ранее кэшированные данные и должны иметь очень быстрое (то есть без чтения с диска или запрашивает состояние системы управления версиями); в противном случае производительность интегрированной среды разработки может начать снижаться.  
  
 Если отчет не обновляется состояние, подключаемый модуль системы управления версиями сохраняет пустую строку в буфере, на которые указывают `lpFileName`. В противном случае подключаемый модуль сохраняет полный путь файла, для которой сведения о состоянии изменилась и возвращает код соответствующего состояния (одно из значений, описанных в [код состояния файла](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)

