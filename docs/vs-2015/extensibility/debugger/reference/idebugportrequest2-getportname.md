---
title: 'IDebugPortRequest2:: Жетпортнаме | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188363"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 заполняет Возвращает имя порта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Интерфейс [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) обычно передается из пакета отладки (клиента) поставщику порта (серверу) для получения подключения к порту. Как пакет отладки, так и поставщик порта знают о возможных вариантах для порта. Если в простой строке можно описать порт, то у `IDebugPortRequest2::GetPortName` метода будет достаточно сведений для установления соединения. В противном случае клиенту могут предоставляться дополнительные интерфейсы, которые могут быть получены сервером с помощью `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
