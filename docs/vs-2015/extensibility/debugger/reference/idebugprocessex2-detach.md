---
title: IDebugProcessEx2::D етач | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b79f1f80f9b6849c37fc9b6c4c8669f1397f0227
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538152"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод информирует процесс о том, что сеанс больше не находится в процессе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSession`  
 окне Значение, уникально идентифицирующее сеанс, из которого отсоединяется этот процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Переданный интерфейс `pSession` должен обрабатываться только как файл cookie, значение которого однозначно определяет диспетчер отладки сеанса, изначально подключенный к этому процессу; ни один из методов предоставленного интерфейса не работает.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
