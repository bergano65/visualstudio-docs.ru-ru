---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 37a25e762f15a550aa3c4d06c85c64c500065747
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Вызывает обработчик событий для получения результатов о процессе загрузки символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `pModule`  
 [out] Объект IDebugModule3, представляющий модуль, для которого были загружены символы.  
  
 `pbstrDebugMessage`  
 [in, out] Возвращает строку, содержащую все сообщения об ошибках из модуля. Если нет ошибок, эта строка будет содержать только имя модуля, но никогда не бывает пустым.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` не может быть `NULL` и должны быть освобождены вызовом `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Сочетание флагов из [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) перечисления, указывающее, были ли загружены символы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда обработчик получает [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) событие после предпринята попытка загрузить отладочные символы для модуля, обработчик можно вызвать этот метод, чтобы определить результаты нагрузки.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)