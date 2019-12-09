---
title: 'IDebugDocumentHelper:: Адддеферредтекст | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577042"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Уведомляет вспомогательный объект о доступности заданного текста, но не предоставляет символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cChars`  
 окне Число символов (в Юникоде) для добавления.  
  
 `dwTextStartCookie`  
 окне Определяемый узлом файл cookie, представляющий начальную точку текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Сбой метода.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет узлу отложить предоставление символов для добавления до тех пор, пока они не понадобятся, в то же время позволяя вспомогательному приложению формировать точные уведомления и сведения о размере. Параметр `dwTextStartCookie` — это файл cookie, определяемый узлом, который представляет начальную точку текста. Последующие вызовы `IDebugDocumentText::GetText` должны предоставить этот файл cookie. Например, в узле, представляющем текст в двухбайтовой кодировке (DBCS), файл cookie может быть смещением в байтах.  
  
 Предполагается, что один вызов `IDebugDocumentText::GetText` может получать символы из нескольких вызовов `AddDeferredText`. Вспомогательные классы также могут запрашивать один и тот же диапазон отложенных символов более одного раза.  
  
> [!NOTE]
> Вызовы `AddDeferredText` не должны смешиваться с вызовами `AddUnicodeText` или `AddDBCSText`. Если это происходит, возвращается `E_FAIL`.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: аддуникодетекст](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper:: адддбкстекст](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)