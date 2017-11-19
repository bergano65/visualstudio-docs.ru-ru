---
title: "IDebugTypeFieldBuilder::CreatePointerToType | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 712450c06ead20e4516a13861160166a2e1f14a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Создает указатель в указанный тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```csharp  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pTypeField`  
 [in] Тип для указания. Он представлен [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейса.  
  
 `pPtrToTypeField`  
 [out] Возвращает указателя, представленного новый **IDebugField** объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)