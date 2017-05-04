---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
Указывает вспомогательному приложению, что указанный диапазон символов блок скрипта, отрегулирован заданное обработчиком скрипта.  
  
## Синтаксис  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### Параметры  
 `ulCharOffset`  
 \[in\] начальное расположение блока скрипта.  
  
 `cChars`  
 \[in\] количество символов в блоке скрипта.  
  
 `pas`  
 \[in\] обработчик скриптов для данного блока скрипта.  
  
 `fScriptlet`  
 \[in\] пометьте, указывающее если блок скрипта скрипт.  
  
 `pdwSourceContext`  
 \[out\] контекст источника для блока скрипта.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Промежуточный узел может использовать этот метод, когда его документы, содержащие внедренные блоки скриптов.  Обработчик языка может использовать этот метод, если код содержит внедренные скрипты для остальных языков.  
  
 Обработчик скриптов отвечает за всех уточняющих запросов контекста расцветки и кода синтаксиса в блоке скрипта.  
  
 Метод `DefineScriptBlock` следует вызывать после того, как текст был добавитьо \(например, с помощью метода `IDebugDocumentHelper::AddDBCSText` \), но до того, как будет проанализировать блок скрипта \(например, с помощью метода `IActiveScriptParse ::ParseScriptText` \).  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)