---
title: 'Идебуженумфиелд:: Жетундерлингсимбол | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1841ca2bf9bd5a43ec5a16a515a03769db64ea15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188971"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий имя перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 заполняет Возвращает [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий имя этого перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Имя перечисления также содержит тип перечисления, привязанный к расположению в памяти с помощью [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="see-also"></a>См. также:  
 [идебуженумфиелд](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [Выполняется](../../../extensibility/debugger/reference/idebugbinder-bind.md)
