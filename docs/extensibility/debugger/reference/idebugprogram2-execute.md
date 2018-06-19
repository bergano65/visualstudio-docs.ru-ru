---
title: IDebugProgram2::Execute | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7f4e26a5c892e1c796a2b6e2f9371898db21f68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115415"
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