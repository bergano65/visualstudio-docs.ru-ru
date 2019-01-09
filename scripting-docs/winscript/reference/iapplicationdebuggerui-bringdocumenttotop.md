---
title: IApplicationDebuggerUI::BringDocumentToTop | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c77c87011c539e02f92aa2aedfdcd7659466d37
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096256"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Открывает окно, содержащее документ указанный отладки отладчик в верхнюю часть пользовательского интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pddt`  
 [in] Отладка документа, чтобы переместить наверх в пользовательском интерфейсе отладчика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Документ не известен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод открывает окно, содержащее документ указанный отладки отладчик в верхнюю часть пользовательского интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)