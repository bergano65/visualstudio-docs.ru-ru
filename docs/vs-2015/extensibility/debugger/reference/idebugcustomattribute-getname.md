---
title: IDebugCustomAttribute::GetName | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4463fc4f9d321b26487e885255843a7acd945f76
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62569274"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает имя настраиваемого атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 [out] Возвращает строку, содержащую имя настраиваемого атрибута.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Именованный возвращаемого этим методом соответствует имени класса, используемого для объявления атрибута. Это может не совсем соответствовать имя самого класса настраиваемого атрибута как C# позволяет суффикс «Attribute» будет удален из имени настраиваемого атрибута, при использовании в объявлении.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
