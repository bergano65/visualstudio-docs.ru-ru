---
title: IDebugBinder3::GetAllAliases | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c2f4b15b04a21b61ed521507e35b6616e9e649b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183527"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 [in, out] Массив байтов с помощью псевдонима (если это значение null и `uRequest` равно 0, будет возвращаться количество псевдонимов, которые могут быть возвращены `puFetched`).  
  
 `puFetched`  
 [out] Возвращает количество получить псевдонимы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

