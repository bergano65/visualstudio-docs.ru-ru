---
title: IDebugReference2::GetDerivedMostReference | Документация Майкрософт
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
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b680571bc2edc54e89b1625b012e5a34885ffe9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568656"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugReference2::GetDerivedMostReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-getderivedmostreference).  
  
Получает ссылку на производный ссылку. Зарезервировано для будущего использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDerivedMost`  
 [out] Возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий свойство производного.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
 Например, если это свойство описывает объект, реализующий `ClassRoot` , но это фактически является экземпляром `ClassDerived` , производный от `ClassRoot`, этот метод возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта Представляет ссылку на `ClassDerived` объекта.  
  
## <a name="see-also"></a>См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

