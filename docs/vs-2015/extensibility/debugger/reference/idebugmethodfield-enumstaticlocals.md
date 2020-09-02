---
title: 'Идебугмесодфиелд:: Енумстатиклокалс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69230ce3f748cca460c08d2d40648523161707d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162586"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для статических локальных переменных метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppLocals`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список статических локальных переменных. Возвращает значение null, если статические локальные переменные отсутствуют.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает S_FALSE, если статические локальные переменные отсутствуют. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Каждый элемент является объектом [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющим различные типы статических локальных переменных. Вызовите [метод GetObject](../../../extensibility/debugger/reference/idebugfield-getkind.md) для каждого объекта, чтобы точно определить, какой тип статического локального объекта представляет объект.  
  
## <a name="see-also"></a>См. также:  
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
