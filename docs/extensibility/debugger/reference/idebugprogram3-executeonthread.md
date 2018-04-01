---
title: IDebugProgram3::ExecuteOnThread | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 649b16c1b57b2f66772c2117b776e6b79ad862be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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