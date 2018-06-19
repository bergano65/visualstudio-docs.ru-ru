---
title: IDebugPortRequest2::GetPortName | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c81bdc6586766cb4a241bf29e653cb1b10f66f2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114337"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Возвращает имя порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrPortName`  
 [out] Возвращает имя порта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) обычно передается интерфейс из пакета отладки (клиент) для поставщика порта (сервер) для подключения к порту. Отладочный пакет и поставщика порта известно возможные варианты для порта. Если простая строка можно описать порт, то `IDebugPortRequest2::GetPortName` метод имеет достаточно информации для подключения. В противном случае можно указать дополнительные интерфейсы для клиента, который можно получить с помощью сервера `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)