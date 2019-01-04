---
title: IDebugDocument2::GetDocumentClassID | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 69c9b5d351f3989bf7a9855274634ededa52f08a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825728"
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
 [out] Возвращает идентификатор GUID, представляющий собой идентификатор класса документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 GUID класса можно использовать для создания отдельных классов, каждый из которых представляет документ.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)