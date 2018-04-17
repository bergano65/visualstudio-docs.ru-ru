---
title: IDebugCustomAttribute::GetAttributeBytes | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 949bc7b8722e11be0a69800f890b509399169688
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Возвращает сведения об атрибутах, как большой двоичный объект байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppBlob`  
 [in, out] Массив, который содержит атрибут байт.  
  
 `pdwLen`  
 [in, out] Указывает максимальное число байтов для возврата в `ppBlob` массива и возвращает количество байтов, фактически записанных в массив.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Задать `ppBlob` параметр в значение null для возврата количества атрибутов доступных байтов. Затем выделить память для массива и передать этот массив в для `ppBlob` параметра.  
  
 Байты атрибута представляют необработанные данные настраиваемого атрибута.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)