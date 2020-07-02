---
title: 'IActiveScriptSiteDebug32:: Жетдокументконтекстфромпоситион | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835281"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Используется обработчиком языка для делегирования `IDebugCodeContext::GetSourceContext` .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSourceContext`  
 окне Исходное содержимое, предоставленное для `ParseScriptText` или `AddScriptlet` .  
  
 `uCharacterOffset`  
 окне Смещение символа относительно начала блока скрипта или скриптлет.  
  
 `uNumChars`  
 окне Число символов в этом контексте.  
  
 `ppsc`  
 заполняет Контекст документа, соответствующий этому диапазону символьной позиции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод выполнен успешно.|  
  
## <a name="remarks"></a>Комментарии  
 Обработчики языка используют этот метод для делегирования `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Дополнительно  
 [Интерфейс IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)