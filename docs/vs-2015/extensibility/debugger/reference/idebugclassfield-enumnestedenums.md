---
title: 'Идебугклассфиелд:: Енумнестеденумс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84f60b9b0c882883c930657df59530f1c5107a22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191063"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для вложенных перечислителей этого класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список вложенных перечислений. Возвращает значение null, если нет вложенных перечислений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет вложенных перечислителей. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Каждый элемент перечисления является объектом [идебуженумфиелд](../../../extensibility/debugger/reference/idebugenumfield.md) , описывающим вложенное перечисление.  
  
 Перечисление, объявленное внутри класса, считается вложенным перечислением. Например, если учитывать, что:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums`Метод возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , содержащий один объект [идебуженумфиелд](../../../extensibility/debugger/reference/idebugenumfield.md) , представляющий `NestedEnum` перечисление.  
  
## <a name="see-also"></a>См. также:  
 [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
