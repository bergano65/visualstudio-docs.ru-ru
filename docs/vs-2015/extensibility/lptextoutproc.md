---
title: LPTEXTOUTPROC | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37fe822a60e2f4b9628c66d9e4d292e5bc814668
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925569"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При выполнении пользователем операции управления версиями из интегрированной среды разработки (IDE), подключаемый модуль системы управления версиями может потребоваться передать ошибки или состояния сообщения, относящиеся к работе. Подключаемый модуль может отображать свой собственный окон сообщений, для этой цели. Тем не менее более плавной интеграции подключаемого модуля можно передать строки в интегрированную среду разработки, которая затем отображает их в его собственном способ отображения сведений о состоянии. — Это механизм `LPTEXTOUTPROC` указатель на функцию. IDE реализует эту функцию, (более подробно ниже) для отображения ошибок и состояний.  
  
 Интегрированной среды разработки передает в системы управления версиями подключаемого модуля для этой функции, указателя функции как `lpTextOutProc` параметр, при вызове [SccOpenProject](../extensibility/sccopenproject-function.md). Во время операции SCC, например, в процессе вызова [SccGet](../extensibility/sccget-function.md) с участием большого числа файлов, подключаемый модуль можно вызвать `LPTEXTOUTPROC` функции, периодически передачи строк для отображения. Интегрированная среда разработки может отображать эти строки в строке состояния, в окне вывода или в отдельном окне сообщений, соответствующим образом. При необходимости можно попытаться отображения определенных сообщений с помощью интегрированной среды разработки **отменить** кнопки. Это позволяет пользователю отменить операцию, и он дает возможность передать эти сведения обратно в подключаемый модуль интегрированной среды разработки.  
  
## <a name="signature"></a>Подпись  
 Выходной интегрированной среды разработки функции имеет следующую сигнатуру:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Параметры  
 display_string  
 Текстовая строка для отображения. Эта строка не должно оканчиваться каретки возвращаемого значения или перевода строки.  
  
 mesg_type  
 Тип сообщения. В следующей таблице перечислены поддерживаемые значения для этого параметра.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Сообщение считается сведения, предупреждение или ошибка.|  
|`SCC_MSG_STATUS`|Сообщение отображается состояние и могут отображаться в строке состояния.|  
|`SCC_MSG_DOCANCEL`|Отправить строки без сообщения.|  
|`SCC_MSG_STARTCANCEL`|Начинается отображение **отменить** кнопки.|  
|`SCC_MSG_STOPCANCEL`|Останавливает отображение **отменить** кнопки.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Запрашивает интегрированной среды разработки, если фоновая операция — отменить: возвращает IDE `SCC_MSG_RTN_CANCEL` Если операция была отменена; в противном случае возвращает `SCC_MSG_RTN_OK`. `display_string` Приводится параметр [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) структуры, который предоставляется путем подключаемый модуль системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Среда интегрированной разработки о файле, прежде чем он извлекается из системы управления версиями. `display_string` Приводится параметр [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) структуры, который предоставляется путем подключаемый модуль системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Среда интегрированной разработки о файле, после их получения из системы управления версиями. `display_string` Приводится параметр [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) структуры, который предоставляется путем подключаемый модуль системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Среда интегрированной разработки текущего состояния фоновой операции. `display_string` Приводится параметр [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) структуры, который предоставляется путем подключаемый модуль системы управления версиями.|  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Строка была отображаться или операция выполнена успешно.|  
|SCC_MSG_RTN_CANCEL|Пользователю отменить операцию.|  
  
## <a name="example"></a>Пример  
 Предположим, что вызовы IDE [SccGet](../extensibility/sccget-function.md) с двадцать имена файлов. Подключаемый модуль системы управления версиями хочет предотвратить отмену операции середине get файл. После получения каждого файла, он вызывает `lpTextOutProc`, передавая ему сведения о состоянии для каждого файла и отправляет `SCC_MSG_DOCANCEL` сообщение, если он имеет отчет о состоянии отсутствует. Если в любой момент плагин получает возвращаемое значение `SCC_MSG_RTN_CANCEL` в интегрированной среде разработки, он отменяет операции get немедленно, так, что другие файлы извлекаются.  
  
## <a name="structures"></a>Структуры  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_IS_CANCELLED` сообщения. Он используется для обмена данными идентификатор операции фона, который был отменен.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` сообщения. Он используется для связи, имя файла будет извлекаться и идентификатор, осуществляющей извлечение фоновой операции.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` сообщения. Он используется для обмена данными результат получения указанного файла, а также идентификатор фоновая операция, которую использовали для извлечения. См. в разделе возвращаемые значения для [SccGet](../extensibility/sccget-function.md) для что может быть задан в результате.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщения. Он используется для обмена данными текущее состояние в фоновом режиме. Состояние выражается в виде строки для отображения в интегрированной среде разработки и `bIsError` указывает на серьезность сообщения (`TRUE` для сообщения об ошибке; `FALSE` предупреждение или информационное сообщение). Присваивается идентификатор отправки состояние фоновой операции.  
  
## <a name="code-example"></a>Пример кода  
 Ниже приведен краткий пример вызова `LPTEXTOUTPROC` для отправки `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщение, в котором показано, как привести структуру для вызова.  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализованные интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)

