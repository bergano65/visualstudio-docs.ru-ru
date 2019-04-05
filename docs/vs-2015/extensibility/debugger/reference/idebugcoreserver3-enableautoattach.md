---
title: IDebugCoreServer3::EnableAutoAttach | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45362c9456b99d6cec0af01dcb29844d02363a27
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991581"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Включает автоматическое присоединение для указанного отладчики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rgguidSpecificEngines`  
 [in] Массив идентификаторов GUID для каждого ядра отладки, чтобы пометить как автоматическое присоединение.  
  
 `celtSpecificEngines`  
 [in] Число ядер, указанный в `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] Начальный URL-адрес для использования при присоединении автоматически.  
  
 `pbstrSessionID`  
 [out] Идентификатор сеанса, который был подключен автоматически.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Один код ошибки- `E_AUTO_ATTACH_NOT_REGISTERED`, который указывает, что фабрика класса auto-attach не был зарегистрирован.  
  
## <a name="remarks"></a>Примечания  
 При запуске программы, связанный с указанным URL-адрес, указанный отладчики автоматически к работе и подключен.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
