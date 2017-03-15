---
title: "IDebugCoreServer3::DiagnoseWebDebuggingError | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 04a8ecbb1bfdc7f14f6b493df7f1dc9e16b53cd6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Чтобы определить, почему auto-attach попыток.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```c#  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszUrl`  
 [in] Не используется; должно всегда быть присвоено значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Ниже перечислены другие типичные коды возврата.  
  
|Код|Описание|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Не удается определить причину сбоя удаленного сервера начать отладку.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Не удается выполнить отладку на удаленном сервере из-за недостаточных разрешений или команда DEBUG не включен.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Веб-сервер заблокирован и блокирует команду DEBUG, необходимую для включения отладки.|  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
