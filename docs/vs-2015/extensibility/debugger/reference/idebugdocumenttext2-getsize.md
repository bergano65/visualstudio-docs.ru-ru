---
title: IDebugDocumentText2::GetSize | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6d438db999e2e0b2aa85c45c0b38333238755e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "58994666"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает размер текста в этой позиции в документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
