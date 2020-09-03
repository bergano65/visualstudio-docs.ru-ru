---
title: 'Идебугженерикфиелддефинитион:: Конструктинстантиатион | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 57a28cfd3b2ccd2ff37fae80d426817b664972fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180896"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Конструирует экземпляр поля по заданному массиву аргументов типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cArgs`  
 окне Число аргументов в `ppArgs` массиве.  
  
 `ppArgs`  
 окне Массив, содержащий аргументы типа. Аргументы типа должны быть закрытыми типами (не универсальными или полностью созданными универсальными классами).  
  
 `ppConstructedField`  
 заполняет Возвращает интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий новое поле.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Ограничения не проверяются.  
  
## <a name="see-also"></a>См. также:  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
