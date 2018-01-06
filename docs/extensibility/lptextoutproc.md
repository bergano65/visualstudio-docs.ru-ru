---
title: "LPTEXTOUTPROC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9fb212d7908d32bc9d9d14d7e8f4786089bc5f89
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Когда пользователь выполняет операцию системы управления версиями из внутри интегрированной среды разработки (IDE), подключаемый модуль системы управления версиями может потребоваться передачи ошибка или состояние сообщения, относящиеся к работе. Подключаемый модуль может отображать свой собственный окон сообщений, для этой цели. Однако для более прозрачную интеграцию, подключаемый модуль можно передать строки в интегрированную среду разработки, которая затем отображает их в его собственном способ отображения сведений о состоянии. — Это механизм `LPTEXTOUTPROC` указатель функции. IDE реализует эту функцию, (более подробно ниже) для отображения ошибок и состояний.  
  
 IDE передает в систему управления версиями подключаемого модуля указатель на функцию в эту функцию как `lpTextOutProc` параметра при вызове [SccOpenProject](../extensibility/sccopenproject-function.md). Во время операции SCC, например, во время вызова [SccGet](../extensibility/sccget-function.md) включающих много файлов, подключаемый модуль может вызывать `LPTEXTOUTPROC` функции, периодически передачи строк для отображения. Интегрированной среды разработки может отображать эти строки в строку состояния в окне вывода или в отдельном окне сообщений, в зависимости. При необходимости интегрированной среды разработки может сможет отображать некоторые сообщения с **отменить** кнопки. Это дает пользователю возможность отменить операцию, и он дает возможность передавать эти сведения подключаемый модуль интегрированной среды разработки.  
  
## <a name="signature"></a>Подпись  
 IDE выходных данных объекта функция имеет следующую сигнатуру:  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Параметры  
 display_string  
 Текстовая строка для отображения. Эта строка не должно заканчиваться каретки возврата и перевода строки.  
  
 mesg_type  
 Тип сообщения. В следующей таблице перечислены поддерживаемые значения для этого параметра.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Сообщение считается сведения, предупреждение или ошибка.|  
|`SCC_MSG_STATUS`|Сообщение отображается состояние и могут отображаться в строке состояния.|  
|`SCC_MSG_DOCANCEL`|Отправляет строку без сообщений.|  
|`SCC_MSG_STARTCANCEL`|Начинается отображение **отменить** кнопки.|  
|`SCC_MSG_STOPCANCEL`|Останавливает отображение **отменить** кнопки.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Запрашивает IDE при фоновой операции будут отменены: возвращает IDE `SCC_MSG_RTN_CANCEL` Если операция была отменена; в противном случае возвращает `SCC_MSG_RTN_OK`. `display_string` Параметр приводится к [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) структуру, которая поставляется с подключаемым модулем системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Среда интегрированной разработки о файле до их извлечения из системы управления версиями. `display_string` Параметр приводится к [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) структуру, которая поставляется с подключаемым модулем системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|После извлечения из системы управления версиями, среда интегрированной разработки о файле. `display_string` Параметр приводится к [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) структуру, которая поставляется с подключаемым модулем системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Среда интегрированной разработки текущего состояния фоновой операции. `display_string` Параметр приводится к [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) структуру, которая поставляется с подключаемым модулем системы управления версиями.|  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Отображается строка или операция выполнена успешно.|  
|SCC_MSG_RTN_CANCEL|Пользователю необходимо отменить операцию.|  
  
## <a name="example"></a>Пример  
 Предположим, что вызовы IDE [SccGet](../extensibility/sccget-function.md) с двадцать имена файлов. Подключаемый модуль системы управления версиями хочет предотвратить отмену операции середине get файла. После получения каждого файла, он вызывает `lpTextOutProc`, передавая сведения о состоянии для каждого файла и отправляет `SCC_MSG_DOCANCEL` сообщение, если он не имеет статуса отчет. Если в любой момент подключаемый модуль получает возвращаемое значение `SCC_MSG_RTN_CANCEL` интегрированной среде разработки, он отменяет операцию получения немедленно, чтобы получить дополнительные файлы не будут.  
  
## <a name="structures"></a>Структуры  
  
###  <a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_IS_CANCELLED` сообщения. Он используется для связи ID фоновых операций, который был отменен.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` сообщения. Он используется для связи, имя файла будет извлекаться и идентификатор фоновых операций, который выполняет извлечение.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` сообщения. Он используется для обмена данными результат извлечения указанного файла, а также идентификатор фоновых операций, который выполнял извлечение. Увидеть возвращаемые значения для [SccGet](../extensibility/sccget-function.md) для учитывая то, что в результате.  
  
###  <a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщения. Он используется для передачи текущего состояния фоновой операции. Состояние выражается как строка, отображаемая в интегрированной среде разработки и `bIsError` указывает серьезность сообщения (`TRUE` для сообщения об ошибке; `FALSE` предупреждение или информационное сообщение). Кроме того, предоставляется идентификатор фоновая операция отправки состояния.  
  
## <a name="code-example"></a>Пример кода  
 Ниже приведен краткий пример вызова `LPTEXTOUTPROC` для отправки `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщения, показывающий, как выполнить приведение структуру для вызова.  
  
```cpp  
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
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)