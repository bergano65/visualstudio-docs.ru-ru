---
title: IDebugCustomAttribute::GetAttributeBytes | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 574deb12fd774d989f2868dd1300c6a641849015
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562614"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugCustomAttribute::GetAttributeBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattribute-getattributebytes).  
  
Возвращает сведения об атрибутах как большой двоичный объект байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in, out] Массив, который заполняется байты атрибута.  
  
 `pdwLen`  
 [in, out] Указывает максимальное число байтов для возврата в `ppBlob` массива и возвращает количество байтов, фактически записанных в массив.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Задайте `ppBlob` параметр в значение null для возврата количества атрибутов доступных байтов. Затем выделить память для массива и передать этот массив в для `ppBlob` параметра.  
  
 Атрибут байты представляют необработанные данные настраиваемого атрибута.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

