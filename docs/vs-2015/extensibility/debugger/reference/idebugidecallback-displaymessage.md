---
title: IDebugIDECallback::DisplayMessage | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f36cc481a7b92b89705b0db25098c0ba0042ea50
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558948"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugIDECallback::DisplayMessage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugidecallback-displaymessage).  
  
Отправляет заданной строкой сообщения в окне вывода отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `szMessage`  
 [in] Строка сообщения для отображения в окне вывода отладчика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)

