---
title: 'Идебугфиелд:: Equals | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547316"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод сравнивает это поле с указанным полем для проверки на равенство.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pField`  
 окне Поле для сравнения с данным полем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если поля совпадают, возвращает `S_OK` . Если поля отличаются, `S_FALSE.` в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
