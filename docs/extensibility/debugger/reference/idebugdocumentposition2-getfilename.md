---
title: IDebugDocumentPosition2::GetFileName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 407ddfe794d1b23e65baf1530182b9c3ec568b98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967415"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Получает имя файла исходного файла, содержащий положение документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```csharp  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrFileName`  
 [out] Возвращает имя файла исходного файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Исходный файл не всегда возможно (исходный файл может не существует на диске, к примеру) имя файла.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)