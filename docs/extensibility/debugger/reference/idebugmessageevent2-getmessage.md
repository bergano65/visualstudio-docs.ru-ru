---
title: IDebugMessageEvent2::GetMessage | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74a89fafd8d163bfb03be8d29f58eb036be68f82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838573"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Получает сообщение для отображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMessageType`  
 [out] Возвращает значение из [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) перечисление, описывающее тип сообщения.  
  
 `pbstrMessage`  
 [out] Возвращает сообщение.  
  
 `pdwType`  
 [out] Возвращает тип сообщения, используя правила Win32 `MessageBox` функции. См. в разделе [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) функция сведения.  
  
 `pbstrHelpFileName`  
 [in, out] Возвращает имя файла справки. Может быть значение null (C++) или пустое значение (C#), если нет файла справки.  
  
 `pdwHelpId`  
 [in, out] Возвращает идентификатор справки. Может быть 0, если нет справки, на которое имеется связанное с этим сообщением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)