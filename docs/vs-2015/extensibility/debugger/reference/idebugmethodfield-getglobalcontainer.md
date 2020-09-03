---
title: 'Идебугмесодфиелд:: Жетглобалконтаинер | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63912b75435de503dec677b715d1914b419ba07a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162562"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает глобальный контейнер метода.  
  
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
 заполняет Возвращает [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий модуль, в котором определен этот метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Возвращаемый объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) представляет весь модуль и является искусственным объектом, то есть сам модуль не имеет фактического класса, но может быть представлен `IDebugClassField` объектом, что позволяет перечислять и обнаруживать различные элементы модуля.  
  
## <a name="see-also"></a>См. также:  
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
