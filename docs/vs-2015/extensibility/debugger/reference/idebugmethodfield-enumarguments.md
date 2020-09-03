---
title: 'Идебугмесодфиелд:: Енумаргументс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5744e25f76676e70e25777596fb0d8eb3a580511
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205224"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для типа каждого аргумента, необходимого для вызова метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppParams`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список типов аргументов. Возвращает значение null, если аргументы отсутствуют.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает S_FALSE, если аргументы отсутствуют. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Каждый элемент является объектом [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющим типы каждого параметра. Вызовите метод " [info](../../../extensibility/debugger/reference/idebugfield-getinfo.md) ", чтобы получить сведения о типе каждого параметра.  
  
 Если требуется имя параметра вместе с типом, вызовите метод [енумпараметерс](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .  
  
## <a name="see-also"></a>См. также:  
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
