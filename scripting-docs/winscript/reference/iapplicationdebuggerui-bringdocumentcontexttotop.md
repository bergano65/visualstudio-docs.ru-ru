---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fab017ab286957cf2c4be35832b1db877b339bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Переводит окно, содержащее контекст данного документа в верхнюю часть пользовательского интерфейса отладчика и Прокручивает окно до контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pddc`  
 [in] Контекст документа для добавления в начало пользовательского интерфейса отладчика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Контекст, указанный с `pddc` не известен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод переводит окно, содержащее контекст данного документа в верхнюю часть пользовательского интерфейса отладчика и Прокручивает окно до контекста.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)