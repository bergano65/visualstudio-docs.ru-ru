---
title: IApplicationDebuggerUI::BringDocumentToTop | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a8a88b44f609113670259492eb82491b16004d29
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148247"
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