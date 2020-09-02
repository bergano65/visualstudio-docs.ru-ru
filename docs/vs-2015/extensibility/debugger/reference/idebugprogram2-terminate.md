---
title: 'IDebugProgram2:: Terminate | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4673259e4a8ca0d4354037efbc35b63bedfcbc96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146345"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Завершает программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если возможно, программа будет завершена и выгружена из процесса. в противном случае модуль отладки (DE) выполнит необходимую очистку.  
  
 Этот метод или метод [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) вызывается интегрированной средой разработки, обычно в ответ на то, что пользователь останавливает всю отладку. Реализация этого метода в идеале должна завершать программу внутри процесса. Если это невозможно, параметр DE должен препятствовать запуску программы в этом процессе (и выполнить все необходимые действия по очистке). Если `IDebugProcess2::Terminate` метод вызывался интегрированной средой разработки, весь процесс будет завершен некоторое время после `IDebugProgram2::Terminate` вызова метода.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Завершение](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
