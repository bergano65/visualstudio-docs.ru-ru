---
title: 'IDebugEngine3:: Сетжустмикодестате | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebaf697bfdfff435c12eee1002ff93f4eba7ed65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195863"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод сообщает модулю отладки о сведениях о состоянии Жустмикоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fUpdate`  
 окне Ненулевое значение ( `TRUE` ) для обновления текущей информации, ноль ( `FALSE` ) для сброса всех данных (без учета ранее заданных).  
  
 `dwModules`  
 окне Количество информационных структур в `rgJMCSpec.`  
  
 `rgJMCSpec`  
 окне Массив структур [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) для использования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Жустмикоде — это концепция отладки только кода, относящегося к пользователю, и игнорирования всех промежуточных кодов, таких как системный код, даже если исходный код доступен для этого системного кода.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
