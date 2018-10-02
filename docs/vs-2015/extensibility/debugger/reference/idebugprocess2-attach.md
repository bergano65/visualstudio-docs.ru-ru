---
title: IDebugProcess2::Attach | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90ff2520a64ca338cb703c5e22f8a0c021b52540
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562117"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProcess2::Attach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-attach).  
  
Диспетчер отладки сеансов (SDM) присоединяется к процессу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, используемый для уведомления о событии отладки.  
  
 `rgguidSpecificEngines`  
 [in] Массив идентификаторов GUID подсистемы отладки, чтобы использовать для отладки программ, запущенных в процессе. Этот параметр может иметь значение null. Дополнительные сведения см. примечания.  
  
 `celtSpecificEngines`  
 [in] Количество отладки ядра в `rgguidSpecificEngines` массива и размер `rghrEngineAttach` массива.  
  
 `rghrEngineAttach`  
 [in, out] Массив кодов HRESULT, возвращаемых механизмы отладки. Размер массива указан в `celtSpecificEngines` параметра. Каждый код обычно является либо `S_OK` или `S_ATTACH_DEFERRED`. Второй случай показывает, что DE сейчас подключен к нет программ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены другие возможные значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанный процесс уже подключен к отладчику.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Произошло нарушение безопасности во время процедуры подключения.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Отладчику не удается присоединить процесса рабочего стола.|  
  
## <a name="remarks"></a>Примечания  
 Присоединение к процессу присоединяет SDM для всех программ, работающих в этом процессе, можно устранить, если механизмы отладки (DE), указанный в `rgguidSpecificEngines` массива. Задайте `rgguidSpecificEngines` параметр со значением null значение или включить `GUID_NULL` в массиве для присоединения к все программы в процессе.  
  
 Все события отладки, возникающие в процессе отправляются в заданной [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объекта. Это `IDebugEventCallback2` объект предоставляется в том случае, когда SDM вызывает этот метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

