---
title: 'IDebugBinder3:: Жетексцептионобжектандтипе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6da9b1259518f3796968712b11c725a08aa9a01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843301"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод извлекает исключение, связанное с объектом, если таковой имеется.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppException`  
 заполняет Возвращает объект, представляющий исключение.  
  
 `ppField`  
 заполняет Возвращает объект, представляющий конкретное поле, которое может вызвать исключение (это может быть значение null).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
> [!NOTE]
> Чтобы проверить, существует ли исключение, проверьте значение, возвращаемое `ppException` : если это значение null, то исключение не связано с этим объектом.  
  
## <a name="see-also"></a>См. также:  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
