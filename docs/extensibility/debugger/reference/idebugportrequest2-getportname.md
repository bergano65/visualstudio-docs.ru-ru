---
title: "IDebugPortRequest2::GetPortName | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2::GetPortName
helpviewer_keywords: IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab94c9bcb0ec686b9b2d8aba7378bbd55ca71c72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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