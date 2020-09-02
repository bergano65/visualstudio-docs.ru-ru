---
title: 'Иенумдебугобжектс:: NOCOUNT | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cec5f45465d8fa9dcd96e557736ad52179ce296a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160937"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает количество элементов в перечислении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcelt`  
 заполняет Возвращает количество элементов в перечислении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод не является частью пользовательского интерфейса перечисления COM, который указывает, что необходимо реализовать только следующие методы: "только следующий", "клонировать", "пропустить" и "Сброс".  
  
## <a name="see-also"></a>См. также:  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
