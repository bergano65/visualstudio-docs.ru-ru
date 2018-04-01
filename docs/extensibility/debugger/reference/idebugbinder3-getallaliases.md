---
title: IDebugBinder3::GetAllAliases | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 57f644cb0f5cb550e093ccc2691fed91e9f5f4b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Этот метод извлекает список псевдонимов из программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uRequest`  
 [in] Максимальное количество псевдонимов для возврата (указывает длину массива, передаваемого в `ppAliases`).  
  
 `ppAliases`  
 [in, out] Массив, в который наполнить псевдонимы (если это значение null и `uRequest` равно 0, будут возвращаться количество псевдонимов, которые могут быть возвращены `puFetched`).  
  
 `puFetched`  
 [out] Возвращает количество получить псевдонимы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)