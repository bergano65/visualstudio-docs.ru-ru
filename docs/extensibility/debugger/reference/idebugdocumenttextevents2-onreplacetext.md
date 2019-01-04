---
title: IDebugDocumentTextEvents2::onReplaceText | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2::OnReplaceText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onReplaceText
ms.assetid: cb39f025-66d8-4dc0-bef6-1bdc8e07db92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c985949952904c5f8b99bc0969fa612e547ffcd3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848629"
---
# <a name="idebugdocumenttextevents2onreplacetext"></a>IDebugDocumentTextEvents2::onReplaceText
Уведомляет отладочный пакет о том, что текст был заменен в документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT onReplaceText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToReplace  
);  
```  
  
```csharp  
int onReplaceText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToReplace  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pos`  
 [in] Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) указывает, где текст был заменен.  
  
 `dwNumToReplace`  
 [in] Указывает количество символов текста, которые были заменены.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)