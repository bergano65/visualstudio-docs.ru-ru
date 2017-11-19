---
title: "IDebugErrorEvent2::GetErrorMessage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords: IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b8a4e4c2ca938d8c600d3fd9ef0e615aa847fd9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Возвращает информацию, позволяющую построении сообщения восприятия ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMessageType`  
 [out] Возвращает значение из [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) перечисление, описывающее тип сообщения.  
  
 `pbstrErrorFormat`  
 [out] Формат окончательное сообщение для пользователя (Дополнительные сведения в подразделе «Примечания»).  
  
 `hrErrorReason`  
 [out] Связана с кодом ошибки сообщения.  
  
 `pdwType`  
 [out] Серьезность ошибки (используйте константы MB_XXX для `MessageBox`, например `MB_EXCLAMATION` или `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Путь к файлу справки (set со значением null, если отсутствует файл справки).  
  
 `pdwHelpId`  
 [out] Идентификатор раздела справки для отображения (значение 0, если ни один раздел справки).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сообщение об ошибке должно форматироваться в соответствии с `"What I was doing.  %1"`. `"%1"` Будет заменен вызывающему объекту с сообщением об ошибке, производные от кода ошибки (который возвращается в `hrErrorReason`). `pMessageType` Указывает код, вызывающий способ отображения ошибок сообщения.  
  
## <a name="see-also"></a>См. также  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)