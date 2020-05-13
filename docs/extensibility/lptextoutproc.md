---
title: LPTEXTOUTPROC Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702794"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Когда пользователь выполняет операцию управления исходным кодом изнутри интегрированной среды разработки (IDE), плагин управления исходным кодом может захотеть передать сообщения об ошибках или статусе, связанные с операцией. Плагин может отображать свои собственные ящики сообщений для этой цели. Однако для более бесшовной интеграции плагин может передавать строки в IDE, который затем отображает их в своем родном способе отображения информации о статусе. Механизмом для этого `LPTEXTOUTPROC` является указатель функции. IDE реализует эту функцию (описанную более подробно ниже) для отображения ошибок и статуса.

IDE передается к плагину управления исходным кодом в `lpTextOutProc` указатель функции к этой функции, как параметр, при вызове [SccOpenProject.](../extensibility/sccopenproject-function.md) Во время операции SCC, например, в середине вызова [SccGet](../extensibility/sccget-function.md) с участием многих `LPTEXTOUTPROC` файлов, плагин может вызвать функцию, периодически проходя строки для отображения. IDE может отображать эти строки на строке состояния, в окне вывода или в отдельном окне сообщения, если это необходимо. В качестве опционов IDE может отображать определенные сообщения с помощью кнопки **«Отмена».** Это позволяет пользователю отменить операцию, и это дает IDE возможность передавать эту информацию обратно в плагин.

## <a name="signature"></a>Сигнатура
 Функция вывода IDE имеет следующую подпись:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Параметры

display_string

Текстовая строка для отображения. Эта строка не должна быть прекращена с возвратом перевозки или линейной подачей.

mesg_type

Тип сообщения. В следующей таблице перечислены поддерживаемые значения для этого параметра.

|Значение|Описание|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Сообщение считается информацией, предупреждением или ошибкой.|
|`SCC_MSG_STATUS`|Сообщение отображает состояние и может отображаться в панели статуса.|
|`SCC_MSG_DOCANCEL`|Отправлено без строки сообщения.|
|`SCC_MSG_STARTCANCEL`|Начинаетотра отображение кнопки **Отмена.**|
|`SCC_MSG_STOPCANCEL`|Прекращает отображение кнопки **«Отмена».**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Спрашивает IDE, если фоновая операция должна `SCC_MSG_RTN_CANCEL` быть отменена: IDE возвращается, если операция была отменена; в противном случае, возвращается `SCC_MSG_RTN_OK`. Параметр `display_string` отливается в виде структуры [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) которая поставляется подключаемым плагином управления исходным управлением.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Сообщает IDE о файле до его извлечения из управления версиями. Параметр `display_string` отлит в виде структуры [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) которая поставляется подключаемым плагином управления исходным управлением.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Сообщает IDE о файле после его извлечения из управления версиями. Параметр `display_string` отлит в виде структуры [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) которая поставляется подключаемым плагином управления исходным управлением.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Сообщает IDE о текущем состоянии фоновой операции. Параметр `display_string` отлит в виде структуры [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) которая поставляется подключаемым плагином управления исходным управлением.|

## <a name="return-value"></a>Возвращаемое значение

|Значение|Описание|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Строка была отображана или операция была успешно завершена.|
|SCC_MSG_RTN_CANCEL|Пользователь хочет отменить операцию.|

## <a name="example"></a>Пример
 Предположим, что IDE вызывает [SccGet](../extensibility/sccget-function.md) с двадцатью именами файлов. Плагин управления исходным элементом хочет предотвратить отмену операции в середине файла. После получения каждого файла, он вызывает, `lpTextOutProc`передавая ему информацию о состоянии на каждом файле, и отправляет `SCC_MSG_DOCANCEL` сообщение, если он не имеет статуса, чтобы сообщить. Если в любое время плагин получает `SCC_MSG_RTN_CANCEL` возвратное значение от IDE, он немедленно отменяет операцию get, так что больше не будет извлечено файлов.

## <a name="structures"></a>Структуры

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Эта структура отправляется `SCC_MSG_BACKGROUND_IS_CANCELLED` с сообщением. Используется для передачи идентификатора отменяемой фоновой операции.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Эта структура отправляется `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` с сообщением. Он используется для передачи имени файла, который должен быть извлечен, и идентификатора фоновой операции, выполняющей извлечение.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Эта структура отправляется `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` с сообщением. Он используется для передачи результата извлечения указанного файла, а также идентификатора фоновой операции, которая сделала извлечение. Ознакомьтесь со значениями возврата [для SccGet,](../extensibility/sccget-function.md) что может быть дано в результате.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Эта структура отправляется `SCC_MSG_BACKGROUND_ON_MESSAGE` с сообщением. Он используется для передачи текущего состояния фоновой операции. Статус выражается как строка, отображаемый IDE, `bIsError` и`TRUE` указывает на серьезность сообщения (для сообщения об ошибке; `FALSE` для предупреждения или для информационного сообщения). Также дается идентификатор фоновой операции отправки статуса.

## <a name="code-example"></a>Пример кода
 Вот краткий пример `LPTEXTOUTPROC` вызова для `SCC_MSG_BACKGROUND_ON_MESSAGE` отправки сообщения, показывающего, как бросить структуру для вызова.

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
- [Функции обратного вызова, реализованные IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
