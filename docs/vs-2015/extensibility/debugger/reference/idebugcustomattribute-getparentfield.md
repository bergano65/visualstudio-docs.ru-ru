---
title: 'Идебугкустоматтрибуте:: Жетпарентфиелд | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b6d6ceadc8ee0dc6099d6463a75f1c792837e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569580"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает поле, к которому присоединен настраиваемый атрибут.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 заполняет Возвращает объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий поле, к которому присоединен настраиваемый атрибут.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Вызовите метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) для возвращенного объекта [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , чтобы определить, какой тип поля является родительским.  
  
## <a name="see-also"></a>См. также:  
 [идебугкустоматтрибуте](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
