---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8ef097ed02ae90b03289e3a2f3a1ad3f0ad8618
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446039"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
> [C++] `pbstrDebugMessage` не может быть `NULL` и должны быть высвобождены с `SysFreeString`.  
  
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
