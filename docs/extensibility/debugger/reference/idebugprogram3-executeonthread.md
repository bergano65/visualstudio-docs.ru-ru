---
title: IDebugProgram3::ExecuteOnThread | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8aff643014da16ed9644573a77cb8444836d713d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117066"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Выполняет программу отладчика. Поток возвращается для предоставления информации отладчика, в каком потоке пользователь просматривает при выполнении программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Существует три способа, отладчик может возобновить выполнение после остановки:  
  
-   Выполнение: Отменить все ранее и выполняется до следующей точки останова и т. д.  
  
-   Шаг: Отменить все старые шаг и выполнить до завершения новый шаг.  
  
-   Продолжить: Запустите еще раз, а также оставить какой-либо шаг старого active.  
  
 Поток, передаваемый `ExecuteOnThread` полезно при определении этап для отмены. Если вы не знаете, работающей в потоке выполнения отменяет все шаги. С помощью базы знаний потока достаточно отменить действие для активного потока.  
  
## <a name="see-also"></a>См. также  
 [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)