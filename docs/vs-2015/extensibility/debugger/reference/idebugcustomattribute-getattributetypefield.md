---
title: 'Идебугкустоматтрибуте:: Жетаттрибутетипефиелд | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a56a148342eb659a4f57d68581159f64ee3b1226
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568934"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает тип класса настраиваемого атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppCAType`  
 заполняет Возвращает объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий класс, для которого настраиваемый атрибут является экземпляром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Настраиваемый атрибут всегда является классом. Этот метод предоставляет доступ к объекту [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , который описывает этот класс.  
  
## <a name="see-also"></a>См. также:  
 [идебугкустоматтрибуте](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
