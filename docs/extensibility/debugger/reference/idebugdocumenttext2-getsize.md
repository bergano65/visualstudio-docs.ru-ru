---
title: IDebugDocumentText2::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee62052911ab724fd220c7a808022c5f35b49f74
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859923"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Получает размер текста в этой позиции в документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcNumLines`  
 [out] Возвращает количество строк текста.  
  
 `pcNumChars`  
 [out] Возвращает количество символов текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [C++] Если определенное значение не требуется, передайте значение NULL для параметра.  
  
 [C# только] Необходимо указать оба параметра.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)