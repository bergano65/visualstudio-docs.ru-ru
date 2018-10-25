---
title: IDebugCoreServer3::GetServerFriendlyName | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bfc596bd1b77c77ea5b54a66ca349a66e50915c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875792"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Возвращает понятное имя для сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrName`  
 [out] Возвращает понятное имя для сервера.  
  
> [!NOTE]
>  Вызывающий объект несет ответственность за освобождение строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Для серверов запущен пользователем имя, возвращаемый этим методом является полное имя сервера. Для автоматического запуска серверов называется машины сервер работает.  
  
 Для компьютера ориентированное имя, вызовите [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)