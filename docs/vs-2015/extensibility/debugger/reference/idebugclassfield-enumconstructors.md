---
title: 'Идебугклассфиелд:: Енумконструкторс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd93f4867221f0b42f91fe1f96b8a8b464bf5aa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191033"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для конструкторов этого класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cMatch`  
 окне Значение из перечисления [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) , указывающее тип конструкторов для перечисления.  
  
 `ppEnum`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список конструкторов. Возвращает значение null, если нет конструкторов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет конструкторов. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Каждый элемент перечисления — это объект [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md) , описывающий метод-конструктор.  
  
 Список конструкторов обычно не включает конструкторы по умолчанию, предоставляемые компилятором.  
  
## <a name="see-also"></a>См. также:  
 [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
