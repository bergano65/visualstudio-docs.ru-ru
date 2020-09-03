---
title: 'IDebugDocumentContext2:: Compare | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f09684c5e9587c6e3bb631674e009d0b36f4fc5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189417"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Сравнивает данный контекст документа с заданным массивом контекстов документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `compare`  
 окне Значение из перечисления [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) , указывающее тип сравнения.  
  
 `rgpDocContextSet`  
 окне Массив объектов [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , которые представляют контексты документа, сравниваемые с.  
  
 `dwDocContextSetLen`  
 окне Длина массива контекстов документа для сравнения.  
  
 `pdwDocContext`  
 заполняет Возвращает индекс в `rgpDocContextSet` массив первого контекста документа, удовлетворяющего условию сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` , если найдено совпадение. Возвращает значение `S_FALSE` , если совпадение не найдено. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Объекты [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , переданные в массиве, должны быть реализованы с помощью того же модуля отладки, который реализует `IDebugDocumentContext2` вызываемый объект; в противном случае сравнение недопустимо.  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
