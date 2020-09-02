---
title: 'Идебугмесодфиелд:: Енумлокалс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2306bbf0c44a883c584346c3dbb3dd70e9b39175
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162602"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для выбранных локальных переменных метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 окне Объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , представляющий адрес отладки, который выбирает контекст или область, из которой должны быть получены локальные переменные.  
  
 `ppLocals`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список локальных переменных. в противном случае возвращает значение null, если нет локальных переменных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет локальных переменных. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Перечисляются только те переменные, которые определены в блоке, содержащем заданный адрес отладки. Если требуются все локальные переменные, включая все созданные компилятором локальные переменные, вызовите метод [енумалллокалс](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .  
  
 Метод может содержать несколько контекстов области или блоков. Например, следующий метод надуманный содержит три области, два внутренних блока и сам текст метода.  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 Объект [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md) представляет `func` сам метод. При вызове `EnumLocals` метода с [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , для которого задан `Inner Scope 1` адрес, возвращается перечисление `temp1` , содержащее переменную, например.  
  
## <a name="see-also"></a>См. также:  
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md)   
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
