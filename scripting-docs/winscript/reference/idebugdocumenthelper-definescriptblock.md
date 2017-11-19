---
title: "IDebugDocumentHelper::DefineScriptBlock | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Указывает помощникам определенного диапазона символов блок сценария, выполняемая подсистемой данного скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Расположение на начало блока скрипта.  
  
 `cChars`  
 [in] Число символов в блоке сценария.  
  
 `pas`  
 [in] Обработчик скриптов для этого блока сценария.  
  
 `fScriptlet`  
 [in] Флаг, который указывает, является ли блок сценария пользователи.  
  
 `pdwSourceContext`  
 [out] Контекст источника для блока скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод можно использовать промежуточный узел, если документы содержат внедренные блоки скриптов. Этот метод можно использовать подсистему языка при его код содержит внедренные скрипты для других языков.  
  
 Обработчик сценариев отвечает за все синтаксис Цветовая разметка и код контекст уточняющих запросов в блоке сценария.  
  
 `DefineScriptBlock` Метод следует вызывать после добавления текста (например, с помощью `IDebugDocumentHelper::AddDBCSText` метод), но перед скрипт проанализирован блока (например, с помощью `IActiveScriptParse ::ParseScriptText` метода).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)