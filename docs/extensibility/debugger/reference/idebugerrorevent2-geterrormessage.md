---
title: IDebugErrorEvent2::GetErrorMessage Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730040"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Возвращает информацию, позволяющую построить сообщение об ошибке, читаемое человеком.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Параметры
`pMessageType`\
(ваут) Возвращает значение из перечисления [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) описывающего тип сообщения.

`pbstrErrorFormat`\
(ваут) Формат окончательного сообщения пользователю (подробнее см. "Замечания").

`hrErrorReason`\
(ваут) Код ошибки, о чем идет речь.

`pdwType`\
(ваут) Тяжесть ошибки (использовать MB_XXX константы для `MessageBox`; например, `MB_EXCLAMATION` или `MB_WARNING`).

`pbstrHelpFileName`\
(ваут) Путь к файлу справки (установленное на нулевую величину, если нет файла справки).

`pdwHelpId`\
(ваут) Идентификатор темы справки для отображения (установлен на 0, если нет темы справки).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Сообщение об ошибке должно быть `"What I was doing.  %1"`отформатировано по аналогии с . Затем `"%1"` он будет заменен абонентом сообщением об ошибке, полученным из `hrErrorReason`кода ошибки (который возвращается в). Параметр `pMessageType` сообщает вызывающему, как должно отображаться окончательное сообщение об ошибке.

## <a name="see-also"></a>См. также
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [ТИП СООБЩЕНИЯ](../../../extensibility/debugger/reference/messagetype.md)
