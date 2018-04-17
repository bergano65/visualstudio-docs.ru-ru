---
title: IDebugDocument2::GetDocumentClassID | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79a80d5a37c341a46d32e9bedac8f7ff416158da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Получает идентификатор класса документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pclsid`  
 [out] Возвращает идентификатор GUID, который является Идентификатором класса документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Класс GUID можно использовать для создания отдельных классов, каждый из которых представляет документ.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)