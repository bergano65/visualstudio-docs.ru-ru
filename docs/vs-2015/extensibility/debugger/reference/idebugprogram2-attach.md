---
title: IDebugProgram2::Attach | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e029c2e16d5eee1764b463b21fc0fd8a4032252
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992012"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Присоединение к программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, используемый для уведомления о событии отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны некоторые возможные коды ошибок.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанная программа уже присоединен к отладчику.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Произошло нарушение безопасности во время процедуры подключения.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Отладчику не удается присоединить классическую программу.|  
  
## <a name="remarks"></a>Примечания  
 Отладчик (DE) никогда не вызывает этот метод, чтобы присоединиться к программе. Если DE выполняется в адресном пространстве программы, [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) вызывается метод. Если выполняется DE в диспетчер отладки сеансов (SDM) адресное пространство, [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
