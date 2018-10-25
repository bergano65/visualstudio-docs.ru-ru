---
title: IDebugProgram3::ExecuteOnThread | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3f63b0afffb833fdc59bf39ac5214ccc799e0f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865054"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Выполняет программу отладчика. Поток возвращается для предоставления информации отладчика, в каком потоке пользователь просматривает при выполнении программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Существует три разных способа, что отладчик можно возобновить выполнение после остановки:  
  
- Выполнение: Отмена какой-либо предыдущий шаг и выполняется до следующей точки останова, и т. д.  
  
- Шаг: Отмените все старые шаг и выполняться до завершения этого шага новые.  
  
- По-прежнему: Запустите еще раз и оставить какой-либо шаг старый active.  
  
  Поток, передаваемый `ExecuteOnThread` полезна при принятии решения о этап для отмены. Если вы не знаете потоке, выполнение отменяет все шаги. С помощью базы знаний потока достаточно для отмены шага в активном потоке.  
  
## <a name="see-also"></a>См. также  
 [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

