---
title: 'Идебугкустоматтрибуте:: Name | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569274"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя настраиваемого атрибута.  
  
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
 заполняет Возвращает строку, содержащую имя пользовательского атрибута.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Имя, возвращаемое этим методом, соответствует имени класса, используемого для объявления атрибута. Это может не совпадать с именем самого класса настраиваемого атрибута, так как C# позволяет удалять суффикс "Attribute" из имени настраиваемого атрибута при его использовании в объявлении.  
  
## <a name="see-also"></a>См. также:  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
