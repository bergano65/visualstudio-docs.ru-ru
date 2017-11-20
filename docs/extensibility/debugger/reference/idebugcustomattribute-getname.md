---
title: "IDebugCustomAttribute::GetName | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetName
helpviewer_keywords: IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 165362ab03685a3acca457e4095778b9dcb182e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Возвращает имя настраиваемого атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 [out] Возвращает строку, содержащую имя настраиваемого атрибута.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Именованный, возвращаемый этим методом соответствует имени класса, используемого для объявления атрибута. Это может не совсем соответствуют имя самого класса настраиваемого атрибута как C# позволяет суффикс «Attribute» для удаления из имени настраиваемого атрибута при использовании в объявлении.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)