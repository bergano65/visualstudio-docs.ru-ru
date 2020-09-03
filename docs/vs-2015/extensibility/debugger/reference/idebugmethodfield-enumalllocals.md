---
title: 'Идебугмесодфиелд:: Енумалллокалс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f0f89c3fee45d6d56b845753958d697e41ab11f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190889"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для всех локальных переменных метода, включая созданные внутри компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 окне Объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , представляющий адрес отладки в методе, указывающий на конкретную область или контекст.  
  
 `ppLocals`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список всех локальных переменных в указанной области. в противном случае возвращает значение null, указывающее, что локальные переменные отсутствуют.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет локальных переменных. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Перечисляются только те переменные, которые определены в блоке, содержащем заданный адрес отладки. Этот метод включает все созданные компилятором локальные переменные. Если все, что требуется, — это локальные переменные, явно определенные в источнике, вызовите метод [енумлокалс](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .  
  
 Метод может содержать несколько контекстов области или блоков.  
  
## <a name="see-also"></a>См. также:  
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md)   
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
