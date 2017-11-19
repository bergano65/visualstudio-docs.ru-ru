---
title: "IDebugDocumentHelper::AddDeferredText | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Уведомляет вспомогательное приложение доступно заданный текст, но он не поддерживает символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cChars`  
 [in] Число символов (Юникод) для добавления.  
  
 `dwTextStartCookie`  
 [in] Определить на уровне узла куки-файл, представляющий начальное положение текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Сбой метода.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет узлу отложить, предоставляя символы, которые требуется добавить, пока они нужны, обеспечив при этом вспомогательное приложение для создания точных уведомления и сведения о размере. `dwTextStartCookie` Параметр имеет файл cookie, определяемый узла, который представляет начальную позицию текста. Последующие вызовы `IDebugDocumentText::GetText` необходимо предоставить этот файл cookie. Например в узле, который представляет текст в кодировке DBCS, куки-файл может быть смещение в байтах.  
  
 Предполагается, что за один вызов `IDebugDocumentText::GetText` можно получить символов из нескольких вызовов `AddDeferredText`. Вспомогательные классы может также потребоваться тот же диапазон символов отложенное более одного раза.  
  
> [!NOTE]
>  Вызовы `AddDeferredText` не должны смешиваться с вызовами `AddUnicodeText` или `AddDBCSText`. В этом случае `E_FAIL` возвращается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)