---
title: IDebugDocumentHelper::AddDeferredText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ba6f945e6c7fa4df83a5e301d73b3fc0bb9da92b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096087"
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Этот метод не выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет узлу отложить Указание символов для добавления, пока они потребуются, предоставляя вспомогательное приложение для создания точных уведомления и сведения о размере. `dwTextStartCookie` Параметр является файл cookie, определенные средой размещения, представляющий начальное положение текста. Последующие вызовы `IDebugDocumentText::GetText` необходимо предоставить этот файл cookie. Например в узел, который представляет текст в DBCS, куки-файл может быть смещение в байтах.  
  
 Предполагается, что один вызов `IDebugDocumentText::GetText` можно получить символы из нескольких вызовов `AddDeferredText`. Вспомогательные классы может также потребоваться тот же самый набор отложенные символов более одного раза.  
  
> [!NOTE]
>  Вызовы `AddDeferredText` не должны смешиваться с вызовами `AddUnicodeText` или `AddDBCSText`. В этом случае `E_FAIL` возвращается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)