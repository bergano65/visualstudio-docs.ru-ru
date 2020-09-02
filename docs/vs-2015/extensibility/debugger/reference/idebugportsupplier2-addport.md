---
title: 'IDebugPortSupplier2:: Аддпорт | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf5bf281e794bde04ae0c2e86c6d27edb7edc5a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188296"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Добавляет порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRequest`  
 окне Объект [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , описывающий добавляемый порт.  
  
 `ppPort`  
 заполняет Возвращает объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод фактически создает запрошенный порт, а также добавляет его в внутренний список активных портов поставщика порта. Сначала можно вызвать метод [канаддпорт](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) , чтобы избежать возможных длительных задержек.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
