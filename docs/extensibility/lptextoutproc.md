---
title: "LPTEXTOUTPROC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7229d2681912663ad2cddcf95e140197495c0934
ms.lasthandoff: 02/22/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
При выполнении операции управления версиями из среды разработки (IDE), подключаемый модуль системы управления версиями может потребоваться передать ошибка или состояние сообщения, относящиеся к операции. Подключаемый модуль можно отобразить собственную окон сообщений, для этой цели. Однако более плавной интеграции подключаемого модуля можно передать строки в интегрированную среду разработки, которая затем отображает их в его собственный способ отображения информации о состоянии. — Это механизм `LPTEXTOUTPROC` указатель функции. Эта функция, (более подробно ниже) для отображения об ошибках и состоянии реализована в Интегрированной среде разработки.  
  
 IDE передает в системы управления версиями подключаемого модуля указатель на функцию в эту функцию как `lpTextOutProc` параметра при вызове [SccOpenProject](../extensibility/sccopenproject-function.md). Во время операции SCC, например, во время вызова [SccGet](../extensibility/sccget-function.md) с участием большого числа файлов, подключаемый модуль может вызвать `LPTEXTOUTPROC` функции, периодически передачи строк для отображения. IDE может отображать эти строки в строке состояния в окне вывода или в отдельном окне сообщений, соответствующим образом. При необходимости IDE можно для отображения определенных сообщений с **отменить** кнопки. Это дает пользователю возможность отменить операцию и дает возможность передавать эту информацию обратно в подключаемый модуль интегрированной среды разработки.  
  
## <a name="signature"></a>Подпись  
 Выходной IDE функция имеет следующую подпись:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Параметры  
 display_string  
 Текстовая строка для отображения. Эта строка не должно заканчиваться каретки возврата или перевода строки.  
  
 mesg_type  
 Тип сообщения. В следующей таблице перечислены поддерживаемые значения для этого параметра.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Сообщение считается сведения, предупреждение или ошибка.|  
|`SCC_MSG_STATUS`|Сообщение отображается состояние и может отображаться в строке состояния.|  
|`SCC_MSG_DOCANCEL`|Строка не сообщений, отправленных.|  
|`SCC_MSG_STARTCANCEL`|Начинается отображение **отменить** кнопки.|  
|`SCC_MSG_STOPCANCEL`|Останавливает отображение **отменить** кнопки.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Запрашивает IDE при фоновой операции для отмены: возвращает IDE `SCC_MSG_RTN_CANCEL` Если операция была отменена; в противном случае — возвращает `SCC_MSG_RTN_OK`. `display_string` Параметр приводится к [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) структура, которая поставляется с подключаемым модулем системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Среда интегрированной разработки о файле до их извлечения из системы управления версиями. `display_string` Параметр приводится к [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) структура, которая поставляется с подключаемым модулем системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Среда интегрированной разработки о файле после его получения из системы управления версиями. `display_string` Параметр приводится к [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) структура, которая поставляется с подключаемым модулем системы управления версиями.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Среда интегрированной разработки текущего состояния фоновой операции. `display_string` Параметр приводится к [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) структура, которая поставляется с подключаемым модулем системы управления версиями.|  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Отображается строка или операция выполнена успешно.|  
|SCC_MSG_RTN_CANCEL|Этому пользователю отменить операцию.|  
  
## <a name="example"></a>Пример  
 Предположим, что вызовы IDE [SccGet](../extensibility/sccget-function.md) с двадцати имена файлов. Подключаемый модуль системы управления версиями хочет предотвратить отмену операции середине get файла. После получения каждого файла, он вызывает `lpTextOutProc`, передавая сведения о состоянии для каждого файла и отправляет `SCC_MSG_DOCANCEL` сообщение, если она не имеет статуса в отчет. Если в любой момент плагин получает возвращаемое значение `SCC_MSG_RTN_CANCEL` в интегрированной среде разработки он отменяет операции получения немедленно, чтобы получить дополнительные файлы не будут.  
  
## <a name="structures"></a>Структуры  
  
###  <a name="a-namelinksccmsgdataiscancelleda-sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_IS_CANCELLED` сообщение. Он используется для связи ID фоновых операций, который был отменен.  
  
###  <a name="a-namelinksccmsgdataonbeforegetfilea-sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` сообщение. Он используется для связи имя файла будет извлекаться и идентификатор фоновых операций, выполняемых для извлечения.  
  
###  <a name="a-namelinksccmsgdataonaftergetfilea-sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` сообщение. Он используется для связи результат извлечения указанного файла, а также идентификатор фоновых операций, который выполнял извлечение. В разделе значения возврата для [SccGet](../extensibility/sccget-function.md) для учитывая то, что в результате.  
  
###  <a name="a-namelinksccmsgdataonmessagea-sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Эта структура передается со `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщение. Он используется для передачи текущего состояния фоновой операции. Состояние выражается как строка, отображаемая в интегрированной среде разработки и `bIsError` указывает серьезность сообщения (`TRUE` для сообщения об ошибке; `FALSE` предупреждение или информационное сообщение). Присваивается идентификатор фоновых операций отправки информации о состоянии.  
  
## <a name="code-example"></a>Пример кода  
 Ниже приведен краткий пример вызова `LPTEXTOUTPROC` для отправки `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщений, демонстрирующий приведение структуры для вызова.  
  
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
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)
