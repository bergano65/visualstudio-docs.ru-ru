---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Документация Майкрософт
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
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: daed5db818bb4e29da1ffd70f5e78509debcde92
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569751"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugSymbolSearchEvent2::GetSymbolSearchInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo).  
  
Вызывается обработчиком событий для получения результатов о процессе загрузки символов.  
  
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
 [out] IDebugModule3 объект, представляющий модуль, для которого были загружены символы.  
  
 `pbstrDebugMessage`  
 [in, out] Возвращает строку, содержащую все сообщения об ошибках из модуля. Если отсутствуют ошибки, эта строка будет просто содержать имя модуля, но никогда не бывает пустым.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` не может быть `NULL` и должны быть высвобождены с `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Сочетание флагов из [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) перечисления, указывающее, были ли загружены символы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда обработчик получает [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) событие после попытки загрузить отладочные символы для модуля, обработчик можно вызвать этот метод, чтобы определить результаты эта нагрузка.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)

