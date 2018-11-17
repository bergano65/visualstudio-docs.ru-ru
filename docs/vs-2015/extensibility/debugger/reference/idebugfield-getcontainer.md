---
title: IDebugField::GetContainer | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c28347c3f77b421650706e51b2210c90c3dc8ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737809"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает контейнер поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppContainerField`  
 [out] Возвращает контейнер, представленные как [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если это поле не имеет контейнер, возвращенный `ppContainerField` будет иметь значение null.  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

