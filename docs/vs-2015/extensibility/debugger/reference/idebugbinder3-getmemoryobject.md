---
title: 'IDebugBinder3:: Жетмеморйобжект | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0019b1691cb36b9d23be546cdfdb0e061779647d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193020"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод извлекает объект памяти, представляющий память, к которой привязан этот объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pField`  
 окне Указывает поле, для которого необходимо получить объект памяти.  
  
 `uConstant`  
 окне Представляет адрес или значение памяти для постоянного значения.  
  
 `ppObject`  
 заполняет Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий память, к которой привязан этот объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
