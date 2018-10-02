---
title: IDebugField::Equal | Документация Майкрософт
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
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3218b8cc61dea3d55132f5596f624108cd4d85bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558762"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugField::Equal](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfield-equal).  
  
Этот метод сравнивает это поле с указанным полем на предмет равенства.  
  
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
 [in] Поле для сравнения с этим параметром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если поля не изменилось, возвращает `S_OK`. Если поля не совпадают, возвращает `S_FALSE.` в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

