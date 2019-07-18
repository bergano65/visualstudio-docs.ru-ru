---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc2075ccc37d280640f7559b1454990ee6684f25
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62555752"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод извлекает список псевдонимов из программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uRequest`  
 [in] Максимальное количество псевдонимов для возврата (указывает длину массива, передаваемого в `ppAliases`).  
  
 `ppAliases`  
 [in, out] Массив байтов с помощью псевдонима (если это значение null и `uRequest` равно 0, будет возвращаться количество псевдонимов, которые могут быть возвращены `puFetched`).  
  
 `puFetched`  
 [out] Возвращает количество получить псевдонимы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
