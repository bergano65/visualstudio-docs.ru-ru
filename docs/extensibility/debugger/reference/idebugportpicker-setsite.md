---
title: IDebugPortPicker::SetSite | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54286ded44f6acf44033c2fa5e2227ccaa688a64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123072"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Задает поставщик услуг.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSP`  
 [in] Ссылка на интерфейс поставщика службы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод будет вызываться перед вызовом других методов.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)