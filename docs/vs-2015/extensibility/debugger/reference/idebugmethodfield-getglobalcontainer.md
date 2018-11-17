---
title: IDebugMethodField::GetGlobalContainer | Документация Майкрософт
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
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb64dd5e3e45eb20f98d7c0e27a96114422b98e1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791661"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает контейнер глобального метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppClass`  
 [out] Возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) представляющий модуль, в котором определен этот метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Возвращенный [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект представляет весь модуль и является объектом искусственного, то есть сам модуль не имеют фактический класс, но она может быть представлена `IDebugClassField` объектам, различных элементы модуля перечисления и обнаружения.  
  
## <a name="see-also"></a>См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

