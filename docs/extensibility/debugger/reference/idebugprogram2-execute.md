---
title: "IDebugProgram2::Execute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2e53f13aea93de8f39c5802dd2a12598ad938f64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Продолжает выполнение программы в остановленном состоянии. Предыдущее состояние выполнения (например, шаг) снят, и программа начинает выполнение еще раз.  
  
> [!NOTE]
>  Этот метод является устаревшим. Используйте [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) метод вместо него.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда пользователь начинает выполнение из остановленного состояния в потоке некоторые другие программы, этот метод вызывается для данной программы. Этот метод также вызывается, когда пользователь выбирает **запустить** из **отладки** меню в Интегрированной среде разработки. Реализация этого метода может быть достаточно вызвать метод [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) метод для текущего потока в программе.  
  
> [!WARNING]
>  Не отправлять события остановки или немедленно (синхронно) событие [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)