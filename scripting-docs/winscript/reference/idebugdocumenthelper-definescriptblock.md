---
title: IDebugDocumentHelper::DefineScriptBlock | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a320e4e43a983ace4decbaa68de0b1a7df7d457
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783028"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Указывает для вспомогательного приложения определенного диапазона символов блок скрипта, который обрабатывается обработчиком данного сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ulCharOffset`  
 [in] Расположение начала блока скрипта.  
  
 `cChars`  
 [in] Число символов в блоке сценария.  
  
 `pas`  
 [in] Обработчик скриптов для этого блока сценария.  
  
 `fScriptlet`  
 [in] Флаг, который указывает, является ли блок скрипта пользователи.  
  
 `pdwSourceContext`  
 [out] Исходный контекст для блока скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод можно использовать промежуточный узел, если документы содержат встроенных блоков скриптов. Этот метод можно использовать модуль языка, если ее код содержит внедренные скрипты для других языков.  
  
 Обработчик скриптов отвечает за все синтаксис Цветовая разметка и код контекст уточняющих запросов в блоке сценария.  
  
 `DefineScriptBlock` Метод должен вызываться после добавления текста (например, с помощью `IDebugDocumentHelper::AddDBCSText` метод), но перед сценарием было проанализировано блока (например, с помощью `IActiveScriptParse ::ParseScriptText` метод).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)