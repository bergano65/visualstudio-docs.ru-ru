---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1b79326d7b0ac59ffb00fd5bb8883c635284586
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923346"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает массив указанного типа и размера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```csharp  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pTypeField`  
 [in] Тип элементов, которые будет содержать массив.  
  
 `rank`  
 [in] Число элементов в массиве.  
  
 `pArrayOfTypeField`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекты, представляющие новый массив.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)

