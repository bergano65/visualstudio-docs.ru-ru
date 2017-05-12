---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
Возвращает диапазон символов, которые были добавитьы с помощью метода `IDebugDocumentHelper::AddDeferredText`, в исходном документе основного приложения.  
  
## Синтаксис  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Параметры  
 `dwTextStartCookie`  
 \[in\] базовая приложение\- указанный файл cookie, представляющее начальную позицию текста.  
  
 `pcharText`  
 \[in, out\] текстовый буфер символов, а.  Этот метод не возвращает символы если этот параметр `NULL`.  
  
 `pstaTextAttr`  
 \[in, out\] буфер атрибута символа, а.  Этот метод не возвращает атрибуты если этот параметр `NULL`.  
  
 `pcNumChars`  
 \[in, out\] показывает фактическое количество возвращаемых символов и атрибутов.  Этот параметр необходимо устанавливать равным нулю до вызова этого метода.  
  
 `cMaxChars`  
 \[in\] максимальное число возвращаемых знаков.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## Заметки  
 Этот метод может возвращать `E_NOTIMPL`, если основное приложение не вызовет `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Этот метод возвращает текст из исходного документа.  Основное приложение не отслеживает правок или других изменений в документе.  
  
## См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Перечисление SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)