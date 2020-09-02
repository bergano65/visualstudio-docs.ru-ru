---
title: 'Идебугпропертифиелд:: Жетпропертисеттер | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8484aa4041e00b9decce73dc9e19e22aa106e9df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164858"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает метод, который задает свойство.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```csharp  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 заполняет Возвращает объект [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md) , представляющий метод, который задает свойство.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Чтобы получить метод, который получает свойство, вызовите метод [жетпропертижеттер](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) .  
  
## <a name="see-also"></a>См. также:  
 [идебугпропертифиелд](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
