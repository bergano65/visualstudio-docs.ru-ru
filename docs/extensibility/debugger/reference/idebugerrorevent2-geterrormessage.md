---
title: IDebugErrorEvent2::GetErrorMessage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55c36c6649b8ff2b1b0bebc57012970625a964b8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199945"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Возвращает информацию, позволяющую конструкции понятное сообщение.

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
[out] Возвращает значение из [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) перечисление, описывающее тип сообщения.

`pbstrErrorFormat`\
[out] Формат окончательное сообщение для пользователя (см. в разделе «Примечания» Дополнительные сведения).

`hrErrorReason`\
[out] Код ошибки сообщения посвящен.

`pdwType`\
[out] Серьезность ошибки (использовать константы MB_XXX для `MessageBox`, например `MB_EXCLAMATION` или `MB_WARNING`).

`pbstrHelpFileName`\
[out] Путь к файлу справки (указано значение null, если отсутствует файл справки).

`pdwHelpId`\
[out] Идентификатор раздела справки для отображения (значение 0, если ни одного раздела).

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Сообщение об ошибке должно форматироваться вроде `"What I was doing.  %1"`. `"%1"` Бы заменить вызывающим с сообщением об ошибке, производным от кода ошибки (которое возвращается в `hrErrorReason`). `pMessageType` Указывает вызывающий объект как окончательный должно появиться сообщение об ошибке.

## <a name="see-also"></a>См. также
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)