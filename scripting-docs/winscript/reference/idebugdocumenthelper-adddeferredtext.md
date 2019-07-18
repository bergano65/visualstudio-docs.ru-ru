---
title: IDebugDocumentHelper::AddDeferredText | Документация Майкрософт
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
ms.openlocfilehash: b2f2a7c134142668613cc38cee9357e42cb95096
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433941"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Уведомляет вспомогательный метод, что заданный текст доступен, но он не поддерживает символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cChars`  
 [in] Число символов (Юникод) для добавления.  
  
 `dwTextStartCookie`  
 [in] Определяемые узла файл cookie, представляющий начальное положение текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Этот метод не выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет узлу отложить Указание символов для добавления, пока они потребуются, предоставляя вспомогательное приложение для создания точных уведомления и сведения о размере. `dwTextStartCookie` Параметр является файл cookie, определенные средой размещения, представляющий начальное положение текста. Последующие вызовы `IDebugDocumentText::GetText` необходимо предоставить этот файл cookie. Например в узел, который представляет текст в DBCS, куки-файл может быть смещение в байтах.  
  
 Предполагается, что один вызов `IDebugDocumentText::GetText` можно получить символы из нескольких вызовов `AddDeferredText`. Вспомогательные классы может также потребоваться тот же самый набор отложенные символов более одного раза.  
  
> [!NOTE]
> Вызовы `AddDeferredText` не должны смешиваться с вызовами `AddUnicodeText` или `AddDBCSText`. В этом случае `E_FAIL` возвращается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)