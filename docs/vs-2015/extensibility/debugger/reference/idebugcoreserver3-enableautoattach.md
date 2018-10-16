---
title: IDebugCoreServer3::EnableAutoAttach | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbfea47c85d9cacefdfd8d897d9af4a037bde406
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242532"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Включает автоматическое присоединение для указанного отладчики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
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

