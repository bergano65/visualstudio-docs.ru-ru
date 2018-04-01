---
title: IDebugPortSupplierDescription2::GetDescription | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2::GetDescription
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5e568954bbc2c3091d104f3a91c9c193efd877b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplierdescription2getdescription"></a>IDebugPortSupplierDescription2::GetDescription
Извлекает описание и описание метаданных для поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDescription(  
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,  
   BSTR *pbstrText  
);  
```  
  
```csharp  
public int GetDescription(  
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,  
   out string pbstrText  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwFlags`  
 [out] Флаги метаданные для описания.  
  
 `pbstrText`  
 [out] Описание поставщика порта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)