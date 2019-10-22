---
title: 'Иаппликатиондебугжеруи:: Брингдокументконтексттотоп | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577809"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Переводит окно, содержащее данный контекст документа, в начало в пользовательском интерфейсе отладчика и прокручивает окно до контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pddc`  
 окне Контекст документа, который будет переноситься в начало в пользовательском интерфейсе отладчика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Контекст, заданный `pddc`, неизвестен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод переводит окно, содержащее данный контекст документа, в начало в пользовательском интерфейсе отладчика и прокручивает окно до контекста.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)