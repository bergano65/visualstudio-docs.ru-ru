---
title: 'Идебугфунктионобжект:: Креатеаррайобжект | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205808"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает объект Array. Этот массив может содержать как примитивы, так и значения экземпляров объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ot`  
 окне Задает значение из перечисления [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) , указывающее тип нового объекта массива.  
  
 `pClassField`  
 окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий класс объекта, при создании массива значений экземпляра объекта. При создании массива примитивных объектов этот параметр имеет значение null.  
  
 `dwRank`  
 окне Ранг или количество измерений массива.  
  
 `dwDims`  
 окне Размеры каждого измерения массива.  
  
 `dwLowBounds`  
 окне Источник каждого измерения (обычно 0 или 1).  
  
 `ppObject`  
 заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный массив. Фактически это объект [идебугаррайобжект](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Вызовите этот метод, чтобы создать объект, который представляет параметр массива для функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
