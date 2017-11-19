---
title: "IDebugMessageEvent2::GetMessage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 511826e54e4331084c3cbd5c34814b73d0e80078
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Возвращает сообщение для отображения.  
  
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
 [out] Возвращает тип сообщения, используя соглашения о Win32 `MessageBox` функции. В разделе [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) функция подробные сведения.  
  
 `pbstrHelpFileName`  
 [in, out] Возвращает имя файла справки. Может быть значение null (C++) или пустое значение (C#), если отсутствует файл справки.  
  
 `pdwHelpId`  
 [in, out] Возвращает идентификатор справки. Может быть 0, если нет справки, на которое имеется связанное с этим сообщением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)