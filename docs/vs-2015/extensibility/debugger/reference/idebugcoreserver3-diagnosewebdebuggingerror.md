---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24f142a631df25cfbff8ed795736c0cbf4e59eaf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205281"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Чтобы определить, почему auto-attach попыток.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszUrl`  
 [in] Не используется; всегда должны устанавливаться в значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены другие типичные коды возврата.  
  
|Код|Описание|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Не удается определить, почему удаленному серверу не удалось начать отладку.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Не удается выполнить отладку на удаленном сервере, из-за недостаточных разрешений или потому, что команда DEBUG не включена.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Веб-сервер заблокирован и блокирует команду DEBUG, который необходим для включения отладки.|  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
